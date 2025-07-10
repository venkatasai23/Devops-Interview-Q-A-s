# 🚀 CI/CD – Scenario‑Based Questions

---

## 1. Build Fails on Dependency Download

**Troubleshoot**:  

- Verify network/proxy settings in CI agent  
- Cache dependencies between runs  
- Lock versions in `pom.xml`/`package.json`

---

## 2. Tests Failing Only in CI

- Compare local vs CI env (OS, JDK, Node versions)  
- Check missing environment variables  
- Inspect test logs/artifacts

---

## 3. Deployment Stuck on “Applying Terraform”

- Ensure service principal has RBAC on target subscription  
- Verify remote state backend connectivity  
- Check Terraform logs (`TF_LOG=DEBUG`)

---
