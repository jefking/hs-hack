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

## Commands
### Deploy
``
az group create -g hs-job --location "West US 2"
``
``
az group deployment create --name process --resource-group hs-job --template-file deploy.json
``
### Upload