The following article provides the pre-requisites and instructions to install AccuKnox S3 Audit Reporter agent to monitor access logs of S3 buckets and export relevent metrics to AccuKnox Control Plane.

## Requirements
The following software and network requirements must be met.

### AWS S3 Requirements
For any AWS S3 bucket that needs to be monitored, we need the following requirements to be met with:

1. Enable the AWS S3 Access Logs - [https://docs.aws.amazon.com/AmazonS3/latest/userguide/enable-server-access-logging.html](https://docs.aws.amazon.com/AmazonS3/latest/userguide/enable-server-access-logging.html)

2. Create AWS user credentials(access key id and secret access key) for the Data Bucket - the bucket that contains the objects to be monitored. This user credentials must have permission to list the objects in the data bucket.

3. Create AWS user credentials(access key id and secret access key) for the Logs Bucket - the bucket that contains the logs objects. This user credentials must have permissions to list the objects and retreive the objects present in the logs bucket.

### Software Requirements
AccuKnox S3 Audit Reporter supports Linux and can be run on most major Linux based OSes such as Ubuntu 18.04+, Debian 8+, CentOS 7+.

### Network Requirements
AccuKnox S3 Audit Reporter requires port number 443 to be open for egress. This port will be used to fetch S3 Access Log data, Bucket data and to push metrics to AccuKnox Control Plane.

## AWS S3 Bucket configuration
AccuKnox S3 Audit Reporter can monitor more than 1 bucket at a time. 

The bucket to be monitored is configured through a file located at conf/buckets.yaml The following is an example of a buckets.yaml:

```
apiVersion: v1
type: S3AuditReporterBuckets
data:
  workspace: 30921123
  apiToken: as013n21m3nkjn2m1m97sd
  buckets:
    - dataBucketName: bucket-1
      logsBucketName: bucket-1-logs
      logPrefix: logs/
      dataBucketAccessKeyId: AK.....
      dataBucketSecretAccessKey: 99.....
      logBucketAccessKeyId: AK...
      logBucketSecretAccessKey: 99....
      dataSourceProvider: AWS
      bucketRegion: us-west-2
    - dataBucketName: bucket-2
      logsBucketName: bucket-2-logs
      logPrefix:
      dataBucketAccessKeyId: AK.....
      dataBucketSecretAccessKey: 99.....
      logBucketAccessKeyId: AK...
      logBucketSecretAccessKey: 99....
      dataSourceProvider: AWS
      bucketRegion: us-west-2
```

## Installation
Unzip AccuKnox S3 Audit Reporter 

`unzip aks3r.zip -d aks3r`

Edit the conf/buckets.yaml

Configure the buckets to be monitored

Add the workspace

Add the apiToken

The app.yaml and buckets.yaml files must be present inside conf/ folder.

Run AccuKnox S3 Audit Reporter

`./asar > /dev/null 2>&1 &`