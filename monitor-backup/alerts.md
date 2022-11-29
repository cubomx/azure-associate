# Azure alerts

## Benefits
- **Better notification system**: use action groups (groups of notifications and actions).
- **Unified authoring experience**: alerts for all.
- **View Log Analytics Alerts in Azure Portal**
- **Separation of Fired Alerts & Alert Rules**
- **Better workflow**: simpler.

Use:
- Metric values
- Log search queries
- Activity Log events
- Health of Azure
- Test for web site availability

### Alert states
- *New*: detected
- *Acknowledged*: admin has reviewed the alert and started working
- *Closes*: issue solved.

## Alert rules
Notify when important conditions are found in your monitoring data. Identify & address issues before the users 
notice them. Alerts (can be enabled/disabled):
- *Target resource*
- *Signal*: metric, log, app insights.
- *Criteria*: Signal & Logic (threshold)
- *Alert name*
- *Alert description*
- *Severity*: 0 to 4.
- *Action*

## Action groups
Collection of notification preferences (used by Azure Monitor & Service Health alerts). **Notifications**: 
configure the method in which users will be notified.
- **Email ARM role**: send email to the members of sub's role.
- **Email/SMS/Push/Voice**: any.

**Actions**: configure the method in which actions are perfomed when trigger.
- **Automation runbook**: Define, build, orchestrate, manage, and repor on workflows (support sys & net 
operational processes).
- **Azure Functions**: Serverless compute service to run event-triggered code (without provision).
- **ITSM**: Connect to IT Service Management product/service.
- **Logic App**: automating your workflows.
- **Webhook**: HTTPS/HTTP endpoint to communicate external apps.