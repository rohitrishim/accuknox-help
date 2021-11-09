In order to setup AccuKnox S3 Access Audit perform the following steps:

1. Visit [AccuKnox Platform](https://app.accuknox.com)

2. Login using the email and password.

3. Select or create a new workspace

4. On the left navigation pane, select Data Protection

5. Next, select Data Sources

6. Click on the Configure Data Source button at the top right corner

7. Choose No for Is the s3 bucket mounted inside a container workload?

8. Choose No for Is your S3 access log buckets accessible from outside your private network?

9. In our scenario, we do not have S3 bucket objects accessible from outside the private network, hence click on Done.

10. Follow the steps [here](s3-audit-reporter-installation-guide.md) to install the AccuKnox S3 Audit Reporter Agent.

11. Once the agent has been configured and is running, it'll start syncing the objects in the data bucket with AccuKnox Platform. 

12. Now, on the left navigation pane, under Data Protection, click on Sensitive Source Labels

13. Enter a value for Label.

14. Under S3 BUCKET on the left, select the bucket you want to configure sensitive sources from and select the objects that are sensitive on the right.

15. Click on Next.

16. We can skip the Configure Flagged Destination step.

17. Review the selection and click on Create.
