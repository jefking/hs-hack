# hs-hack
## Tools
Git: Assume it is installed ;-)

[Azure](https://portal.azure.com)
[Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
[AZCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-linux)

## Resources
Storage Account
- Drive
LogicApp
ACI

## Algo
Create
- Resource Group
Execute Deployment
- ARM Template
    - Creates Storage
    - Creates ACI instance
    - Creates File Share (in Storage)
Upload Files (manually?)
Execute Deployment
- Create ACI
    - Custom Image
    - Map Drive
Wait for Complete (manually)
Download Files (manually)
Delete all resources (manually?)

## Commands
### Deploy
``
az group create -g hs-hack --location "West US 2"
``
``
az group deployment create --name process --resource-group hs-hack --template-file deploy.json --parameters customerName=contoso
``
### Upload