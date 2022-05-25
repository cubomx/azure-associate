# Azure Storage Explorer
Easy to access & edit data in Azure.

It is a GUI app to simplify access to, and the management of, data stored in Azure SAs.

Benefits:
- Easy to conn & manage multiple SAs
- Connect to Data Lake Storage
- Update & View entities in your Storage Accountss
- Free

Operations:
- Edit
- Download
- Copy
- Delete

Supported types:
- **Blob storage**: unstructured data 
- **Table storage**: NoSQL, semi-structured
- **Queue storage**: messages in a queue; HTTPS calls
- **Files**: file-sharing through SMB protocol
- **Azure Data Lake Storage**: (based on Apache Hadoop) for large data volumes; unstructured
& structured data. Storing and analyzing large data sets. It supports large data workloads. It's well suited to capture data of any type or size, and at any speed.


## Local emulators
In case you don't want to incur additional costs by using SAs: 
- **Azure Storage Emulator**: local instance of Microsoft SQL Server 2012 Express LocalDB (Table, Queue, Blob)
- **Azurite**: (Node.js), open-source that supports most Azure storage cmds (via API)

Emulator must be running before opening Storage Explorer, and connect via `Attach to a local emulator`.

## Connecting
You need 2 permissions: management & data. You could use it with only the data-layer permission (granted, at a minum, 
a read data role). Management role grants access to see lists of your various SAs, containers, and service
endpoints.

## Connection types
- Connection string
    - When user has data layer access
    - For Azure Data Lake blob container or std blob container
    - Requires more configuration
    - The account you use needs the right permissions & authorization
- Add resources by using Azure AD
- SAS URI
- Name & Key
- Attach to a local emulator
- Attach to Azure Data Lake Storage using a URI
    - Use Gen1
    - You need the URI of the Data Lake
