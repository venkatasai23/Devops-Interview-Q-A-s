# 🔐 Secrets Management

---

## 1. Vault vs Cloud KMS

- **HashiCorp Vault**: Dynamic secrets, leasing, revocation  

- **Azure Key Vault / AWS KMS**: Managed, integrated with IAM  

---

## 2. Injecting Secrets Securely

- CI/CD: use protected variables (e.g., GitHub Secrets)  
- Kubernetes: mount secrets via `secretKeyRef`  
- HashiCorp Vault Agent Injector

---

## 3. Rotating Secrets

- Automate rotation policy (e.g., every 30 days)  
- Use Vault’s dynamic credentials for DBs  
- Update dependent services automatically
