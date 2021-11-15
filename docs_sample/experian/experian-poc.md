# Experian POC: Installation & Deployment Steps for Various Modules

## Installation Flow
### 1. Backend Platform
 - Kubernetes cluster
 - Installing the backend software components in the kubernetes cluster
  i. Setup Databases - MySQL, Pinot
  ii. Setup Kafka
  iii. Install Istio in Kubernetes
  iv. Microservices
  v. Setup Istio API Gateway (Internal)

### 2. UI - Frontend
 - Setup a VM with Nginx as webserver and point to the HTML UI build

### 3. S3 Data Audit POC
 1. Setup 5 S3 buckets (5 for Data Bucket, atleast 1 bucket for logs).
 2. Populate some files using the provided script.
 3. Setup the S3 Audit Log Reporter Agent in a VM.
 4. Configure the data buckets and logs buckets in YAML file.

**Note:** Please install the pre-requisites below before proceeding with deploying the modules:
 - MySql Operator
 - Kafka Operator
 - Pinot Deployment Steps
 - Istio & it's gateway installation
