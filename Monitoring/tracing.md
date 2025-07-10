# 📊 Distributed Tracing

---

## 1. Why Tracing?

Gives visibility into request flows across microservices, root‑cause high latencies.

---

## 2. Tools

- **Jaeger**  
- **Zipkin**  
- **OpenTelemetry**

---

## 3. Instrumentation Example (OpenTelemetry)

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: otel-collector
spec:
  template:
    spec:
      containers:
      - name: otel-collector
        image: otel/opentelemetry-collector
        args: ["--config=/etc/otel/config.yaml"]
```
