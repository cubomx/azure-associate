# Tools

## Azure Cloud Shell
- Interactive 
- You can opt for Bash/PowerShell experience
- It is a browser-based command-line experience
- It does not belong to a local machine

Features:
- Persists `$HOME` using a **5-GB** image in your file share
- Automatic authentication
- Monaco editor
- Times out after 20 minutes without interaction
- Permissions as in Linux

## Azure PowerShell
Module that you add to PowerShell. You will be able to:
- Connect to your **Azure Subscription**
- Manage your resources

First commands: 
```ps
Connect-AzAccount
```

### Installation
```sh
brew install --cask powershell
```

```ps
Install-Module -Name Az -Scope CurrentUser -Repository PSGallery -Force
```

### Commands
Connect to Azure:
```ps
Connect-AzAccount -Tenant <TenantID>
```

Get SubscriptionID:
```ps
Get-AzSubscription -Tenant <TenantID>
```

Change subscription
```ps
Set-AzContext -Subscription <SubscriptionID>
```

```ps
Get-AzLocation
```

### Scripting
Capture input:
```ps
param([type]$name)
```

Create variable:
```ps
$variableName = <value>
```

For loop:
```ps
For ($i = initialValue; condition; increment)
```

## Azure CLI
[Install](https://docs.microsoft.com/en-us/learn/modules/control-azure-services-with-cli/3-exercise-install-and-run-the-azure-cli?pivots=macos)

Command-line program to:
- Connect to Azure
- Execute admnistrative commands on Azure resources

It is:
- Cross-platfrom
- Can be used **interactive** or **scripted** (as PowerShell)
- Commands are structured in
    - *groups*: represents a service provided by Azure
    - *subgroups*: divide commands for the services into logical groupings