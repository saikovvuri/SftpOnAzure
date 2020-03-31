# SFTP server on Azure

__Deploy a SFTP server running as a container in an Azure Container Instance with Azure File Shares as the persistent storage__

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2Fazure-quickstart-templates%2Fmaster%2F101-storage-account-create%2Fazuredeploy.json)

>Note: This is a temporary proof of concept

# Deployment Steps via Az CLI

```
az group create --name <resourcegroup> --location <location>
az group deployment create --resource-group <resourcegroup> --template-file <template.json>
```

# Deployment results

- Template creates two users, with name and password provided as parameters
- Individual file shares will be created per user, which are bind mounted to container instance

# Testing 
- use a SFTP client like WinSCP
- use Container Instance's public IP as hostname
- use username/password for the 2 users to login and view/upload artifacts
- validate on azure file shares

# Future roadmap
- Supply list of users in config file and map to /etc/sftp/users.conf
- Users should use more secure way to login in like SSH keys. Mount public keys in the user's .ssh/keys directory
