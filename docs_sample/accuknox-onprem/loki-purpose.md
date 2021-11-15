Loki is a log aggregation tool, and it is the core of a fully-featured logging stack. Loki is a datastore optimized for efficiently holding log data.

A Loki-based logging stack consists of 3 components:

- Fluent bit is daemonset its running in each node to get the logs.

- Promtail is the agent, responsible for gathering logs and sending them to Loki.

- Loki is the main server, responsible for storing logs and processing queries.