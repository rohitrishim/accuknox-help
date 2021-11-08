### Note:
1. Don't change the namespace name because if you change the namespace - You need to change the service name , If the service name is changed ,then you  
need to change the microservice configmap files . eg: app.yaml.

2. Please create a node pool on EKS / GKE / AKS (or) on-premises worker nodes with below Taints and labels

<b>Taints - mysql:true 

Labels - mysql:true</b>

Add accuknox repository to install  Mysql Percona helm package:
```sh
helm repo add accuknox-prerequisites https://accuknox-user:5U:u8~wu-b@agents.accuknox.com/repository/accuknox-prerequisites
helm repo update
helm search repo accuknox-prerequisites
helm pull accuknox-prerequisites/mysql—untar
```
```sh
cd mysql-percona-chart
kubectl create namespace accuknox-dev-mysql
kubectl config set-context $(kubectl config current-context) --namespace=accuknox-dev-mysql 
cd accuknox-dev-mysql 
kubectl apply -f bundle.yaml
kubectl apply -f cr.yaml
kubectl apply -f secrets.yaml 
kubectl apply -f ssl-secrets.yaml 
kubectl apply -f backup-s3.yaml
```

After following steps the above steps, you will see a similar image as above 
Run a sanitary test with below commands at the mysql namespace

```sh
kubectl run -i --rm --tty percona-client --image=percona:8.0 --restart=Never -- bash -il
mysql -h accuknox-dev-mysql-haproxy -uroot -proot_password
```

Update the passwords in secret.yaml file and run below command

```sh
kubectl apply -f secrets.yaml
```
Optional To configure backup with gcs add the HMAC keys in backup-s3.yaml, change the bucket name in cr.yaml and cron can be changed as required cr.yaml files.

FQDN: For K8’s Service name

#### accuknox-dev-mysql-haproxy.accuknox-dev-mysql.svc.cluster.local