## Channel Integration
Channel Integrations is the fourth sub-section of Workspace Manager.

This section is used to integrate external services with AccuKnox so you can export logs as well as metrics. These services include:

 1. Webhooks
 2. Slack
 3. Jira
 4. Elastic Search
 5. Pagerduty
 5. Syslog
 6. Splunk
 7. Email
 8. ServiceNow
 9. AWS CloudWatch

Choose any one of the services and click the <b>Integrate Now</b> button.

### 1. Integration of Slack:
#### a. Prerequisites:
 - You need a valid and active account in Slack.
 - After logging into your Slack channel, you must generate a Hook URL.
 - [Note]: If you don’t know how to get Hook URL then click this [link](https://slack.com/intl/en-in/help/articles/115005265063-Incoming-webhooks-for-Slack) and follow the steps.

#### b. Steps to Integrate:
 - Goto Channel Integration [URL](https://app.dev.accuknox.com/channel-integrations)
 - Click the Integrate Now button inside Slack
 - Here you'll be able to see these entries: 
    - <b>Integration Name:</b> Enter the name for the integration. You can set any name.
    - <b>Hook URL:</b> Enter your slack hook URL here.
    - <b>Sender Name:</b> Enter the sender name here.
    - <b>Channel Name:</b> Enter your slack channel name here.
    - <b><i>Message Title:</i></b> You can set a message title using this input field. <i>This is optional.</i>
    - <b><i>Tags to be sent with alerts:</i></b> You can set tags using this input field. <i>This is optional.</i>
 - Once you fill every field then click the button this will test whether your integration is working or not.
 - Click the Save button.

### 2. Integration of Splunk:
#### a. Prerequisites
 - You need a Splunk HTTP event collector URL for this Integration.
 - <b>[Note]:</b> If you don’t know how to get Splunk HTTP event collector URL then click this [link](https://docs.splunk.com/Documentation/SplunkCloud/8.2.2106/Data/UsetheHTTPEventCollector) 

#### b. Steps to Integrate:
 - Goto Channel Integration [URL](https://app.dev.accuknox.com/channel-integrations)
 - Click the Integrate Now button inside Splunk
 - Here you'll be able to see these entries:
    - <b>Integration Name:</b> Enter the name for the integration. You can set any name.
    - <b>Splunk HTTP event collector URL:</b> Enter your Splunk HTTP event collector URL here.
    - <b>Token:</b> Enter your Splunk Token here.
    - <b>Source:</b> Enter your Splunk channel name here.
    - <b>Index:</b> Enter your Splunk Index here.
    - <b>Source Type:</b> Enter your Source Type here.
    - <b>Enable HTTPS:</b> If you want HTTPS service then enable this button.
    - <b>Enable TLS Verify:</b> If you want TLS service then enable this button.
 - Once you fill every field then click the button this will test whether your integration is working or not.
 - Click the Save button.

