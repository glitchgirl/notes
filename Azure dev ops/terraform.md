# Terraform 

Terraform is an open-source infrastructure as code (IaC) tool that enables users to define and provision infrastructure using a declarative configuration language. Terraform allows you to describe your infrastructure, such as virtual machines, storage accounts, and networking components, in a configuration file. This file is typically written in HashiCorp Configuration Language (HCL).

# Basic overview:

- Create a configuration file, which describes the resources you want.
-  Run `terraform init` in the directory containing your Terraform configuration file.
-  Run `terraform plan` to see what changes Terraform will make to your infrastructure.
-  Run `terraform apply` to apply the changes specified in your configuration.
-  Then terraform will create/modify resources. It will also update the state file.

useful links:
[terraform azure getting started](https://developer.hashicorp.com/terraform/tutorials/azure-get-started?utm_offer=ARTICLE_PAGE&utm_content=DOCS&utm_source=WEBSITE&utm_medium=WEB_IO)
[Provising resources using terraform](https://learn.microsoft.com/en-us/azure/app-service/provision-resource-terraform)
[Creating a resource group using Terraform](https://learn.microsoft.com/en-us/azure/developer/terraform/create-resource-group?tabs=azure-cli)
