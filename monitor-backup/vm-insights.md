# Monitor by using Azure Monitor VM Insights
You can query logs for:
- Trend analysis
- Reporting
- Alerting

**Azure Monitor VM Insights** relies on Azure Monitor Logs. Predefined, curated monitoring experience (little 
configuration required). A table named *InsightsMetrics*: it includes performance & usage for VMs. You can see
the information in a meaningful way. You can process log data without exposing the underlying queries. Needs
to be configured.

## Azure platform logs
Collected by Azure Monitor. Provide comprehensive diagnostic & auditing info for Azure resources and the 
underlying Azure platform. Are:
- Resource logs
- Activity logs
- Azure AD logs

## Log Analytics workspace
Containers where Azure Monitor data is collected, aggregated, and analyzed. Ingestion types:
- VMs: Event, Syslog, Heartbeat, Perf
- Azure resources: Activity, Diagnostics
- Custom logs, Usage, others

### Level of access
**Access mode**: how users can access and scope. 2 options:
- *Workspace-context*: provides access to all logs in a workspace if permission is assigned. Queries are scoped 
to all data in all tables.
- *Resource-context*: Access to view logs for resources in all tables you have access. Scoped to only data
associated to resource.

**Access control mode**: how permissions work for a workspace:
- *Require workspace permissions*: access to all data in any table where permissios are defined (not RBAC). 
*Resource* or *workspace permissions* allows for granular RBAC. Permissions to a individual or a group.

**Table-level RBAC**: + granular data control. Define which data types are accessible to a set of users. 
Requires Azure custom roles.

## Agents
- **Azure Monitor** (newest): monitoring data from guest OS. To replace: Log Analytics agent & Azure diagnostics
extension.
- **Log Analytics**: logs & performance data for VMs in all environments. Works with:
    - VM Insights
    - Microsoft Defender for the Cloud
    - Microsoft Sentinel
    - Azure Automationa accounts
- **Azure diagnostics extension**: receive extra data from guest OS & workloads. Sent to Metrics. Boot 
diagnostics.
- **Dependency**: discovered data about certain processes running on VMs. Maps dependencies.

## Build Log queries
Use KQL to extract data. The next services use Log Analytics workspaces:
- Microsoft Defender for Cloud
- Microsoft Sentinel
- Azure Monitor App Insights

Where you can use log queries:
- **Alert rules**: log search at intervals.
- **Dashboards**: results of a log can be pinned to *Azure Dashboard*. You can visualize metric & log at once.
- **Export**: Data can be imported into Excel/PoweBI.
- **PowerShell**: can retrieve data.
- **Azure Monitor API**

