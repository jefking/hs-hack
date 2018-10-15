# Tools
- Git
- Docker
- [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
- [AZCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-linux)

# [Azure](https://portal.azure.com)
- [Storage Account](https://docs.microsoft.com/en-us/azure/storage/)
    - [File Share](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-introduction)
- [Container Instances](https://azure.microsoft.com/en-us/services/container-instances/)
    - Creates Share (Azure CLI)
    - Processes Files (Custom Image)

# Algorithm
- Initialize
    - Resource Group (command)
- ARM Deployment (command [1.deploy.json](https://github.com/jefking/hs-hack/blob/master/1.deploy.json))
    - Creates Storage Account
    - Creates Azure Container Instance
        - Container creates File Share
- Upload Files (script)
- ARM Deployment (command [2.deploy.json](https://github.com/jefking/hs-hack/blob/master/2.deploy.json))
    - Deploy Custom Image to ACI
        - With Mapped File Share
- Wait for processing to complete (manually)
- Download Files (script)
- Delete all resources (command)

# Commands
## Specify
- Resource Group Name (alpha-numeric)
- Resource Group Location (West US 2)
- Customer Name (alpha-numeric)
- Container Image Name

## Deploy
### 1. Create Resource Group
``
az group create -g <resourceGroupName> --location "West US 2"
``

### 2. Setup File Share
``
az group deployment create --name setup --resource-group <resourceGroupName> --template-file 1.deploy.json --parameters customerName=<customerName>
``

### 3. Upload (untested)
``
azcopy --source /mnt/<customerName> --destination https://<storageAccountName>.blob.core.windows.net/<customerName> --dest-key <storageAccountKey>
``

### 4. Process Files (Container)
``
az group deployment create --name process --resource-group <resourceGroupName> --template-file 2.deploy.json --parameters 2.parameters.json
``

### 5. Download (untested)
``
azcopy --source https://<storageAccountName>.blob.core.windows.net/<customerName> --destination /mnt/<customerName> \ --source-key <storageAccountKey>
``

### 6. Delete Resources ($0)
``
az group delete -n <resourceGroupName>
``

# V.Next
1. Code changes
- Process terminates when done
- Don't delete files
- ini -> data store (later)
- processing can be per file (later)
2. Automation