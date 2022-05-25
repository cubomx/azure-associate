# Azure Active Directory
It is Microsoft's *multi-tenant* cloud-based directory & identity management service.

## Benefits 
- SSO to a any cloud & on-premises web app (Microsoft 365, Workday)
- iOS, macOS, Android, Windows devices.
- Secure remote access to on-premises web applications (MF4, Conditional access policies, group-based access management)
- Extend AD to the cloud
- Protect sensitive data & applications:
    - Suspicious sign-in activities  & potential vulnerabilities
- Provide self-service application access & password management

## Concepts
**Identity:** *object* that can be **authenticated** (user & password). Also, apps & other servers (authentication through certificates or secret keys).

**Account**: identity that has data associated with it.

**Azure AD Account**: identity created through Azure AD/another Microsoft cloud service.

**Azure subscription**: used to pay for Azure cloud services.

**Azure tenant/directory**: a dedicated & trusted instance of Azure AD. 

## Differences with AD DS
Azure Directory Domain Services (AD DS) is the traditional deployment of Windows Server-based AD.

What it is?
- Identity solution
- REST API Querying
- Communication Protocols: HTTP/HTTPS (SAML, WS-Federation, OpenID Connect for authentication & OAuth for authorization)
- Federation Services
- Flat structure: not Organizational Units(oUs) or Group Policy Objects(GPOs)


## Editions
Free: included with an Azure subscription
Premium P1 & P2: available through a Microsoft Enterprise Agreement, Open Volume License Program, and the Cloud Solution Providers program. *Azure & Microsoft 365* subscribers can also buy AAD P1 & P2 online.

| Feature | Free | Microsoft 365 | P1 | P2 |
| ------- | ---- | ------------- | -- | -- |
| Directory Objects | <div align="center">500,000| <div align="center"> Unlimited | <div align="center">Unlimited | <div align="center">Unlimited |
| SSO | Unlimited | <div align="center">Unlimited | <div align="center">Unlimited | <div align="center">Unlimited |
| Core Identity & Access Managemnt | <div align="center">X | <div align="center">X | <div align="center">X | <div align="center">X |
| B2B Collaboration | <div align="center">X | <div align="center">X | <div align="center">X | <div align="center">X | 
| Identity & Access Management for Microsoft 365 apps | | <div align="center">X | <div align="center">X | <div align="center">X |
| Premium Features | | | <div align="center">X | <div align="center">X |
| Hybrid Identities | | | <div align="center">X | <div align="center">X |
| Advanced Group Access Management | | | <div align="center">X | <div align="center">X |
| Conditional Access | | | <div align="center">X | <div align="center">X | 
| Identity  Protection | | | | <div align="center">X |
| Identity Governance | | | | <div align="center">X |

**AAD Free**: 
- User & group management
- On-premises directory sync
- Basic reports
- SSO (Azure, Microsoft 365, other SaaS apps)

**AAD Microsoft 365 Apps**:
- Free features
- Identity & Access Management for Microsoft 365 apps
    - MFA
    - Group access management
    - Self-service password reset for cloud users

**AAD Premium P1**
- Free features
- Hybrid users (on-premises and cloud)
- Advanced administration:
    - Dynamic groups
    - Self-service group management
    - Microsoft Identity Manager (on-premises identity & access management suite)
    - Cloud write-back capabilties (self-service password reset for on-premises users)

- **AAD Premium P2**: 
- Free & P1 features
- AAD Identity Protection:
    - Help provide risk-based Conditional Access to your apps  & critical company data
- Privileged Identity Management:
    - Discover, restrict & monitor administrators and their access to resources and to provide just-in-time access
