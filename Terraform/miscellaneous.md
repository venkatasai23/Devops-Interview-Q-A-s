# 🧩 Terraform – Miscellaneous Topics

---

## 1. count vs for_each in Azure

- Use `count` for list iterations
count = length(var.subnets)
Use for_each for maps

for_each = var.subnet_map

### 2. Manage Env-Specific Config

Use workspaces (dev, prod)

Use terraform.tfvars

### 3. Manage Existing Resources

``` bash
terraform import <resource> <id>
```

### 4. Upgrade Terraform Providers

Update version in required_providers, then:

terraform init -upgrade

### 5. Data Sources (Azure Examples)

data "azurerm_client_config" "current" {}
data "azurerm_resource_group" "example" {
  name = "my-rg"
}

### 6. Use Dynamic Blocks

dynamic "rule" {
  for_each = var.rules
  content {
    name = rule.value.name
    ...
  }
}

### 7. Lifecycle Meta-Argument

lifecycle {
  prevent_destroy = true
  create_before_destroy = true
}

### 8. Manage Tags Across Resources

locals {
  common_tags = {
    env = "prod"
    owner = "team-x"
  }
}

### 9. Resource Dependencies

Terraform handles them automatically. Use depends_on for explicit links.

### 10. Blue-Green Deployment

Deploy new infra alongside old → switch traffic using DNS or load balancer.

### 11. Ensure Idempotency

Always use data sources, avoid hardcoded values, control drift.

### 12. terraform refresh

Refreshes state to sync with real infrastructure.
