[#]: subject: "Watch Out Elasticsearch! Tiger Data's PostgreSQL BM25 Search Extension Goes Open Source"
[#]: via: "https://itsfoss.com/news/tiger-data-pg-textsearch/"
[#]: author: "Sourav Rudra https://itsfoss.com/author/sourav/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Watch Out Elasticsearch! Tiger Data's PostgreSQL BM25 Search Extension Goes Open Source
======

[![Warp Terminal][1]][2]

[Tiger Data][3] is the company behind [TimescaleDB][4], a popular time-series database extension for PostgreSQL. The company builds tools that enhance PostgreSQL for time-series data, real-time analytics, and AI applications.

They have now open-sourced pg_textsearch, their [PostgreSQL][5] extension that brings modern search capabilities to the database. Let's check it out! 😃

### pg_textsearch Goes Open

Tiger Data has released pg_textsearch under [The PostgreSQL License][6] on [GitHub][7]. The extension **was previously available only on Tiger Cloud** , their managed database platform.

Announcing this move, [Michael Freedman][8], the CTO of Tiger Data, stated that:

> If you care about fast, relevance-ranked keyword search without leaving Postgres – or hybrid retrieval by combining pg_textsearch with pgvector/pgvectorscale – this is for you.

The extension **lets developers run BM25 relevance-ranked keyword searches directly in PostgreSQL** without them needing to set up an external search system like [Elasticsearch][9].

BM25 is the industry-standard ranking algorithm behind modern search engines. With pg_textsearch, you can now run it inside Postgres for relevance-ranked text search. pg_textsearch pairs naturally with pgvector to support keyword + semantic search in a single database.

Some additional details can be [found in this blog post][10].

![][11]

Some **key features** of [pg_textsearch][12] include:

  * Support for 29+ languages.
  * Works with partitioned tables.
  * Simple SQL syntax with the `<@>` operator.
  * Memtable architecture for efficient indexing.
  * [BM25][13] ranking with configurable ranking parameters (k1, b).



Tiger Data positions this as the first step toward their **Postgres Search Stack** , aimed at Postgres developers, infrastructure engineers, and AI app builders. The stack will combine keyword search via `pg_textsearch` with vector search through `pgvector` and `pgvectorscale`, giving teams a complete search solution inside PostgreSQL.

[pg_textsearch on GitHub][7]

**Suggested Read 📖:** [Is SysAdmin Still a Good Career Choice in 2026?][14]

![][15]

--------------------------------------------------------------------------------

via: https://itsfoss.com/news/tiger-data-pg-textsearch/

作者：[Sourav Rudra][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://itsfoss.com/author/sourav/
[b]: https://github.com/lujun9972
[1]: https://itsfoss.com/assets/images/warp.webp
[2]: https://www.warp.dev?utm_source=its_foss&utm_medium=display&utm_campaign=linux_launch
[3]: https://www.tigerdata.com/
[4]: https://github.com/timescale/timescaledb
[5]: https://www.postgresql.org/
[6]: https://opensource.org/license/postgresql
[7]: https://tsdb.co/itsfoss_pg_textsearch
[8]: https://www.linkedin.com/posts/mfreed_postgres-activity-7406358783196758016-itPq/
[9]: https://www.elastic.co/elasticsearch
[10]: https://www.tigerdata.com/blog/introducing-pg_textsearch-true-bm25-ranking-hybrid-retrieval-postgres
[11]: https://itsfoss.com/content/images/icon/icon.ico
[12]: https://www.tigerdata.com/docs/use-timescale/latest/extensions/pg-textsearch
[13]: https://en.wikipedia.org/wiki/Okapi_BM25
[14]: https://itsfoss.com/news/is-sysadmin-good-career-choice/
[15]: https://itsfoss.com/content/images/icon/android-chrome-512x512-119.png
