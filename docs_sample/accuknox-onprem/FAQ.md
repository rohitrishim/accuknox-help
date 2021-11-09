## FAQ

### 1. Can I skip Pinot and send logs to my elastic or splunk cluster?
  - Yes, it's feasible. The feeder agent sends the logs to /var/log/*.log which can be pushed to ELK stack.
  - Please refer accuknox-onprem/elastic for specific details.
### 2.Can I send metrics to my time series?
  - Yes, it's feasible.Install a GRPc server, with TCP IP and port.
  - Map the GRPC server IP and port in Feeder Service.<connectToGRPC> method
