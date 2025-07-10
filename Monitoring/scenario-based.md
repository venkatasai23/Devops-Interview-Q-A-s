# 📊 Monitoring – Scenario‑Based Questions

---

## 1. Alert Flood During Incident

- Implement **inhibition rules** in Alertmanager  
- Add **silence** or **rate-limits**  
- Prioritize critical alerts first

---

## 2. Missing Metrics Data

- Verify exporter pods `Running`  
- Check scrape configs in `prometheus.yml`  
- Test endpoint: `curl <exporter>:<port>/metrics`

---

## 3. High Cardinality in Metrics

- Use relabeling to drop low‑value labels  
- Aggregate metrics in PromQL (e.g., `sum by (job)`)

---
