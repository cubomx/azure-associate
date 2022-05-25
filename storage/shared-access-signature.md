# Access to Azure Storage with SAS

Blob Storage is optimized for storing massive amounts of unstructured data. Every access to files stored 
in Azure requires authorization. SAS provides secure, delegated access to resources in your SA.

## Authorization options
Files stored in Azure Storage are accesed by clients over HTTP/HTTPS.

### Public Access
Anonymous public read access for containers and blobs. You need:
- Confgiure the SA to allow public access by setting `AllowBlobPublicAccess` property. You need to enabled 
public access to container
- Container has 2 possible settings: public access to a specific blob or the blobs within a container.

### Azure AD
Not storing credentials. First, authenticate a security principal that returns a *OAuth 2.0 token*. This is
passed to Azure Storage.

### Shared Key
2 512-bit access keys for every SA. Root access. Manage them with Azure Key Vault. Rotate keys.

### SAS
Grant granular access to files.
Types:
- **User delegation SAS**: only for Blob, secured with Azure AD credentials.
- **Service SAS**: secured with a SA key. Delegates access to a resource in any of the four Azure Storage services.
- **Account SAS**: similar to the previous, but can also control access to service-level operations (e.g. Get Service Stats).

## Best Practices
- Use HTTPS
- *User delegation* is the most secure.
- Small time for the *expiration time*
- Minimum-required privileges

## Stored access policy
- **Identifier**: name to reference
- **Start time**
- **Expiry time**
- **Permissions**
