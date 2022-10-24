# Azure App Services
Websites, mobile backends, web APIs. 

Reasons:
- **Multiple langs & frameworks**
- **CI/CD with**: Azure DevOps, GitHub, BitBucket, Docker Hub, or ACR.
- **Global sclae with HA**: scaling (auto, manual)
- **Serverless code**

## Creating
- Choose a **Resource Group** and **Service Plan**.
- OS: Linux or Windows
- Region
- **Runtime stack** (language, SDK)
- **Publish**: Code or a Docker Container

### Additional Settings
- **Always On**: keep the app up even if not traffic.
- **ARR affinity**: route to the same instance through all the session
- **Connection strings**: encrypted at rest & go through a encrypted channel

## CI/CD
**Automated Deployment**: Azure DevOps, GitHub, Bitbucket
**Manual Deployment**: push your code to Azure: Git, CLI (`webapp up`), Visual Studio, FTP/S

## Deployment slots
Live apps with their own hostnames
- **Validate app changes in stagging**

*Auto swap isn't currently supported in web apps on Linux* 

Swapped: versions, app settings, connection strs, handler, Azure CDN
Not swapped: TLS/SSL settings not public, endpoints, custom DN, scale settings, CORS, VNet integration, IP restrictions

## Secure
Use the separate module for:
- Authenticate users (provider)
- Token lifecycle
- Manages the auth session
- Injects indetity info into req headers

Types of anon auth:
1. Allow Anon req: u write code.
2. Allow only auth requests: u don't write code.

## Custom DN
1. Get your domain name in Azure or external
2. Create a DNS records to map the domain to the Web app:
    - A record: domain name to an IP
    - CNAME: domain name to domain name
3. Validate it.

## Backup
**Backup and Restore** feature (manually, scheduled).
- App config
- File contnet
- DB connected to your app

Considerations:
- Std or Premium tier
- SA and Container in the sane subscription.
- Up to 10 GB
- Not allowed firewall SA
- Partial backups

## Application Insights (Azure Monitor)
Auto detect performance anomalies, and includes powerful analyticatl tools.
- Diff platforms, on-premises, hybrid, public.

Features:
- Most visited pages, best performance pages.
- Dependency issues (slowdown)
- Exceptions
