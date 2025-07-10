# 🚀 CI/CD – Basics

---

## 1. What is CI/CD and why is it important?

**Continuous Integration (CI)** automates merging code changes into a shared repo, with builds & tests each commit.  

**Continuous Delivery (CD)** automatically deploys successful builds to staging/production.  
Benefits: faster feedback, reduced integration pain, higher deployment frequency.

---

## 2. CI vs CD vs Continuous Deployment

- **CD (Delivery)**: Manual approval before production.  

- **Continuous Deployment**: Fully automated deploy on success.

---

## 3. Popular CI/CD Tools

| Tool               | Features                                 |
|--------------------|------------------------------------------|
| Jenkins            | Extensible with plugins, self‑hosted     |
| GitHub Actions     | Native GitHub integration, YAML workflows |
| GitLab CI          | Integrated with GitLab, Docker support   |
| Azure Pipelines    | Multi‑cloud, deep Azure integration      |

---

## 4. Key Pipeline Stages

1. **Build**: Compile, lint, unit tests  
2. **Test**: Integration, security, performance tests  
3. **Deploy**: Provision infra (IaC), deploy artifact  

---
