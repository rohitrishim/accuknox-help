## Agent Metrics: FileBeat | Kibana | On-prem Metrics
### 1. Status of Feeder Agent running on Cluster:
Please run the below command to check if agent and dependent pods are up and running.
```sh
kubectl get all –n feeder-service
```
All the pods/services should be in <b>Running</b> state.

> **_NOTE:_** It's assumed that Feeder Agent is running on cluster if not kindly go through [this](#hyperlink) section

### 2. Beats Setup:
 - The agent will be spinned along with Filebeat running along as a sidecar.
 - The filebeat configuration file in the package can be updated to specific Elastic instances, and logs can be viewed in <b>Kibana</b>.

#### a. Elastic Configuration Parameters:
 - The below Configuration parameters can be updated for elastic configuration.
> <i>(If Default params needs to be modified)</i>
```yaml
 - name: ELASTICSEARCH_HOST
        value: https://elasticsearch-es-http
 - name: ELASTICSEARCH_PORT
        value: "9200"
 - name: ELASTICSEARCH_USERNAME
        value: "elastic"
 - name: ELASTICSEARCH_PASSWORD
        value: "xxxxxxxxxxxxx"
```

#### b. Command to be Used:
```sh
kubectl set env deploy/feeder -n feeder-service ELASTICSEARCH_HOST=”https://elasticsearch-es-http”
```

#### c. Update Log Path:
 - To Update the Log path configured, please modify the below log input path under file beat inputs.
```yaml
filebeat.inputs:
        - type: container
        paths:
        - /log_output/value.log
```

### 2. Kibana Dashboard
 - Once the filebeat starts listening, an index will be created or updated on the elastic configured and the pushed logs can be seen.
 - In order to create a dashboard, you will need to build visualizations. Kibana has two panels for this
    1. One called <b>Visualize</b> and
    2. Another called <b>Dashboard</b>
 - In order to create your dashboard, you will first create every individual visualization with the Visualize panel and save them.
 

### 3. Metrics:
 - Once the feeder agent starts running, check the logs using below command
```sh
Kubectl logs –f podname –n feeder-service
```
 - The logs will push the metric data to GRPC Client / Kafka, and the GRPC server in SaaS platform will be listening to this metrics and can be viewed in Prometheus.
> (prometheus-dev.accuknox.com)
 
 
### 4. On Prem Metrics:
 - To fetch the metrics in standalone environment, please write a scrape job in Prometheus with feeder service agent as a job name, and scrape the metrics from port <i>(:xxxx)</i>
```yaml
- job_name: "feeder-pod-agent"
        sample_limit: 10000
```
