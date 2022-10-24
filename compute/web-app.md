# Host Web App

## Azure App Service
Azure App Service: full managed web app hosting platform.

The slots are like the environments: prod, dev.

Sources (CI/CD):
- GitHub
- BitBucket
- Azure DevOps
- FTP
- Dropbox
- OneDrive

Manual sources:
- `git`
- `az webapp up`
- ZIP: `az webapp deployment source config-zip`
- WAR: Java. Use Kudu HTTP API: `http://<YourAppName>.scm.azurewebsites.net/api/wardeploy`
- 

You can also publish from Visual Studio via **Web Deploy** technology.

## App Service plans
Set of virtual server resources for App Service apps.
Pricing: bandwith + tier.