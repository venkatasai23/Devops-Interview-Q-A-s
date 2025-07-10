# 📊 Prometheus & Grafana

---

## 1. Prometheus Architecture

- **Server**: scrapes & stores TSDB  
- **Exporters**: expose metrics (node_exporter, kube-state-metrics)  
- **Alertmanager**: handles alerts

---

## 2. Basic PromQL Examples

```promql
# CPU usage per node
rate(node_cpu_seconds_total{mode!="idle"}[5m])
# HTTP 5xx error rate
sum(rate(http_requests_total{status=~"5.."}[5m]))
```

### 3. Grafana Dashboard

Connect Prometheus as data source

Use templated variables for multi‑cluster views

Configure alert rules (email, Slack)
