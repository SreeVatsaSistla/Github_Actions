## Modules

This repository includes the following Terraform modules:

### **ADF-IAC**

- **Description**: Manages Azure Data Factory infrastructure as code.
- **Purpose**: Automates the creation and management of Azure Data Factory resources, which are used for data integration and transformation.

### **APP-CONFIGURATION-IAC**

- **Description**: Manages Azure App Configuration resources.
- **Purpose**: Automates the setup of Azure App Configuration, a service that provides centralized configuration management for applications.

### **APPINSIGHTS-IAC**

- **Description**: Provisions Azure Application Insights resources.
- **Purpose**: Sets up Application Insights, a service that helps monitor the performance and usage of your applications.

### **AUTOMATIONACCOUNT-IAC**

- **Description**: Manages Azure Automation Account resources.
- **Purpose**: Automates the creation of Automation Accounts, which are used to automate tasks and orchestrate workflows in Azure.

### **KEYVAULT-IAC**

- **Description**: Manages Azure Key Vault resources.
- **Purpose**: Automates the provisioning of Key Vaults, which securely store and manage sensitive information like secrets, keys, and certificates.

### **LOGANALYTICS-IAC**

- **Description**: Provisions Azure Log Analytics resources.
- **Purpose**: Sets up Log Analytics workspaces, which collect and analyze log data from various sources for monitoring and troubleshooting.

### **SA-IAC**

- **Description**: Manages Azure Storage Account resources.
- **Purpose**: Automates the creation and management of Storage Accounts, which provide scalable and secure storage solutions for various types of data.

### **SERVICEBUS-IAC**

- **Description**: Provisions Azure Service Bus resources.
- **Purpose**: Sets up Service Bus namespaces and entities, which enable reliable messaging and communication between different applications and services.

Each module includes the following files:

- **`inputs.tf`**:
  - **Purpose**: Defines the input variables for the module. These variables allow you to customize the module's behavior and resources. For example, you might specify the name of a resource, its location, or other configuration details.
- **`main.tf`**:
  - **Purpose**: Contains the main Terraform configuration for the module. This file includes the resource definitions and any necessary logic to provision the infrastructure. It is the core of the module where the actual infrastructure is defined.
- **`outputs.tf`**:
  - **Purpose**: Defines the output variables for the module. These outputs provide useful information about the resources created by the module, which can be used in other parts of your Terraform configuration. For example, you might output the ID of a created resource or its endpoint URL.
