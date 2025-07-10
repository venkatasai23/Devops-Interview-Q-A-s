# 🧪 Kubernetes – Scenario‑Based Questions & Answers

This file covers real‑world troubleshooting, performance, security, and operational scenarios that come up frequently in interviews.

---

## 1. Pod CrashLoopBackOff  

**How to Diagnose & Fix**  

```bash

kubectl describe pod <pod>
kubectl logs <pod> --previous
Causes: bad entrypoint/command, missing env vars, mis‑mounted volumes.

```

Fix: correct command/args, validate ConfigMaps/Secrets, fix volume mounts, adjust probe timings.

### 2. Service Unreachable from Outside

``` bash

Symptoms: curl <NodeIP>:<NodePort> times out.

```

Steps:

``` bash

kubectl get svc → confirm type: and port mappings.

kubectl describe svc <name> → check Endpoints (zero endpoints = no healthy Pods).

kubectl get ep <name> → ensure Pod IPs listed.

```

Inspect firewall / cloud LB rules.

### 3. PVC Stuck in Pending

Diagnosis:

```bash

kubectl get pvc
kubectl describe pvc <name>
```

No matching PV: Create a PV with correct storageClassName/capacity.

Dynamic provisioning failure: Check StorageClass controller logs.

### 4. NodeDiskPressure Evictions

How to Recover:

```bash

kubectl describe node <node>
kubectl top node <node>

```

Free disk (remove logs, rotate).
Adjust eviction thresholds in kubelet config or --eviction-hard.

### 5. High API Server Latency / 503 Errors

Checks:

Control‑plane CPU/memory saturation (top, vmstat).

Etcd health:

```bash

kubectl get --raw /healthz/etcd

```

Audit logs for spikes.
Mitigation: Scale control plane, tune etcd (compaction, defragmentation).

### 6. High Pod Startup Time

Possible Causes:
Large container images → switch to smaller base or use imagePullPolicy.
Slow storage (PVC) → use faster class.
Readiness probe misconfigurations.

### 7. Unauthorized API Calls (RBAC)

Scenario: Developer sees “Forbidden” on kubectl get pods.
Fix:

Inspect Roles/ClusterRoles:

```bash

kubectl get role,clusterrole
```

Bind user/group via RoleBinding/ClusterRoleBinding.

### 8. Resource Starvation (OOMKills)

Symptoms: Pods terminating with OOMKilled.

Steps:

``` Text

1.kubectl describe pod <pod> → look for OOMKilled.

2.Review resources.requests and resources.limits in PodSpec.

3.Add appropriate requests/limits or optimize app memory.

```

### 9. Horizontal Pod Autoscaler (HPA) Not Scaling

Diagnose:

```bash

kubectl get hpa
kubectl describe hpa <name>
```

No metrics: Ensure Metrics Server is deployed and healthy.
Threshold never met: Check CPU/memory usage vs target, tune thresholds.

### 10. CronJob Failing to Run

Checks:

kubectl get cronjob → inspect .status.lastScheduleTime.

Look for suspended flag.

Describe Job created by CronJob:

```bash

kubectl get jobs --selector=job-name=<cronjob>
kubectl describe job <job>

```

`` Text
 Logs: kubectl logs job/<job>
``

### 11. NetworkPolicy Blocking Traffic

Problem: Pods cannot communicate after NP applied.
Solution:

Validate apiVersion: networking.k8s.io/v1 and kind: NetworkPolicy.

Ensure policies explicitly allow ingress/egress for needed labels/ports.

Use kubectl test pod to ping across namespaces.

### 12. Helm Chart Release Issues

Scenario: helm upgrade hangs or fails.
Troubleshoot:

``` Text
helm history <release>

helm rollback <release> [revision]

Inspect CRDs: Some charts require CRDs installed first.

```

Check Tiller logs (Helm v2) or server‑side logs (v3 plugin errors).

### 13. Custom Controller/Operator Misbehaving

How to Debug:

Check Operator logs:

```bash
kubectl logs deployment/<operator-name> -n <namespace>
Validate CR instance YAML against CRD’s spec.versions.schema.openAPIV3Schema.
Use kubectl get events -n <namespace> to catch validation errors.
```

### 14. Cluster Autoscaler Not Adding Nodes

Investigate:

Check ClusterAutoscaler logs (kube-system namespace).

Ensure nodegroup labels match CA filters.

Sufficient IAM permissions for cloud API (e.g., AWS/GCP).

Review pending Pods:

```bash

kubectl get pods --field-selector=status.phase=Pending
Look for scheduling issues (taints, node selectors).
```

### 15. Disaster Recovery – Etcd Backup & Restore

Backup:

``` bash

ETCDCTL_API=3 etcdctl snapshot save snapshot.db \
  --endpoints=<etcd-endpoint> --cacert=ca.crt --cert=peer.crt --key=peer.key
```

Restore:

```bash

ETCDCTL_API=3 etcdctl snapshot restore snapshot.db \
  --data-dir=/var/lib/etcd-new
```

Reconfigure systemd unit to point to new data dir, restart etcd.

### 16. Zero‑Downtime Configuration Rollout

Use Deployment with maxUnavailable: 0 and maxSurge: 1:

```yaml

strategy:
  type: RollingUpdate
  rollingUpdate:
    maxUnavailable: 0
    maxSurge: 1
```

### 17. Pod Evictions During Node Maintenance

Procedure:

```bash
kubectl drain <node> --ignore-daemonsets --delete-local-data
```

Perform maintenance

``` bash

kubectl uncordon <node>
```

Use PodDisruptionBudget to protect critical apps.

### 18. Logging & Monitoring Setup

Standard Tools:

Logging: EFK stack (Elasticsearch, Fluentd, Kibana) or Loki

Monitoring: Prometheus + Grafana

Metrics: Deploy Metrics Server + kube-state-metrics

Sample Prometheus scrape:

```yaml

- job_name: 'kubernetes-pods'
  kubernetes_sd_configs:
  - role: pod
```

### 19. Securing the Cluster

Network: Use NetworkPolicies to limit traffic.

Authentication: Enable OIDC or integrate with cloud IAM.

Admission Control: Use PodSecurityPolicy or OPA/Gatekeeper.

Audit Logs: Enable API server audit logging.

### 20. Rolling Back a Failed Release

Deployments:

```bash

kubectl rollout undo deployment/<name> --to-revision=<n>
```

Helm:

```bash
helm rollback <release> <revision>
```
