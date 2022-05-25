# Azure AD

## Azure AD join
Provides access to organizational apps & resources and to simplify Windows deployments of work-owned devices.

Benefits:
- SSO to Azure-managed SaaS apps & services.
- **Enterprise state roaming** of user settings across joined devices.
- **Access to Microsoft Store for Business** using an Azure AD account.
- Windows Hello support for secure & convenient access to work resources.
- **Restriction of access** to apps from only devices that meet compliance policy.
- **Seamless access to on-premise resources**

Connection options:
- **Registering** a device to Azure AD.
- **Joining** a device is an extension to registering a device (changes the local state of a device)

## Configure 

### Ways to define a user
- **Cloud identities**: only exist in Azure AD. Deleted when removed from the primary directory.
- **Directory-synchronized identities**: users exists in an on-premises AD.
- **Guest users**: exists outside Azure (useful with external vendors or contractors).

### Create user

- User profile is optional (picture, job, info)
- Deleted users can be restored for 30 days
- Sign in & audit log infor is available

In bulk: fill out a CSV template.

### Creating group accounts
Two kinds:
- **Security groups**: used to manage member & computer access to *shared resources* for a group of users (e.g. you can create a security group for a specific security policy).
- **Microsoft 365 apps**: giving members access to a shared mailbok, calendar, files, SharePoint site, and more.

Three ways to assign access rights:
- **Assigned**: add specific users to have unique permissions
- **Dynamic user**: Azure reviews the dynamic group rules for the directory to add/remove member.
- **Dynamic device** (security groups only): automatically add/remove devices depending on the device's attributes.

**Administrative unit**: to restrict administrative scope for independent divisions of any kind. You need *Global Administrator* or a *Privileged Role Administrator*.

## Subscriptions
A **region** is a *geographical* area on the planet with at least one datacenters. If more than 1, the datacenters are in close proximity & networked together with a *low-latency network*. More than 60 regions and available in 140 countries.

- Global Azure services that do not require a region: AAD, Microsoft Azure Traffic Manager, and Azure DNS.
- Each Azure region is paired with another within the same geography, together making a regional pair

**Regional pair**:
- It is desired to be 300 miles of separation between datacenters
- Data residency (tax, law enforcement)
- Region recovery order: recovery of one region per pair.

An **Azure subscription** is a *logical unit* of Azure services (linked to an Azure account).

### Get a subscription
- Enterprise agreement 
- Reseller: Open Licensing program
- Partners: who can *design & implement your Azure cloud solution*.
- Personal free account: free trial

Types of subscription:
- Free: credit for 30 days, free access to the most popular Azure products for 12 months, and access to 25+ products that are always free
- Pay-As-You-Go: charges you monthly for the service you used in that billing period.
- Enterprise Agreement: flexibility to cloud services & software licenses under 1 agreement, with discounts.
- Student: monetary credit to use the first 12 months

Azure **Cost Management** and **Billing Features** to conduct billinh administrative tasks and manage billing access to costs.

**Cost Management**: organizational cost & usage patterns with *advanced analytics*
- Usage-based costs consumed by *Azure services*
- Not shown: reservation purchases, support, and taxes.
- Predictive analytics

**Cost analysis**: explore & analyze your org costs.
- View aggregated costs
- Identify spending trends
- Estimate cost trends

**Budgets**: plan for & meet financial accountability. Prevent cost thresholds.

**Recommendations**: optimize & improve (idle/underutilized). 

**Exporting data**: you can set a daily scheduled export in CSV format and store the data files in Azure storage.

## Resource tagging
Apply tags to Azure resource to organize them by categories. This can help you group billing data.

- Max tags = 50
- Tags are not inherited

##  Cost savings
**Reservations**: paying ahead. You can save up to 72% on pay-as-you-go prices.

**Azure Hybrid Benefits**: maximize the value of existing on-premises Windows Server/SQL Server *license investments* when migrating to Azure.

Pricing can vary from one region to another.

**Pricing Calculator**: provides estimates in all areas of Azure (compute, networking, storage, web, and databases).

## Azure Policy
Management group provides a level of scope above subscriptions. You *apply your governance conditions* to the management group. Benefits:
- Organizational alignment
- Policies and spend budgets

The **Management Group ID** identifies the management group and cannot be modified after creation.

**Azure Policy** is a service that you use to create, assign, and manage policies. The policies enforce different rules over your resources (to stay compliant wijt corporate stds and SLA). 

