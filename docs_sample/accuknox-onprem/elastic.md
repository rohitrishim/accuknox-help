## ELK

- Elasticsearch is a search and analytics engine. It is an open source, full-text search and analysis engine, based on the Apache Lucene search engine.
- Logstash is a log aggregator that collects data from various input sources, executes different transformations and enhancements and then ships the data to various supported output destinations.
- Kibana is a visualization layer that works on top of Elasticsearch, providing users with the ability to analyze and visualize the data. And last but not least — Beats are lightweight agents that are installed on edge hosts to collect different types of data for forwarding into the stack.

### 1. Status of Elastic with On prem Feeder:
Please run the below command to check if agent and dependent pods are up and running.
```sh
kubectl get all -n feeder-service
```
All the pods/services should be in <b>Running</b> state.


### 3. Metrics:
- Once the feeder agent starts running, check the logs using below command
```sh
Kubectl logs –f podname –n feeder-service
```
