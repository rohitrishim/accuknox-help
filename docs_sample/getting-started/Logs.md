## Logs and Triggers
### 1. What Kind of Logs:
- The logs generated from each component like Network / System / Data Protection / Anamoly Detection can be viewed under Logs section.
- The logs can be viewed for independent workloads like K8's or VM's

Each of the component should be up and Running in the installed cluster for the logs to be seen in the <b>Workspace</b>.

> **_NOTE:_** It's assumed that All Agents is running on cluster if not kindly go through [this](#hyperlink) section

### 2. Triggers:
 - An Alert trigger is a rule which triggers information transfer through a known channel. Customer can send information [log] in Real Time when it occurs or on specified Frequency.
 - Frequency is configurable which can be Once In a Day/ Week / Month.
 - Predefined Filters (or) pre-saved global filters are search queries on logs that is already available in the system.
  - Example : show logs for traffic direction = "EGRESS"

### 3. Configuration of Alert Triggers:
- On the Logs page, after choosing specific log filter click on 'Create Trigger' button.
- The below fields needs to be entered with appropriate data:
  - <b>Name:</b> Enter the name for the trigger. You can set any name without special characters.
  - <b>When to Initiate:</b> The frequency of the trigger as Real Time / .
  - <b>Status:</b> Enter the severity for the trigger.
  - <b>Search Filter Data :</b> The filter log chosen in automatically populated here.<i>This is optional.</i>
  - <b>Predefined queries:</b> The list of predefined queries for this workspace is shown as default.
  - <b>Notification Channel:</b> Select the integration channel that needs to receive logs. Can be Slack/ Splunk / Cloudwatch / Elastic. (Note: Channel Integrations needs to be done beforehand)
  - <b>Save:</b> Click on Save for the trigger to get stored in database.


#### a. List Of Triggers:
 - Select Triggers from the left navigation to view the list of triggers created.
> <i>(If Default params needs to be modified)</i>
 - The below fields for each trigger can be viewed.
   - Alert Trigger : Name of the Trigger
   - Created At    : Time of Trigger Creation
   - Channel       : Integration Channel Name
   - Enable/Disable: Enabling / Disabling the trigger to forward the logs into Integration Channel.
   - Details       : The filter query of the associated Trigger.

#### b. Actions:
- Select the below Actions on the triggers to check working of logs forwarding.
> <i>(If Default params needs to be modified)</i>
- The below actions for each trigger can be selected.
  - Enable        : Enabling the trigger to forward the logs into Integration Channel.
  - Disable       : Disabling the trigger to not forward the logs into Integration Channel.
  - Delete        : Delete the Logs Trigger
  - Export        : Exporting the triggers in PDF format.


### 4. Logs Forwarding:
 - For each Enabled Trigger, please check the integrated channel to view the logs.
 - The Rule Engine matches the real time logs against the triggers created.
 - Frequency >> Real Time
  - The Network (OR) System (OR) S3 (OR) Data protection (OR) Anamoly Detection Logs in Real Time can be seen in integrated Channel as it happens.
 - Frequency >> Once in A Day
  - The Network (OR) System (OR) S3 (OR) Data protection (OR) Anamoly Detection Logs in Real Time can be seen in integrated Channel only Once in a Day.
 - Frequency >> Once in A Month
  - The Network (OR) System (OR) S3 (OR) Data protection (OR) Anamoly Detection Logs in Real Time can be seen in integrated Channel only Once in a Month.
 - Frequency >> Once in A Week
  - The Network (OR) System (OR) S3 (OR) Data protection (OR) Anamoly Detection Logs in Real Time can be seen in integrated Channel only Once in a Week.

> **_NOTE:_** Frequency reduces channel noise / and safely provides only one informational log on the channels based on frequency time period.
