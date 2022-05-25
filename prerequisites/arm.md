# Azure Resource Manager

## What it is?
It enables to work with the resources in your solution as a group (deploy, manage, and monitor).

### Benefits
- Grouping
- Repeat
- Declarative templates
- Define the dependencies
- Access control (RBAC)
- Apply tags
- Clarify your billing by sharind the same tag


## Resource Groups
Logical collection of resources:
- Resources can only exist in 1 resource group
- Resource groups cannot be renamed
- Resource groups can have resources of many different types (services)
- Resource groups can have resources from many different regions

### Considerations
- All resources in a group should share the same lifecycle
- Not limitation in adding/removing a resource to a resource group
- You can [move a resource](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/move-support-resources) between groups
- You can use a resource group to scope access control
- A resource can interact with resources in other resource groups

## Locks
Prevent any unintended modification or deletion. Only `Owner` & `Access Administrator` can create/delete management locks.

## Commands
Remove a Resource Group:
```ps
Remove-AzResourceGroup -Name <Name>
```

## [Limits](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits?toc=%2Fazure%2Fnetworking%2Ftoc.json)
### Management group
- **10, 000 management groups** per Azure AD tenant
- Unlimited subscriptions
- Root level + 6 levels of management groups hierarchy
- 800<sup>2</sup> management groups per location
- 10 locations of management groups level deployments

### Resource group
- 980 resource groups per subscription
- 4,194,304 B OF ARM API request size
- 50 tags per subscription (directly)
- 80,000 unique tag calculations per subscription
- 10 locations of subcription.level deployments

## Templates

## [Format](https://docs.microsoft.com/en-us/learn/modules/configure-resources-arm-templates/3-explore-template-schema)
- Written in JSON
    - `$schema`: location of the JSON schema file (**REQUIRED**)
    - `contentVersion`: version of the template (**REQUIRED**)
    - `parameters`
    - `variables`: values to simplify expressions
    - `functions`
    - `resources`: resource types to be managed (**REQUIRED**)
    - `outputs`

parameters format:
```json
"parameters": {
    "<parameter-name>" : {
        "type" : "<type-of-parameter-value>",
        "defaultValue": "<default-value-of-parameter>",
        "allowedValues": [ "<array-of-allowed-values>" ],
        "minValue": <minimum-value-for-int>,
        "maxValue": <maximum-value-for-int>,
        "minLength": <minimum-length-for-string-or-array>,
        "maxLength": <maximum-length-for-string-or-array-parameters>,
        "metadata": {
        "description": "<description-of-the parameter>"
        }
    }
}
```

### Benefits
- Consistency: a common language
- Complex deployments
- Reduce manual, error-prone tasks
- IaC
- Reusability
- Combine multiple templates
- Simplify orchestration
- Validates if the deployment won't have any issue
- Automate deployments
- Idempotent (always the same result)
