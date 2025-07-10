# 🔄 Terraform – Scenario-Based Questions

---

## 1. Deploy 5 VMs in Different Subnets

Use modules with `for_each` over a map containing subnet data.

---

### 2. Upgrade Existing AKS Cluster

Update the `kubernetes_version` and re-apply the config.

---

### 3. terraform apply Fails Midway

- Identify failed resource
- Use `taint`, `import`, or remove from state
- Re-run apply

---

### 4. Azure Portal Changes Outside Terraform

Use:

terraform import
terraform refresh

### 5. Multi-Subscription Deployment

Use aliased providers:

provider "azurerm" {
  alias           = "sub1"
  subscription_id = var.sub1_id
}

provider "azurerm" {
  alias           = "sub2"
  subscription_id = var.sub2_id
}

### 6. Debug Terraform Errors

Use TF_LOG=DEBUG

Read error lines carefully

Re-run plan with -target

### 7. Provider Compatibility Issues

Update required_providers block

Run terraform init -upgrade

### 8. Critical Incident Solved Using Terraform

e.g., accidental VM deletion restored by state reapply.

### 9. Multi-Region Deployments

Use region-specific modules

Organize with workspaces or folders

### 10. Cost Optimization

Use azurerm_reserved_instance

Lower SKU sizes

Cleanup with terraform destroy -target

### 11. Compliance and Governance

Use policy_assignment resources

Tag everything

Enforce via CI/CD

### 12. Terraform Repo Structure

/modules
/environments/dev
/environments/prod

### 13. Complex Project From Scratch

E.g., full Azure Landing Zone: VNets, NSGs, AKS, Key Vaults, Monitoring.
