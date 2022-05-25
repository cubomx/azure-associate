# Configure Virtual Machine extensions
Automate the tasks of creating, maintaining, and removing VMs.

## Virtual Machine Extension
Small applifcation that provide post-deployment config & automation tasks on Azure VMs.
Can be:
- Managed with CLI, PowerShell, ARM, Portal.
- Used with a new VM deployment or run against a existing system

## Custom Script Extension
To automatically launch & execute VM customization tasks post configuration. You can install it in the
Portal. Once the resource is created, you will provide your PowerShell script. Scripts can come from Azure
Storage, GitHub or Portal. You can add your parameters.

Considerations
- Limit of 90 mins to run
- Dependencies should be accesible
- Take errors in account
- Protect/handle your sensitive data

## Desired State Configuration
Management platform in WinD PowerShell. Enables deploying & managing config data for software services and 
managing the environment of these services (How you want the env to be)

```powershell
configuration IISInstall
{
Node “localhost”
{
WindowsFeature IIS
{
Ensure = “Present”
Name = “Web-Server”
} } }
```