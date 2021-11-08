### Note:
Pinot Operator Deployment
1. Don't change the namespace name because if you change the namespace - You need to change the service name , If the service name is changed ,then you need to change the microservice configmap files . eg: app.yaml.

2. Please create a node pool on EKS / GKE / AKS (or) on-premises worker nodes with below Taints and labels

<b>Taints - pinot:true

Labels - pinot:true</b>

Add accuknox repository to install Pinot helm package

```sh
helm repo add accuknox-prerequisites https://accuknox-user:5U:u8~wu-b@agents.accuknox.com/repository/accuknox-prerequisites
helm repo update
helm search repo accuknox-prerequisites
helm pull accuknox-prerequisites/pinot --untar
```
```sh
kubectl create namespace accuknox-dev-pinot
kubectl config set-context –current --namespace=accuknox-dev-pinot
```

```sh
helm install accuknox-dev-pinot accuknox-pinot-dev/
kubectl get all
```