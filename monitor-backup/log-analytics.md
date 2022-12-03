# Log Analytics
Collect & analyze data generated by resources (cloud/on-premises). Query allows to:
- Join data from multiple tables
- Aggregate large sets of data
- Perform complex operations with minimal code

## Workspace
The first thing to do is **add a workspace**.
- Name
- Sub
- Resource Group
- Location (of VMs)
- Pricing (per GB)

## Visualize
- Create & save **Log Searches** to analyze it in the Portal.
- Log Searches to **run automatically** & create an alert.
- You **can export** data to PowerBI/Excel

## Queries
Use of KQL.
```kql
<TableName> where <Property> == <Value>
```

Each *data source* & *solution* stores its data in *dedicated tables* in the Log Analytics workspace.
Common query tables:
- Event
- Syslog
- Heartbeat (Agent health)
- Alert

Common operators:
- count
- limit
- summarize (produces a table that aggregates the content of the input table)
- top
- where