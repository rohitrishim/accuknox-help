#### Add accuknox repository to install Agents helm package:

```sh
helm repo add accuknox-agents https://accuknox-user:5U:u8~wu-b@agents.accuknox.com/repository/accuknox-agents
helm repo update
helm search repo accuknox-agents
```

<b>Follow the below order to install agents on k8s cluster.</b>


#### Cilium

Installation using Helm

Step 1: 
```sh
helm repo add cilium https://helm.cilium.io/
```
Step 2: 
```sh
helm install cilium cilium/cilium --version 1.10.5 --namespace kube-system
```
FYR: https://docs.cilium.io/en/v1.10/gettingstarted/k8s-install-helm/

## kArmor
kArmor is a CLI client to help manage KubeArmor.
KubeArmor is a container-aware runtime security enforcement system that restricts the behavior (such as process execution, file access, and networking operation) of containers at the system level.

## Installation

```sh
curl -sfL https://raw.githubusercontent.com/kubearmor/kubearmor-client/main/install.sh | sh
```

## To build and install, clone the repository and make install

FYR: https://github.com/kubearmor/kubearmor-client


### Shared-informer-agent

Step 1 : Create namespace has accuknox-dev-shared-informer-agent
             Eg: kubectl create ns accuknox-dev-shared-informer-agent

Step 2 :  Install using helm 

```sh
helm upgrade --install shared-informer-agent-chart-1.0.2.tgz  -n accuknox-dev-shared-informer-agent
```

## S3-audit-reporter

Step 1 : Create namespace has accuknox-dev-s3-audit-reporter
Eg.
```sh
kubectl create ns accuknox-dev-s3-audit-reporter
```
Step 2 :  Install using helm 

Eg.
```sh
helm upgrade --install s3-audit-reporter-charts-1.0.1.tgz   -n  accuknox-dev-s3-audit-reporter
```

## Feeder-Service

Step 1 : Create namespace has feeder-service
Eg.
```sh
kubectl create ns feeder-service
```

Step 2 :  Install using helm 

Eg.

```sh
helm upgrade --install feeder-service-0.1.0.tgz   -n  feeder-service
```

## Knox-Containersec

Step 1 : Create namespace has accuknox-agents

```sh
kubectl create ns accuknox-agents
```

Step 2 :  Install using helm 

Eg.
```sh
helm upgrade --install knox-containersec-chart-0.1.0.tgz  -n  accuknox-agents
```

## Policy Enforcement Agent 

Install using helm 

```sh
helm upgrade --install policy-enforcement-agent-1.0.2.tgz  -n  accuknox-agents
```