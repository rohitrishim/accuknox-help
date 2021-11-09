Percona Distribution for Mysql Operator is an open-source drop in replacement for MySQL Enterprise with synchronous replication running on Kubernetes. It automates the deployment and management of the members in your Percona XtraDB Cluster environment. It can be used to instantiate a new Percona XtraDB Cluster, or to scale an existing environment. Consult the documentation on the Percona Distribution for Mysql Operator for complete details on capabilities and options.

## Supported Features

- Scale Your Cluster change the size parameter to add or remove members of the cluster. Three is the minimum recommended size for a functioning cluster.

- Automate Your Backups configure cluster backups to run on a scheduled basis. Backups can be stored on a persistent volume or S3-compatible storage. Leverage Point-in-time recovery to reduce RPO/RTO.

- Proxy integration choose HAProxy or ProxySQL as a proxy in front of the Percona XtraDB Cluster. Proxies are deployed and configured automatically with the Operator.

## Common Configurations

- Set Resource Limits - set limitation on requests to CPU and memory resources.

- Customize Storage - set the desired Storage Class and Access Mode for your database cluster data.

- Control Scheduling - define how your PXC Pods are scheduled onto the K8S cluster with tolerations, pod disruption budgets, node selector and affinity settings.

- Automatic synchronization of MySQL users with ProxySQL

- Fully automated minor version updates (Smart Update)

- Update Reader members before Writer member at cluster upgrades

For more reference: [click here..](https://operatorhub.io/operator/percona-xtradb-cluster-operator#:~:text=Percona%20Distribution%20for%20Mysql%20Operator%20is%20an%20open%2Dsource%20drop,your%20Percona%20XtraDB%20Cluster%20environment.)