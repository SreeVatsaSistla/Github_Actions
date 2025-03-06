# Terraform Module: ADF-IAC

## Overview

This Terraform module creates and configures an Azure Data Factory (ADF) instance with optional GitHub integration. It provides a way to manage virtual networks, public network access, and ADF identity configurations.

## Features

- Create and configure Azure Data Factory
- Optional GitHub integration for source control
- Manage virtual networks
- Control public network access
- Define identity type and configuration

## Usage

```hcl
module "adf_iac" {
  source = "path_to_your_module_or_registry_link"

  data_factory_name             = "example-adf"
  resource_group_name           = "example-rg"
  location                      = "East US"
  managed_vnet_enabled          = true
  public_network_access_enabled = true
  identity_type                 = "SystemAssigned"
  tags                          = {
    environment = "dev"
  }

  github_integration_enabled = true
  github_configuration = {
    account_name       = "example-account"
    branch_name        = "main"
    git_url            = "https://github.com/example/repo"
    publishing_enabled = true
    repository_name    = "repo"
    root_folder        = "/"
  }

  time_outs = {
    create = "30m"
    update = "30m"
    read   = "5m"
    delete = "30m"
  }
}
```

### Advanced Usage

```hcl
module "adf_iac_advanced" {
  source = "path_to_your_module_or_registry_link"

  data_factory_name             = "advanced-adf"
  resource_group_name           = "advanced-rg"
  location                      = "West US"
  managed_vnet_enabled          = false
  public_network_access_enabled = false
  identity_type                 = "UserAssigned"
  tags                          = {
    environment = "prod"
  }

  github_integration_enabled = true
  github_configuration = {
    account_name       = "advanced-account"
    branch_name        = "development"
    git_url            = "https://github.com/advanced/repo"
    publishing_enabled = false
    repository_name    = "advanced-repo"
    root_folder        = "/advanced"
  }

  time_outs = {
    create = "40m"
    update = "40m"
    read   = "10m"
    delete = "40m"
  }
}
```

## Inputs

| Name                            | Description                                                                                                       | Type     | Default                                                                                                                   | Required |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------- | -------- |
| `data_factory_name`             | Name of the Azure Data Factory instance                                                                           | string   | n/a                                                                                                                       | yes      |
| `resource_group_name`           | The name of the Azure Resource Group                                                                              | string   | n/a                                                                                                                       | yes      |
| `location`                      | The Azure region where the Data Factory will be deployed                                                          | string   | n/a                                                                                                                       | yes      |
| `managed_vnet_enabled`          | Enable managed virtual network in Data Factory                                                                    | bool     | false                                                                                                                     | no       |
| `public_network_access_enabled` | Allow public network access to Data Factory                                                                       | bool     | false                                                                                                                     | no       |
| `tags`                          | Tags                                                                                                              | map(any) | {}                                                                                                                        | no       |
| `github_integration_enabled`    | Boolean flag to enable GitHub integration for Data Factory                                                        | bool     | false                                                                                                                     | no       |
| `github_configuration`          | Configuration block for GitHub integration with Data Factory                                                      | object   | { account_name = "", branch_name = "", git_url = "", publishing_enabled = false, repository_name = "", root_folder = "" } | no       |
| `identity_type`                 | Specifies the type of identity used for Data Factory. Allowed values: 'SystemAssigned', 'UserAssigned', or 'None' | string   | n/a                                                                                                                       | yes      |
| `time_outs`                     | Custom timeouts for creating, updating, reading, and deleting the Data Factory instance                           | object   | { create = "30m", update = "30m", read = "5m", delete = "30m" }                                                           | no       |

## Outputs

| Name     | Description                               |
| -------- | ----------------------------------------- |
| `adf_id` | The ID of the Azure Data Factory instance |

## Requirements

| Name      | Version |
| --------- | ------- |
| terraform | >= 0.12 |

## Providers

| Name    | Version |
| ------- | ------- |
| azurerm | >= 2.0  |

## Resources

| Name                     | Type                 |
| ------------------------ | -------------------- |
| azurerm_data_factory.ADF | azurerm_data_factory |

You can copy and paste this into your README.md file. If you need any more help, feel free to ask!

Edit in Pages

AI-generated content may be incorrect

<!-- ## Contributing

If you would like to contribute to this module, please fork the repository, create a feature branch, and submit a pull request. We welcome all contributions!

## License

This module is licensed under the MIT License. -->
