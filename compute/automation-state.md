# Azure Automation State
Make sure tha VMs in a cluster are in a consistent state:
- Same software
- Same configs

## Azure Automation State Configuration
Built on PowerShell. Consistently deploy, monitor, automatic update the desired state. It uses
PowerShell Desired State Configuration. Centrally manages your DSC artifacts & the DSC process.

It has a built-in **pull server** where you can send configurations to the target nodes. You can
also use **Azure Monitor** logs to review compliance.

## PowerShell DSC
Declarative management platform used to *configure, deploy & control systems*.

## Local Configuration Management
Component of WinD Management Framework on WinD. Responsible for updating the state of a node:
1. Get state
2. Compare (.mof file)
3. Update to match desired state

Modes:
- **Push**: admin sends config (manually)
- **Pull**: every node requests config

## Support
- Linx
- WinD 7+, WinD Server 2019, 2016, 2012...

## Requirements
- Open port TCP 443
- Global URL: `<>.azure-automation.net`
- Agent service: `https://<workspaceId>.agentsvc.azure-automation.net`

## Use
```ps
Configuration MyDscConfiguration {              ##1
    Node "localhost" {                          ##2
        WindowsFeature MyFeatureInstance {      ##3
            Ensure = 'Present'
            Name = 'Web-Server'
        }
    }
}
MyDscConfiguration -OutputPath C:\temp\         ##4
```

Save credentials to a `PSCredential` object.

Push config:
```ps
Start-DscConfiguration -path D:\
```
