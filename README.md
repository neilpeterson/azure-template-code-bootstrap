This repository contains the Dockerfile and bootstrapping script used when deploying a Tailwind Traders learning path demo environment. A simple HelloWorld example can also be found in the [deployment](./deployment) directory. This example can be run using this deploy to Azure button.

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fneilpeterson%2Fazure-template-code-bootstrap%2Fmaster%2Fdeployment%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

## Solution details

Azure Resource Manager templates are great for deploying Azure resources however lack extensibility for preforming post-deployment configurations such as starting pods in Kubernetes or populating data in an Azure-based data store. This solution provides a mechanism for running arbitrary code alongside an Azure Resource Manager template. This code can be used for post-deployment configurations.

This solution uses the following tech:

- Azure Container Instance: Acts as the agent for running the arbitrary code.
- Managed Service Identity: Identity given to the Azure Container Instance for interfacing with Azure.

## Dockerfile

Creates the Docker image used by the container instance. This is where any tools and configurations for the Azure Container Instance need to be made. For instance, if your code requires Terraform, the Terraform installation routine would need to be added to the Dockerfile.

```
docker build -t neilpeterson/itt-bootstrap .
```