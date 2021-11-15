Elastic Cloud on Kubernetes (ECK) extends the basic Kubernetes orchestration capabilities to support the setup and management of Elasticsearch, Kibana, Beats, on Kubernetes.

With Elastic Cloud on Kubernetes we can streamline critical operations, such as:

- Managing and monitoring multiple clusters

- Scaling cluster capacity and storage

- Performing safe configuration changes through rolling upgrades

- Securing clusters with TLS certificates

- Setting up hot-warm-cold architectures with availability zone awareness

Please create a node pool on EKS / GKE / AKS (or) on-premises worker nodes with below Taints and labels

<b>
Taints - logging:true

Labels - logging:true
</b>