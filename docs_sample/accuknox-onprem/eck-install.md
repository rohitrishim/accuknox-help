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

### Add accuknox repository to install ECK helm package:

```sh
helm repo add accuknox-onprem-logging https://USERNAME:PASSWORD@agents.accuknox.com/repository/accuknox-onprem-logging
helm repo update
helm search repo accuknox-onprem-logging
helm pull accuknox-onprem-logging/eck-operator --untar
helm pull accuknox-onprem-logging/elasticsearch --untar
helm pull accuknox-onprem-logging/filebeat --untar
helm pull accuknox-onprem-logging/kibana --untar
```

```sh
Kubectl create namespace accuknox-logging
```
```sh
helm install eck-operator eck-operator -n accuknox-logging
helm install elasticsearch elasticsearch -n accuknox-logging
helm install filebeat filebeat -n accuknox-logging
helm install kibana kibana -n accuknox-logging
```

<b>How to verify</b>

```sh
kubectl get all -n accuknox-logging
```

You can see all the pods are up and running. 

Configuration of filebeat

After the verification you have to get the password for kibana to login

The default username is “elastic”

Command to get the password:

```sh
kubectl get secret elasticsearch-es-elastic-user  -o go-template='{{.data.elastic | base64decode}}' -n accuknox-logging
```

It will give you a decoded secret name

Once logged in with this username and password. 

Navigate to the Stack management->Index pattern->Create index pattern->filebeat-*->Next->choose timestamp

