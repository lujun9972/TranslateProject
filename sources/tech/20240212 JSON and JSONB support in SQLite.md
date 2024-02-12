[#]: subject: "JSON and JSONB support in SQLite"
[#]: via: "https://fedoramagazine.org/json-and-jsonb-support-in-sqlite-3-45-0/"
[#]: author: "zmiklank https://fedoramagazine.org/author/zmiklank/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

JSON and JSONB support in SQLite
======

![][1]

Photo by [Pawel Czerwinski][2] on [Unsplash][3]

This article provides insight on SQLite’s support for [JSON][4] (JavaScript Object Notation) and the latest addition, JSONB. It explains how SQLite facilitates handling JSON and JSONB data and what the differences are between JSON and JSONB. Additionally, the article provides practical “hello world” examples.

### What is JSON

JSON is a format for structuring data in an easily readable way, both for computers and for humans. JSON can code four primitive types of data: strings, numbers, booleans and null. It can also include non-primitive types, namely objects and arrays.

In addition there is the [JSON5][5] format – offering extended syntax to cover more use cases for JSON, like using single quotes, no quotes, or trailing commas.

### JSON support in SQLite

At first SQLite provided functions for JSON handling as an opt-in extension, controlled by the _“-DSQLITE_ENABLE_JSON1”_ compile-time option. Since SQLite version 3.38.0, JSON1 support is built-in and can be omitted during compile time by adding the _“-DSQLITE_OMIT_JSON”_ option. SQLite supports the JSON5 standard since the 3.42.0 version. While SQLite can process JSON5 structures, its functions will consistently return JSON in its JSON1 form.

SQLite, unlike other database engines, is [flexibly typed][6], which is important for handling JSONs. When creating a table, you have the option to omit specifying the data type of each column entirely. SQLite operates with so called “[storage classes][7]”, where input is always classified into one of five categories [NULL, INTEGER, REAL, TEXT, BLOB]. These classes are internally divided into more granular types, aligning more naturally with the C language. However, this granularity remains hidden from users’ view. JSON naturally falls under the TEXT class. The following examples outline how you can store the JSON structure and query it in various ways within the SQLite database:

### Practical examples of JSON handling in SQLite

This section will use the following JSON for demonstrative purposes:

```

    $ JSON1='{
      "country": "Luxembourg",
      "capital": "Luxembourg City",
      "languages": [ "French", "German", "Luxembourgish" ]
    }'
    $ JSON2='{
      "country": "Netherlands",
      "capital": "Amsterdam",
      "languages": [ "Dutch" ]
    }'

```

#### Parsing JSON before it enters a database

JSON can be parsed programmatically or by existing CLI tools, such as [sqlite-utils,][8] before being inserted into the database. In this process, the tool parses the JSON, organizing it into different columns within a table. The external tool processes the JSON to SQL commands directly inserting JSON fields into the table:

```

    $ echo $JSON1 | sqlite-utils insert states.db states -
    $ echo $JSON2 | sqlite-utils insert states.db states -
    sqlite> .open states.db
    sqlite> SELECT * FROM states;
    Luxembourg|Luxembourg City|["French", "German", "Luxembourgish"]
    Netherlands|Amsterdam|["Dutch"]

```

#### Storing whole JSON into one column

Users can store JSON as it is or use the _json()_ function, converting the JSON into its minified version before storing it. The _json()_ function also throws an error if the JSON is invalid. However, it is advised to use the _json_valid()_ or _json_error_position()_ function for explicit validity tests before hand. The following example shows both cases:

```

    sqlite> CREATE TABLE states(data TEXT);
    sqlite> SELECT json_valid('{"country":"Luxembourg","capital":"Luxembourg City","languages":["French","German","Luxembourgish"]}');
    1
    sqlite> INSERT INTO states VALUES ('{"country":"Luxembourg","capital":"Luxembourg City","languages":["French","German","Luxembourgish"]}');
    sqlite> INSERT INTO states VALUES (json('{"country":"Netherlands","capital":"Amsterdam","languages":["Dutch"]}'));
    sqlite> SELECT * FROM states;
    {"country":"Luxembourg","capital":"Luxembourg City","languages":["French","German","Luxembourgish"]}
    {"country":"Netherlands","capital":"Amsterdam","languages":["Dutch"]}

```

#### Query JSON field as standard text

JSON stored in the TEXT data class means it can be selected without any added overhead like any other TEXT field. It is up to the application that uses this approach to correctly parse the data from the obtained JSON structure.

```

    sqlite> SELECT data FROM states;
    {"country":"Luxembourg","capital":"Luxembourg City","languages":["French","German","Luxembourgish"]}
    {"country":"Netherlands","capital":"Amsterdam","languages":["Dutch"]}

```

#### Using JSON built-in functions

Built-in JSON functionality provides a couple of [handy functions][9] for querying specific elements of the stored JSON. _json_extract()_ returns one or more values from the provided JSON. Similar are the “ _- >”_ and “ _- >>”_ operators. There are semantic differences between _json_extract()_ , “ _- >_” and “ _- >>”_. The _json_extract()_ function returns a JSON structure if the queried data is a JSON object or array and returns SQL format otherwise. The operator “ _- >_” always returns the JSON representation, and “ _- >>_” returns the SQL representation of the queried structure.

Using JSON functions for handling the JSON data leaves the parsing part of the job for the database, and the user application no longer needs to expend any effort on it. When accessing JSON elements, SQLite must parse JSON stored as a string each time.

Querying specific column and row can look like this:

```

    sqlite> SELECT data->>'country' FROM states WHERE data->>'capital'=='Amsterdam';
    Netherlands
    sqlite> SELECT data->'country' FROM states WHERE data->>'capital'=='Amsterdam';
    "Netherlands"
    sqlite> SELECT json_extract(data,'$.country') FROM states WHERE json_extract(data, '$.capital')=='Amsterdam';
    Netherlands
    sqlite> SELECT json_extract(data, '$.languages') FROM states;
    ["French","German","Luxembourgish"]
    ["Dutch"]

```

#### Other JSON functions in SQLite

Help with creating JSON structures is available with functions like _json_array()_ , and _json_object()_. Functions for adjusting existing JSON structure are _json_insert()_ , _json_replace()_ and _json_set()_ . A helpful function for debugging is _json_type()_ , which returns the type of the JSON element. SQLite documentation provides more detailed information about these and [many more JSON functions][9].

### JSONB in SQLite

A big new feature is introduced in the SQLite 3.45.0 release – [the SQLite JSONB][10]. The aim of this feature is to speed up the JSON manipulation, since storing JSON as BLOB will save time normally spent on parsing the standard JSON saved as string. The JSONB object consists of a header and a body. The header of each element stores its properties, like size or type. Knowing the size of the JSON element speeds up its parsing; eliminating the need of searching for the next delimiter. SQLite offers various functions for JSONB handling. Many standard JSON functions have their JSONB equivalent, like the _jsonb()_ function, which returns a JSONB object, or _jsonb_extract()_ , extracting values from a JSONB blob. Many [standard JSON functions][9] can also take JSONB blob as a parameter.

### Practical examples of JSONB handling in SQLite

#### Inserting a JSONB blob

When storing the JSON as a blob the jsonb() function can be used. This function takes valid JSON as a parameter and returns JSONB binary data. It can also take valid JSONB as parameter, in this situation it simply returns it back.

```

    sqlite> CREATE TABLE states(data BLOB);
    sqlite> INSERT INTO states VALUES(jsonb('{"country":"Luxembourg","capital":"Luxembourg City","languages":["French","German","Luxembourgish"]}'));
    sqlite> INSERT INTO states VALUES(jsonb('{"country":"Netherlands","capital":"Amsterdam","languages":["Dutch"]}'));

```

#### Retrieving JSONB blob

If we choose the standard way for retrieving JSONB, its binary representation is returned.

```

    sqlite> SELECT data FROM states;
    �wcountryLuxembourgwcapital�Luxembourg Citylanguages�gFrenchgGerman�Luxembourgish
    �wcountryNetherlandswcapitalAmsterdamlanguageskWDutch

```

It can be more useful to retrieve the text form of stored JSONB. For this the _json()_ and _json_extract()_ functions can be used.

```

    sqlite> SELECT json(data) FROM states;
    {"country":"Luxembourg","capital":"Luxembourg City","languages":["French","German","Luxembourgish"]}
    {"country":"Netherlands","capital":"Amsterdam","languages":["Dutch"]}
    sqlite> SELECT json_extract(data, '$.languages') FROM states;
    ["French","German","Luxembourgish"]
    ["Dutch"]

```

On the other hand, _jsonb_extract()_ returns JSONB binary if a JSON object or array is retrieved and returns values otherwise.

```

    sqlite> SELECT jsonb_extract(data, '$.languages') FROM states;
    �gFrenchgGerman�Luxembourgish
    kWDutch
    sqlite> SELECT jsonb_extract(data, '$.capital') FROM states;
    Luxembourg City
    Amsterdam

```

### In conclusion

This article presented the handling of JSON in the SQLite database, demonstrating various approaches for storing and retrieving JSON data. Additionally, it briefly outlined SQLite’s new feature, SQLite JSONB, with illustrative examples.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/json-and-jsonb-support-in-sqlite-3-45-0/

作者：[zmiklank][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/zmiklank/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/02/json-jsonb_support_in_sqlite-816x345.jpg
[2]: https://unsplash.com/@pawel_czerwinski?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/a-black-and-white-photo-of-a-cross-in-the-middle-of-a-picture-WEizaiwLk1k?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://www.rfc-editor.org/rfc/rfc4627
[5]: https://json5.org/
[6]: https://sqlite.org/quirks.html
[7]: https://sqlite.org/datatype3.html
[8]: https://sqlite-utils.datasette.io/en/stable/installation.html
[9]: https://www.sqlite.org/json1.html
[10]: https://sqlite.org/draft/jsonb.html
