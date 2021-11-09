## Temporal

- Temporal is an orchestration platform for microservices and a workflow engine that runs in a loop until the workflow is complete. The major advantages of temporal include
  - Handling intermittent failures
  - Re-running the failed operations until success.
  - Supporting long running operations.
  - Running multiple operations parallelly.

- Temporal are written in two types of special purpose functions:

### 1. What are workflows ?
 - Workflows can be seen as a set of tasks that has a specific goal to achieve and it will run until the goal is achieved. Workflow has various timeout options in order to stop the workflow if it runs for a longer period of time.

### 2.What are activities ?
 - Activities contain the business logic of the user application. It is invoked via workflow and task queues. Task queues are used to store activities in a queue and a worker comes and picks up an activity to get it done.

### 3.How are temporal workflows used in AccuKnox ?
 - There are various components in Accuknox such as Network, System, Anomaly Detection and Data protection and these components send logs to kafka topic.
 - The role of the workflow comes here where there are specific workflows for each component and they continuously run, scanning for logs from kafka.
 - The workflow runs without a pause since the logs from the specific components comes every second and it has to capture it and process the logs such that it can send it to different integration channels.
