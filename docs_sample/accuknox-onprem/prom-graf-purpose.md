Prometheus is an open-source systems monitoring and alerting toolkit.Prometheus collects and stores its metrics as time series data.

Features:

- PromQL, a flexible query language to leverage this dimensionality
- Time series collection happens via a pull model over HTTP
- Pushing time series is supported via an intermediary gateway
- Targets are discovered via service discovery or static configuration
- Multiple modes of graphing and dashboarding support
 
Dependencies:

By default this chart installs additional, dependent charts:

- Kube-state-metrics 
- prometheus-node-exporter
- Grafana