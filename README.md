# Tools
- Git
- [Azure](https://portal.azure.com)
- [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
- [AZCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-linux)

# Azure Resources
- [Storage Account](https://docs.microsoft.com/en-us/azure/storage/)
    - [File Share](https://docs.microsoft.com/en-us/azure/storage/files/storage-files-introduction)
- [Container Instances](https://azure.microsoft.com/en-us/services/container-instances/)
    - Create Share
    - Process Imagery

# Algorithm
Create
- Resource Group
Execute Deployment ([1.deploy.json](https://github.com/jefking/hs-hack/blob/master/1.deploy.json))
- ARM Template
    - Creates Storage
    - Creates ACI instance
    - Creates File Share (in Storage)
Upload Files (manually?)
Execute Deployment ([2.deploy.json](https://github.com/jefking/hs-hack/blob/master/2.deploy.json))
- Create ACI
    - Custom Image
    - Map Drive
Wait for Complete (manually)
Download Files (manually)
Delete all resources (manually?)

# Commands
## Needed
- Resource Group Name (alpha-numeric)
- Resource Group Location (West US 2)
- Customer Name (alpha-numeric)
- Container Image Name

## Deploy
### Create Resource Group
``
az group create -g hs-hack --location "West US 2"
``

### Create File Share
``
az group deployment create --name process --resource-group hs-hack --template-file 1.deploy.json --parameters customerName=contoso
``

### Upload
How do we upload to Azure?

### Deploy Container to Process Files
``
az group deployment create --name process --resource-group hs-hack --template-file 2.deploy.json --parameters customerName=contoso
``

### Delete all cloud resources ($0)
``
az group delete -n hs-hack
``