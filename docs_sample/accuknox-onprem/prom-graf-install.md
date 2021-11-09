## Note:
Prometheus Grafana Deployment

Please create a node pool on EKS / GKE / AKS (or) on-premises worker nodes with below Tolerations and Node Selector

```sh
Tolerations:
- key:”monitoring”
  operator: “Equal”
  value: “true”
  effect: “NoSchedule”
Nodeselector:
  monitoring: “true”
```  

### Installing Helm
This guide shows how to install the Helm CLI. Helm can be installed either from source, or from pre-built binary releases.

### From the Binary Releases

Every [release](https://github.com/helm/helm/releases) of Helm provides binary releases for a variety of OSes. These binary versions can be manually downloaded and installed.

Download your [desired version](https://github.com/helm/helm/releases)

Unpack it <b>(tar -zxvf helm-v3.0.0-linux-amd64.tar.gz)</b>

Find the helm binary in the unpacked directory, and move it to its desired destination <b>(mv linux-amd64/helm /usr/local/bin/helm)</b>

<b>Note:</b> Helm automated tests are performed for Linux AMD64 only during CircleCi builds and releases. Testing of other OSes are the responsibility of the community requesting Helm for the OS in question.

<b>For more reference:</b> [Click here..](https://helm.sh/docs/intro/install/)

---

Add accuknox repository to install  Loki helm package:

```sh
helm repo add accuknox-monitoring https://USERNAME:PASSWORD@agents.accuknox.com/repository/accuknox-monitoring
helm repo update
helm search repo accuknox-monitoring 
helm pull accuknox-monitoring/loki-stack/loki-stack  --untar
kubectl create namespace accuknox-loki-logging
kubectl config set-context --current --namespace=accuknox-loki-logging 
helm install loki loki-stack/
```




Add accuknox repository to install Prometheus & Grafana helm package:

```sh
helm repo add accuknox-onprem-monitoring https://USERNAME:PASSWORD@agents.accuknox.com/repository/accuknox-monitoring
helm repo update
helm search repo accuknox-onprem-monitoring 
helm pull accuknox-onprem-monitoring/kube-prometheus-stack  --untar
kubectl create namespace accuknox-monitoring 
kubectl config set-context --current --namespace=accuknox-monitoring 
helm install prometheusmetrics kube-prometheus-stack 
```

Check the Pods deployment:

```sh
kubectl get pods -n accuknox-monitoring
```

Default Username & Password for Grafana:

User: admin 

Password: prom-operator

