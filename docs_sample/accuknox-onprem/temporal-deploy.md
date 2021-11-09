### Temporal Operator Deployment

#### 1. Please create a namespace of your choice. Example : temporal-server
```sh
kubectl create ns temporal-server
```

#### 2. Clone the git repository
 - git clone https://github.com/temporalio/helm-charts.git
 - Navigate into the directory that holds helm-charts folder.

#### 3.Helm Install
```sh
helm install temporal -n <namespace> .
```
If Prometheus/ Grafana is not required, please use the below command.

```sh
helm install --set server.replicaCount=1 --set cassandra.config.cluster_size=1 --set prometheus.enabled=false --set grafana.enabled=false --set elasticsearch.enabled=false temporal . --timeout 15m -n <namespace>
kubectl get all -n <namespace>
```

#### 4 .Set the Default Namespace
```sh
kubectl exec -n <namespace> -it  pod/temporaltest-admintools-<pod-id> -- /bin/bash
tctl --ns default n re
```

#### 5 .Successful Installation
- Port-forward the temporal-web (:8088) pod to view the temporal workflows UI.
```sh
kubectl port-forward svc/temporaltest-web 8088:8088 -n <namespace>
```
