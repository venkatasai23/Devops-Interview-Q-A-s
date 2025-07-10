# 🚀 Terraform – Advanced Concepts

---

## 1. Workspaces

Used to manage multiple environments like dev/stage/prod.

terraform workspace new dev

### 2. terraform import

Adopt existing Azure resources into Terraform state.

terraform import azurerm_resource_group.rg /subscriptions/xxx/resourceGroups/test

### 3. Handle Resource Drift

Run terraform plan or refresh

Use import for missing resources

taint to recreate broken ones

### 4. terraform taint

Forces recreation:

terraform taint azurerm_virtual_machine.vm

### 5. Conditional Resource Deployment

count = var.enable_vm ? 1 : 0

### 6. Terraform Backend

Stores state file, supports locking.

### 7. Configure Azure Blob as Backend

terraform {
  backend "azurerm" {
    resource_group_name  = "rg"
    storage_account_name = "tfstate"
    container_name       = "state"
    key                  = "terraform.tfstate"
  }
}

### 8. Why Use Remote Backends?

Collaboration

Locking

Disaster recovery

### 9. Manage Secrets in Terraform

Use environment variables

Use Azure Key Vault data source

### 10. Azure Key Vault Integration

data "azurerm_key_vault_secret" "dbpass" {
  name         = "db-password"
  key_vault_id = azurerm_key_vault.kv.id
}

### 11. Implement RBAC with Terraform

Use azurerm_role_assignment to assign roles to identities.

### 12. Best Practices for Azure Projects

Use locals

Lock state

Isolate environments

DRY with modules

Use .terraform.lock.hcl

### 13. Azure DevOps Integration

Use pipelines with init, plan, apply, and manual approval steps.

### 14. Terraform Pipeline in Azure DevOps

Tasks:

Install Terraform

terraform init

terraform plan (with approval)

terraform apply

### 15. Secure State in CI/CD

Store in Azure backend, never expose in pipeline logs.

### 16. Approval Gates

Use Azure DevOps environments or manual checks before apply.
