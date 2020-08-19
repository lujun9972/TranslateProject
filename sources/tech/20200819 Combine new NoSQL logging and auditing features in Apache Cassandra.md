[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Combine new NoSQL logging and auditing features in Apache Cassandra)
[#]: via: (https://opensource.com/article/20/8/nosql-cassandra)
[#]: author: (Ben Bromhead https://opensource.com/users/ben-bromhead)

Combine new NoSQL logging and auditing features in Apache Cassandra
======
New auditing features in Cassandra help organizations monitor user
activity to comply with regulatory and security requirements.
![Metrics and a graph illustration][1]

Apache [Cassandra][2]'s upcoming [4.0 release][3] includes new features to help organizations monitor user activity in the database. These features provide a robust set of enterprise-class [audit capabilities][4] that can help companies meet their Sarbanes-Oxley (SOX), Payment Card Industry (PCI), and other regulatory and security requirements.

Cassandra's auditing features enable operators to audit log entries—every [DML, DDL, and DCL change][5]—and log and save the entries to a binary file or a user-configurable source. Auditing can be configured on specific keyspaces, users, or command categories. By default, these are saved to a local disk in BinLog format and can be viewed with Cassandra's [fqltool][6] and the [auditlogviewer][7] tool.

### Logging

Cassandra's new, flexible audit facility enables a range of capabilities, from auditing specific actions to logging a cluster's complete activity and tracking diagnostic events across the cluster. Three core features have been added in Cassandra 4.0:

  * **Audit logging with BinAuditLogger (BAL):** Designed with audit, security, and compliance use cases in mind
  * [**Full Query Logging**][8] **(FQL):** Focuses on testing, benchmarking, and production workload investigations
  * **Diagnostic events:** Provides a Cassandra Query Language (CQL)-native method for subscribing to events generated within the common logging framework used by the BAL and FQL capabilities



#### Audit logging (BAL)

Internally, BAL and FQL are managed by Apache Cassandra's AuditLogManager. Both implement a common extension point called IAuditLogger and are built into Apache Cassandra. FQL and BAL both leverage the same BinLog format, sharing a common implementation.

Audit logging on its own is a full "firehose" of events and actions performed within the database. The administrator can choose to include or exclude specific categories, users, and keyspaces in the generated audit trail.

By default, the format and output are text-based and human-readable.

#### Full Query Logging (FQL)

FQL is similar to audit logging but is designed to capture a representative and repeatable sample of a cluster's workload filtered by some criteria to ensure the output is manageable.

Both can be enabled via nodetool and configured as part of Cassandra.yaml, with the option to ensure an audit event is generated and persisted before an action is returned as successful to the end client.

FQL is designed to be used with the fqltool, which enables viewing, replaying, and manipulating the stream of captured queries.

#### Diagnostic events

Diagnostic events permit clients to subscribe to cluster events and to the same common extension point as BAL and FQL, if users want to consume audit records this way. Diagnostic events push events to clients, and you can subscribe to audit events via this system.

You can configure as many of these three types as you need for your requirements.

### How audit logging differs from CDC

Cassandra's [Change Data Capture][9] (CDC) mechanism has been supported on tables for some time now; however, the implementation has always been nuanced and complex, making it more difficult to use. In essence, CDC provides an index into local node-commit logs containing data for tables with CDC enabled. CDC just captures instantaneous data that is written to disk, leaving consumers with the difficult task of ingesting these commit logs, interpreting the format, and merging the data across the cluster.

On the other hand, Cassandra's audit logging capability can log reads, writes, login attempts, and schema changes and can provide the CQL that produced the event. Effectively, either of these features could be leveraged to build a proper CDC stream. Given the more granular control and dedicated tooling for reading logs, using the IAuditLogger interface is easier than consuming the CDC files.

### What to expect

It is easy to turn on audit logging in your cassandra.yaml file. Performance-wise, there is no impact until the feature is enabled; once enabled, you might see a modest 10 to 15% decrease on (mixed) workload throughput and P99 latency. However, there are a number of performance improvements elsewhere in Apache Cassandra 4.0—particularly from the new internode communications module—that are expected to offset some of this.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/nosql-cassandra

作者：[Ben Bromhead][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/ben-bromhead
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/metrics_graph_stats_blue.png?itok=OKCc_60D (Metrics and a graph illustration)
[2]: https://cassandra.apache.org/
[3]: https://cassandra.apache.org/blog/2020/07/20/apache-cassandra-4-0-beta1.html
[4]: https://issues.apache.org/jira/browse/CASSANDRA-12151
[5]: https://cassandra.apache.org/doc/latest/new/auditlogging.html
[6]: https://cassandra.apache.org/doc/latest/new/fqllogging.html#viewing-the-full-query-logs
[7]: https://cassandra.apache.org/doc/latest/new/auditlogging.html#viewing-the-audit-logs
[8]: https://cassandra.apache.org/doc/latest/new/fqllogging.html
[9]: https://cassandra.apache.org/doc/latest/operating/cdc.html
