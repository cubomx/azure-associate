# Incident response with alerting on Azure
Azure Monitor (reporting & analytics). Insights into the behavior & running of your env and apps. You can
respond proactively.

## Data types in Azure Monitor 
Sources: *Apps, OSs, Azure resources, Azure subs, Azure tenants*. Data type:
- **Metric**: numerical time-sensitive values.
- **Log**: structured, record-based log files.

## Signal types alerts
- **Metric**: provide an alert trigger when a specified threshold is exceeded.
- **Activity log**: notify when Azure resources change state (e.g. resource deleted)
- **Log**: alerts based on things written to log files (e.g. 404/500 return)

## Alert rule
- **Resource** (1+)
- **Condition**: 
    - Signal type. 
    - Alert logic (threshold, change state, log info)
- **Actions**:
    - Action: sending a email, webhook, SMS message
    - Action group: Unique set of recipients.
- **Alert details**:
    - Alert name & description:
    - Severity: 0->Critical, 1->Error, 2->Warning, 3->Informational, 4->Verbose

### Scope
- Metrics
- Log search queries
- Activity logs events
- Health of the underlying Azure platform
- Test for website availability

### Manage alert rules
View: doesn't show clasic alerts. You can apply filters by the following categories:
- Subs
- Alert condition
- Severity
- Time ranges

## Metric alerts
Runs metric alerts trigger conditions at regular intervals. If true, Azure Monitor sends a notification.
Another factor: condition type (static, dynamic).
- **Static**: simple static conditions.
- **Dynamic**: use ML to auto-improve the accuracy of thresholds. 
    - *Look-back period*: how many previous periods need to be evaluated.
    - *Number of violations*: times the logic condition has to deviate before firing a notification.

### Dimensions
You can target multiple related instances.

## Log alerts
For analytical historical data.
Can come from:
- Server logs
- App server logs
- App logs

### How
- How often to run
- Time period under eval
- Query to be run 

### Composition
- Log query
- Time period
- Frequency
- Threshold

### Metric measurement
Same as metric alert logs. Require additional criteria:
- **Aggregate function**: calculation made against the result data.
- **Group field**: (average grouped by computer)
- **Interval**
- **Threshold**

Add a level of tolerance to the results found.
Stateless.

## Activity log
To work with Azure resources. Receive notifications when specific changes occur on a resource within your Subs.
- **Specific operations**: Reports a change to an aspect of your subs.
- **Service health events**: incidents & maintenance. For a whole region.

### Composition
- **Category**: administrative, service health, autoscale, polciy, recommendation
- **Scope**
- **Resource group**
- **Resource type**
- **Operation name**
- **Level**: verbose, info, warn, error, or critical.
- **Status**: started, failed or succeded.
- **Event initiated by**: who.

### Actions when an alert happens
- Email, SMS, Push notification, Voice call, Azure function, Logic App, Notification to a webhook, ITSM ticket,
Runbook.