Advantages: 
- Enforcement & compliance: real-time policy eval and enforcement. Periodic & on-demand compliance eval.
- At scale: policies are inherited. **Policy initiative** lets you apply multiple policies and aggregate *policy states*.
- Remediation

Important if you have:
- Multiple engineering teams
- Multiple subscriptions
- Need to standardize/enforce how cloud resources **are configured**
- Regulatory compliance, cost control, security, or design consistency

### Create Azure policies
- Check Policy Definition (expresses *what to evaluate/what actions to take*)
    - Conditions
    - Effects if the conditions are met
- Create **Iniatiative Definitions** (a set of Policy Definitions to help track compliance state)
- **Scope** the Initiative Definition (region, resource group)
- **View Policy Evaluation results**: once assigned, you can evaluate the state of compliance for all your resources. 
    - Compliance: you can set the **compliance state results** (yes/no).

**Policy Definitions have a specific JSON format**.


## RBAC
It is an authoriation system built on ARM that provides fine-grained access management of resources in Azure.
- **Security Principal**: it represents something that is requesting access.
- **Role definition**: collection of permissions that can be perfomed.
- **Scope**: level of access.
- **Assignment**: attaching a RD to a SP at a particular scope. Deny assignments are read-only. **Grant Access**

Role Definition:
```
Name: Owner
ID: 8e3af657-a8ff-443c-a75c-2fe8c4bcb65
IsCustom: False
Description: Manage everything, including access to resources
Actions: {*}
NotActions: {}
AssignableScopes: {/}
```

A **resource inherits** role assignments from its parent resource.

| Action | RBAC roles | AD roles |
| ------ | ---------- | -------- | 
| Access | Azure resources | Azure AD Resources |
| Scope | Multiple levels | Tenant level |
| Role info | Portal, CLI, ARM, PowerShell, REST | Admin Portal, 365 Admin Portal, Graph AzureAD  PowerShell |

4 Fundamnetal built-in roles:
- **Owner**: full access to all resources; can delegate access:
    - **Service Administrator** & **Co-Administrators** are assigned the Owner role at the subscription scope.
- **Contributor**: create & manage all types of Azure resources.
- **Reader**: view existing Azure resources.
- **User Access Administrator**: manage user access to Azure resources.

## Users & Groups in Azure AD
User account access:
- Type
- Role assignments
- Ownership of individual objects

**Administrator**
- control who is allowed to do what
- reset user passwords
- manage user licenses
- User Administrator/Global Administrator can create a new user whenever they want

**Members users**: native member
- for internal; default permissions
- cannot manage users

**Guest users**
- by default, members can invite guest users.
- external people

Create user:
```az
az ad user create
```

```ps
New-AzureADUser
```

Delete user:
```az
az ad user delete
```

```ps
Remove-AzureADUser
```

Types of assignment:
- **Direct**: assign to a user
- **Group**: all members will inherit the rights
- **Rule-based**: Determine membership based on user/device properties.

Azure AD Premium 2 dynamic user members.

With **Azure AD B2B** you can add people from other companies. Invite Azure AD org, group, 
or, app. Partner has the responsibility to manage its own identities. Easier than a federation.

**Federation**: you have a trust established with another org (or collection of domains), for
shared access to a set of resources.

## SSPR
- **Localization**: render SSPR page in the appropiate language
- **Verification**: username & captcha
- **Authentication**: enter data to identify user (enter a code or security questions)
    - External email
    - Code/call to mobile phone
    - Office phone call
    - Security questions
    - Mobile app code (like Authenticator app)
    - Mobile app notification (verify or deny in the app)
- **Password reset**: if passes, enter a new pass and confirm it
- **Notification**: message of confirmation sent to user

*In free and trial Azure AD organizations, phone call options aren't supported.*

**A strong, two-method authentication policy is always applied to accounts with an administrator role**. The security questions method isn't available.

Notifications:
- Notifies the user
- Notifies admins when another admin resets pass

Any user who is signed in can change their password, regardless of the edition of Azure AD.
If you're not signed in and you've forgotten your password or your password has expired, you can use SSPR in Azure AD Premium P1 or P2

This writeback support (changes between Cloud and on-premises) is available in Azure AD Premium P1 or P2. It's also available with Microsoft 365 Apps for business.

3 settings of SSPR:
- **Disabled**: no users can use SSPR (default).
- **Enabled**: all users can use SSPR.
- **Selected**: allows a group of users