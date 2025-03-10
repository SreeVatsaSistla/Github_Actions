# Terraform Module: APP-CONFIGURATION-IAC

## Overview

This Terraform module creates and configures an Azure App Configuration instance. It provides a way to manage virtual networks, public network access, identity configurations, and replication options.

## Features

- Create and configure Azure App Configuration
- Manage virtual networks and private endpoints
- Control public network access
- Define identity type and configuration
- Enable replication and purge protection

## Usage

```hcl
module "app_configuration" {
  source = "path_to_your_module_or_registry_link"

  app_config_name             = "example-appconfig"
  location                    = "East US"
  resource_group_name         = "example-rg"
  tags                        = { environment = "dev" }
  enable_local_auth           = true
  enable_public_network       = "Disabled"
  enable_purge_protection     = false
  identity_type               = "SystemAssigned"
  sku                         = "standard"
  soft_delete_retention_days  = 30
  enable_replication          = true
  replicas                    = {
    replica1 = {
      name     = "example-replica"
      location = "West US"
    }
    replica2 = {
      name     = "example-replica2"
      location = "Central US"
    }
  }
  appconfig_subnet_id = "/subscriptions/xxxx/resourceGroups/xxxx/providers/Microsoft.Network/virtualNetworks/xxxx/subnets/xxxx"
}
Inputs
Name	Description	Type	Default	Required
app_config_name	The name of the Azure App Configuration instance	string	n/a	yes
location	The Azure region where the App Configuration will be deployed	string	n/a	yes
resource_group_name	The name of the Azure Resource Group	string	n/a	yes
tags	A map of tags to assign to the App Configuration	map(string)	{}	no
enable_local_auth	Enable local authentication for the App Configuration	bool	true	no
enable_public_network	Enable public network access. Allowed values are Enabled and Disabled.	string	"Disabled"	no
enable_purge_protection	Enable purge protection for the App Configuration	bool	false	no
identity_type	Specifies the type of identity used. Allowed values: 'SystemAssigned', 'UserAssigned', or 'None'	string	n/a	yes
sku	The SKU of the Azure App Configuration. Allowed values: 'free', 'standard', 'premium'	string	n/a	yes
soft_delete_retention_days	The number of days for soft delete retention	number	n/a	yes
enable_replication	Boolean flag to enable replication	bool	false	no
replicas	A map of replica locations for Azure App Configuration	map(object({ name = string, location = string }))	{}	no
appconfig_subnet_id	The ID of the subnet to which the App Configuration private endpoint will be connected	string	""	no
Outputs
Name	Description
appconfig_id	The ID of the App Configuration
appconfig_connection_string	The connection string for the App Configuration
Requirements
Name	Version
terraform	>= 0.12
Providers
Name	Version
azurerm	>= 2.0
Resources
Name	Type
azurerm_app_configuration.app_config	azurerm_app_configuration
azurerm_private_endpoint.app_config_private_endpoint	azurerm_private_endpoint
