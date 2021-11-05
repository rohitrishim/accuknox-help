# Cilium: Deployment Guide

## Deployment Steps for Cilium & Hubble CLI
### 1. Download and install Cilium CLI
```sh
curl -L --remote-name-all https://github.com/cilium/cilium-cli/releases/latest/download/cilium-linux-amd64.tar.gz{,.sha256sum}
sha256sum --check cilium-linux-amd64.tar.gz.sha256sum
sudo tar xzvfC cilium-linux-amd64.tar.gz /usr/local/bin
rm cilium-linux-amd64.tar.gz{,.sha256sum}
```

### 2. Install Cilium
```sh
cilium install
```
It is assumed that the k8s cluster is already present/reachable and the user has rights to create service-accounts and cluster-role-bindings.

### 3. Validate the Installation

#### a. [Optional] To validate that Cilium has been properly installed, you can run:
```sh
cilium status --wait
```
#### b. [Optional] Run the following command to validate that your cluster has proper network connectivity:
```sh
cilium connectivity test
```
Congratulations! You have a fully functional Kubernetes cluster with Cilium. 🎉

### 4. Setting up Hubble Observability
#### a. Enable Hubble in Cilium
```sh
cilium hubble enable
```
#### b. Install the Hubble CLI Client
```sh
export HUBBLE_VERSION=$(curl -s https://raw.githubusercontent.com/cilium/hubble/master/stable.txt)
curl -L --remote-name-all https://github.com/cilium/hubble/releases/download/$HUBBLE_VERSION/hubble-linux-amd64.tar.gz{,.sha256sum}
sha256sum --check hubble-linux-amd64.tar.gz.sha256sum
sudo tar xzvfC hubble-linux-amd64.tar.gz /usr/local/bin
rm hubble-linux-amd64.tar.gz{,.sha256sum}
```

### 5. Getting Alerts/Telemetry from Cilium
#### a. Enable port-forwarding for Cilium Hubble relay
```sh
cilium hubble port-forward&
```
#### b. Observing logs using hubble cli
```sh
hubble observe
```
<!---
## K8s platforms tested
1. Google Kubernetes Engine (GKE) Container Optimized OS (COS)
2. GKE Ubuntu image
3. [Amazon Elastic Kubernetes Service (EKS)](https://github.com/kubearmor/KubeArmor/tree/master/deployments/EKS)
4. Self-managed (on-prem) k8s
5. Local k8s engines (microk8s, k3s, minikube)
--->
