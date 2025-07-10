# ☁️ Terraform – Fundamentals

---

## 1. What is Terraform and why use it with Azure?

Terraform is an open-source Infrastructure as Code (IaC) tool that allows you to define and provision Azure (and other cloud) infrastructure using declarative configuration files.

### 2. Terraform vs ARM Templates

| Feature            | Terraform           | ARM Templates        |
|--------------------|---------------------|----------------------|
| Language           | HCL (HashiCorp)     | JSON                 |
| Multi-cloud        | Yes                 | No (Azure-only)      |
| Reusability        | High (modules)      | Moderate             |
| State Management   | Yes                 | No                   |

### 3. Terraform Authentication with Azure

- Azure CLI (`az login`)
- Service Principal with Client ID/Secret
- Managed Identity (for automation)

---

### 4. Provider Block Example

```hcl

provider "azurerm" {
  features = {}
}

### 5. terraform init

Initializes working directory and downloads plugins/providers.

### 6. Define Azure Resource Group

resource "azurerm_resource_group" "rg" {
  name     = "my-rg"
  location = "eastus"
}

### 7. terraform plan / terraform apply

plan: Preview changes

apply: Execute changes

### 8. Destroy Resources

terraform destroy

### 9. What is Terraform State File?

Stores mapping of resources and their metadata.

### 10. Remote State in Azure

Use Azure Blob Storage backend to store state remotely with locking.

### 11. State Locking

Prevents concurrent state changes using blob lease locks.

### 12. Handle State File Corruption

Backup from .backup

Run terraform refresh

Use remote backend versioning

### 13. Define Variables

variable "location" {
  type    = string
  default = "eastus"
}

### 14. Input vs Output Variables

Input: Feed values into Terraform modules.

Output: Return useful data (like IPs, resource names).

### 15. Pass Sensitive Data

variable "client_secret" {
  sensitive = true
}
### 16. Use Locals

locals {
  env = "dev"
}
### 17. Output Block Example

output "app_ip" {
  value = azurerm_public_ip.app.ip_address
}
### 18. What Are Modules?

Reusable blocks of configuration for organizing large codebases.

### 19. Structure Modules for Azure Projects

modules/
  vnet/
  vm/
main.tf

### 20. Use Public Modules

module "vnet" {
  source  = "Azure/vnet/azurerm"
  version = "2.0.0"
}

### 21. Reusable Module for Azure VMs

Create variables for name, size, image; loop with count or for_each.

