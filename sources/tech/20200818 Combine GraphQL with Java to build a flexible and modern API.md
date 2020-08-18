[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Combine GraphQL with Java to build a flexible and modern API)
[#]: via: (https://opensource.com/article/20/8/graphql-quarkus)
[#]: author: (Daniel Oh https://opensource.com/users/daniel-oh)

Combine GraphQL with Java to build a flexible and modern API
======
Avoid under-fetching and over-fetching data when retrieving data using
REST APIs.
![Person drinking a hot drink at the computer][1]

In the past few years, developers have used RESTful web services over HTTP(s) to expose business functions using an API. The [REST API][2] uses server-driven fixed data responses, which means a developer (client) can't determine the result of a response. Instead, the server sends all the data back to the client, which is called _over-fetching_. The developer (client) needs to invoke multiple REST APIs after the first call until the client gets the required data, which results in _under-fetching_.

To create new microservices, developers using these REST APIs have been looking for ways to minimize over-fetching and under-fetching when retrieving data along with business logic.

[GraphQL][3] provides a client-driven query language and runtime to prevent this overhead on the client side and instead retrieve the exact data that the REST API requires. When GraphQL came out, many developers thought that it could replace existing REST API specifications. However, it's not a replacement but an alternative.

This article explains how to consume GraphQL services using [Quarkus][4] applications. Quarkus is a Kubernetes-based framework for writing Java applications. If you haven't created a Quarkus application before, please read [_Writing Java with Quarkus in VS Code_][5] before continuing.

### Add GraphQL extensions to your Quarkus project

Start by adding a Quarkus extension, [`smallrye-graphql`][6], to an existing Quarkus Maven project by entering the following in a terminal (or you can use a [Quarkus tool in Visual Studio Code][7]):


```
`$ mvn quarkus:add-extension -Dextensions="graphql"`
```

You should see the following in the terminal:


```
✅ Extension io.quarkus:quarkus-smallrye-graphql has been installed
[INFO] ---------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ---------------------------------------------------------------------
[INFO] Total time:  9.833 s
[INFO] Finished at: 2020-07-29T22:00:28-04:00
[INFO] ---------------------------------------------------------------------
```

### Add an entity and a service for GraphQL's API

Create two entity Java classes—for this example, which queries data on movies. call them `Film` and `Hero`—to represent GraphQL schemas that are a set of possible data (e.g., objects, fields, relationships) that an end user can retrieve:


```
public class Film {
    private [String][8] title;
    private [Integer][9] episodeID;
    private [String][8] director;
    private LocalDate releaseDate;

   // Getter &amp; Setter methods here
   ...
}

public class Hero {

    private [String][8] name;
    private [String][8] surname;
    private [Double][10] height;
    private [Integer][9] mass;
    private [Boolean][11] darkSide;
    private LightSaber lightSaber;
    private List&lt;Integer&gt; episodeIds = new ArrayList&lt;&gt;();

   // Getter &amp; Setter methods here
   ...
}

enum LightSaber {
    RED, BLUE, GREEN
}
```

### Create a GraphQL API with CDI bean

Implement a few methods to retrieve the `Film` and `Hero` data with parameters in the CDI (Contexts and Dependency Injection) bean class (e.g., `GalaxyService.java`). Generate some example data:


```
public GalaxyService() {

   Film aNewHope = new Film();
   aNewHope.setTitle("A New Hope");
   aNewHope.setReleaseDate(LocalDate.of(1977, Month.MAY, 25));
   aNewHope.setEpisodeID(4);
   aNewHope.setDirector("George Lucas");
   films.add(aNewHope);
   ...

   Hero luke = new Hero();
   luke.setName("Luke");
   luke.setSurname("Skywalker");
   luke.setHeight(1.7);
   luke.setMass(73);
   luke.setLightSaber(LightSaber.GREEN);
   luke.setDarkSide(false);
   luke.getEpisodeIds().addAll([Arrays][12].asList(4, 5, 6));
   heroes.add(luke);
   ...

public List&lt;Film&gt; getAllFilms() {
   return films;
}
```

Now, create a GraphQL API class (e.g., `FilmResource.java`) to inject the CDI bean:


```
@GraphQLApi
public class FilmResource {

    @Inject
    GalaxyService service;

    @Query("allFilms")
    @Description("Get all Films from a galaxy far far away")
    public List&lt;Film&gt; getAllFilms() {
        return service.getAllFilms();
    }
}
```

The `@GraphQLApi` annotation enables you to use the CDI bean (e.g., `GalaxyService`) for a GraphQL endpoint. `@Query` annotation allows you to make the method (e.g., `getAllFilms`) queryable with a specific name (e.g., `allFilms`).

### Access GraphiQL's UI, a GraphQL interface

The Quarkus `smallrye-graphql` extension enables you to use a [GraphiQL][13] tool for easy interaction with your GraphQL APIs when you run your Quarkus application. Access the GraphiQL user interface (UI) with the following endpoint after you start your application using Quarkus' dev mode (`mvn quarkus:dev`):


```
 --/ __ \/ / / / _ | / _ \/ //_/ / / / __/
 -/ /_/ / /_/ / __ |/ , _/ ,&lt; / /_/ /\ \  
\--\\___\\_\\____/_/ |_/_/|_/_/|_|\\____/___/  
2020-07-29 22:25:18,324 WARN  [io.sma.graphql] (Quarkus Main Thread) SRGQL010000: Schema is null, or it has no operations. Not bootstrapping SmallRye GraphQL
2020-07-29 22:25:18,552 INFO  [io.quarkus] (Quarkus Main Thread) quarkus-getting-started 1.0.0-SNAPSHOT on JVM (powered by Quarkus x.xx.x.) started in 1.246s. Listening on: <http://0.0.0.0:8080>
2020-07-29 22:25:18,553 INFO  [io.quarkus] (Quarkus Main Thread) Profile dev activated. Live Coding activated.
2020-07-29 22:25:18,553 INFO  [io.quarkus] (Quarkus Main Thread) Installed features: [cdi, resteasy, smallrye-graphql]
```

Once the Quarkus runtime starts, access GraphiQL's UI locally using `http://localhost:8080/graphql-ui/`.

You will see:

![GraphiQL welcome screen][14]

(Daniel Oh, [CC BY-SA 4.0][15])

### Query the GraphQL API

Try querying GraphiQL using:


```
query allFilms {
  allFilms {
    title
    director
    releaseDate
    episodeID
  }
}
```

Click the **Play** button, and you will see:

![GraphiQL query][16]

(Daniel Oh, [CC BY-SA 4.0][15])

Imagine a new client application requires `title` and `episodeID` data but doesn't need to invoke the previous API (i.e., over-fetching), which includes unnecessary data (e.g., `Director`, `releaseDate`). Try to query GraphiQL again with:


```
query allFilms {
  allFilms {
    title
    episodeID
  }
}
```

You will see:

![GraphiQL query][17]

(Daniel Oh, [CC BY-SA 4.0][15])

### Next steps

GraphQL is only continuing to grow in popularity, and it integrates nicely with Java. If you're looking for more ways to learn, try changing the query data to meet your business requirements over GraphQL APIs. And remember, the complete Java code for this how-to is available in the [GitHub repo][18].

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/graphql-quarkus

作者：[Daniel Oh][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/daniel-oh
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/coffee_tea_laptop_computer_work_desk.png?itok=D5yMx_Dr (Person drinking a hot drink at the computer)
[2]: https://www.redhat.com/en/topics/api/what-is-a-rest-api
[3]: https://opensource.com/article/19/6/what-is-graphql
[4]: https://quarkus.io/
[5]: https://opensource.com/article/20/4/java-quarkus-vs-code
[6]: https://github.com/smallrye/smallrye-graphql
[7]: https://marketplace.visualstudio.com/items?itemName=redhat.vscode-quarkus
[8]: http://www.google.com/search?hl=en&q=allinurl%3Adocs.oracle.com+javase+docs+api+string
[9]: http://www.google.com/search?hl=en&q=allinurl%3Adocs.oracle.com+javase+docs+api+integer
[10]: http://www.google.com/search?hl=en&q=allinurl%3Adocs.oracle.com+javase+docs+api+double
[11]: http://www.google.com/search?hl=en&q=allinurl%3Adocs.oracle.com+javase+docs+api+boolean
[12]: http://www.google.com/search?hl=en&q=allinurl%3Adocs.oracle.com+javase+docs+api+arrays
[13]: https://github.com/graphql/graphiql
[14]: https://opensource.com/sites/default/files/uploads/welcometographiql.png (GraphiQL welcome screen)
[15]: https://creativecommons.org/licenses/by-sa/4.0/
[16]: https://opensource.com/sites/default/files/uploads/graphiqlquery.png (GraphiQL query)
[17]: https://opensource.com/sites/default/files/uploads/graphiqlquery2.png (GraphiQL query)
[18]: https://github.com/quarkusio/quarkus-quickstarts/tree/master/microprofile-graphql-quickstart
