## Note:
Kafka Operator Deployment
1. Don't change the namespace name because if you change the namespace - You need to change the service name , If the service name is changed ,then you need to change the microservice configmap files . eg: app.yaml.

2. Please create a node pool on EKS / GKE / AKS (or) on-premises worker nodes with below Taints and labels

<b>Taints - kafka:true 

Labels - kafka:true</b>

Add accuknox repository to install strimzi-kafka-operator helm package:

```sh
helm repo add accuknox-prerequisites https://accuknox-user:5U:u8~wu-b@agents.accuknox.com/repository/accuknox-prerequisites
helm repo update
helm search repo accuknox-prerequisites
helm pull accuknox-prerequisites/strimzi-kafka-operator --untar
```
```sh
kubectl create namespace accuknox-dev-kafka
kubectl config set-context --current --namespace=accuknox-dev-kafka
```
```sh
helm install dev-kafka  strimzi-kafka-operator
```

Check the Pods deployment
```sh
kubectl get pods -n accuknox-dev-kafka
```

Extract the connectivity information.

## Get bootstrap server endpoint
```sh
kubectl get kafka dev-kafka -o jsonpath='{.status.listeners[?(@.type=="external")].bootstrapServers}' -n accuknox-dev-kafka
```
## Get CA
```sh
kubectl get secret dev-kafka-cluster-ca-cert -o jsonpath='{.data.ca\.p12}' -n accuknox-dev-kafka | base64 -d > ca.p12
```
## Get CA Password
```sh
kubectl get secret dev-kafka-cluster-ca-cert -o jsonpath='{.data.ca\.password}' -n accuknox-dev-kafka | base64 -d > ca.password
```
## Get User Cert
```sh
kubectl get secret/node-event-feeder-common -n accuknox-dev-kafka -o jsonpath='{.data.user\.p12}' | base64 -d > user.p12
```
## Get user password
```sh
kubectl get secret/node-event-feeder-common -n accuknox-dev-kafka -o jsonpath='{.data.user\.password}' | base64 -d > user.password
```
## Convert user.p12 into base64
```sh
cat user.p12 | base64 > user.p12.base64
```
## Convert ca.p12 into base64
```sh
cat ca.p12 | base64 > ca.p12.base64
```
## Convert ca.password into base64
```sh
cat ca.password | base64 > ca.password.base64
```
## Convert user.password into base64
```sh
cat user.password | base64 > user.password.base64
```
## Convert p12 to pem
```sh
openssl pkcs12 -in ca.p12 -out ca.pem
```
## Convert ca.pem to base64
```sh
cat ca.pem | base64 > ca.pem.base64
```
Note: ca.p12, ca.password, user.p12 and user.password are required to be used in Java based applications. For Go based applications, use ca.pem, user.p12 and user.password. For use in Kubernetes, use the base64 versions of respective files.

FQDN (K8’s Service name) Value for Internal Cluster application connectivity.

FQDN : dev-kafka-kafka-bootstrap.accuknox-dev-kafka.svc.cluster.local:9092