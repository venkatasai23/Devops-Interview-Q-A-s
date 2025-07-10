# 🚀 CI/CD – Rollback Strategies

---

## 1. Blue/Green Deployment

-Deploy new version to “green” environment  

- Switch router/LB from blue → green  

- Rollback: switch back to blue

---

## 2. Canary Releases

- Gradually shift percentage of traffic to new version  

- Monitor metrics (error rate, latency)  

- Automated rollback on threshold breach

---

## 3. Feature Flags

- Deploy code guarded by flags  

- Enable/disable features without redeploy  

- Quick rollback by flipping flag

---
