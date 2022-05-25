# Storage security

## Security strategies
- **Ecnryption**: all data encrypted (auto) using *Storage Service Encryption* (SSE).
- **Authentication**: Azure AD & RBAC support for Azure Storage (resource management ops & data ops)
    -  Assign RBAC roles scoped to the SA to security principals & Azure AD to authorize 
    resource management ops (key management)
    - Azure AD integration for Blob & Queue services
- **Data in transit**: using Client-Side Encryption, HTTPS, or SMB 3.0
- **Disk encryption**: VMs disks can be encrypted using Azure Disk Encryption
- **Shared Access Encryption**: delegated access to data objects can be granted using SAS.

## Authorization Options
- **Azure AD**: Microsoft's cloud-based identity & access management service. Fine-grained access to users,
groups, or appcs via RBAC.
- **Shared Key**: relies on account access keys 6 other params to produce an encrypted signature string
to pass in the Authorization header (on the request).
- **SAS**: delegate access to a particular resource in your account, specific permissions & over a 
specified time interval
- **Anon access to containers/blobs**

**SAS** it is a *URI* that grants restricted access rights to Azure Storage resources. Gives granular
control over the type of access:
- Account-level SAS can delegate acces to multiple storage services
- Interval over which is valid
- The permisssions (write, read)

*Service-level SAS delegates access to a resource in just on fht storage services*.

You can also specify:
- IP addresses/range of it
- Protocol

## URI
URI = storage resource URI + SAS Token
e. g = https://myaccount.blob.core.windows.net/?restype=service&comp=properties&sv=2015-04-05&ss=bf&srt=s&st=2015-04-29T22%3A18%3A26Z&se=2015-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https &sig=F%6GRVAZ5Cdj2Pw4txxxxx

## Storage Service Encryption
SSE for *data at rest* protects your data by ensuring your **organizational security** and **compliance commitments** are met.

SSE automatically encrypts you data before persisting. All is encrypted through 
256-bit AES encryption (block ciphers). **Secured by default**.

*Azure Key Vault* can manage your **encryption keys**. You can also generate them.
You can:
- Create
- Disable
- Audit
- Rotate
- Define access controls

This can be used with SSE. SA and the Key Vault must be in the same region (they 
can be in different subscriptions).

## Best Practices
- Use HTTPS for SAS
- Short time on unplanned SAS
- Clientes should automatically renew the SAS if necessary
- Set the start time in the past or don't set it
- Minimum required privileges
- Be careful with SAS, you will be billed for any usage
- Validate data before use
- SAS isn't always the correct choice
- **Storage Analytics** to monitor your app (logging & metrics)