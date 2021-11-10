## Policy Auto Discovery

Accuknox policy auto-discovery engine leverages the pod visibility provided by KubeArmor and Cilium to auto-generate network and system policies.

![Policy Discovery](../assets/images/policy-discovery.png)

### Using Policy Discovery

KnoxAutoPolicy Service is installed along with other control plane elements.
```
kubectl apply -f https://raw.githubusercontent.com/accuknox/knoxAutoPolicy-deployment/6834f042b396bd4002bfaaf31a87f4b46af10442/k8s/deployment.yaml
```

### Fetch Auto Discovered Policies

The auto discovered policies could be kept in a MySQL DB or can be created as simple YAML files in the knoxAutoPolicy service pod. There is a [script provided](https://github.com/accuknox/explorer-charts/blob/main/get_discovered_yamls.sh) that can identify the knoxAutoPolicy service pod and pull the discovered policies.

```
./get_discovered_yamls.sh
```

Sample output:
```
❯ ./get_discovered_yamls.sh
Downloading discovered policies from pod=knoxautopolicy-74f5b5d65b-tv7v7
Got 9 cilium policies for namespace=explorer in file cilium_policies_explorer.yaml
Got 5 cilium policies for namespace=kube-system in file cilium_policies_kube-system.yaml
Got 2 cilium policies for namespace=spire in file cilium_policies_spire.yaml
Got 9 knox policies for namespace=explorer in file knox_policies_explorer.yaml
Got 5 knox policies for namespace=kube-system in file knox_policies_kube-system.yaml
Got 2 knox policies for namespace=spire in file knox_policies_spire.yaml
```

Internally the script using `kubectl cp` to copy the discovered YAML files from the knoxAutoPolicy service pods.

