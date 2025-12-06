# Kubernetes Monitoring Stack

Production-ready monitoring stack with Prometheus, Grafana, and Loki for comprehensive observability.

## Overview

This example deploys a complete monitoring and logging solution for Kubernetes clusters:

- **Prometheus** - Metrics collection and alerting
- **Grafana** - Visualization and dashboards
- **Loki** - Log aggregation
- **AlertManager** - Alert routing and management
- **Node Exporter** - Host metrics
- **kube-state-metrics** - K8s object metrics

## Architecture

```
┌─────────────────────────────────────────────────┐
│           Kubernetes Cluster                    │
├─────────────────────────────────────────────────┤
│                                                 │
│  ┌──────────┐     ┌──────────┐                │
│  │  Pods    │────▶│Prometheus│                │
│  └──────────┘     └────┬─────┘                │
│                        │                        │
│  ┌──────────┐          │      ┌──────────┐    │
│  │  Nodes   │──────────┼─────▶│ Grafana  │    │
│  └──────────┘          │      └──────────┘    │
│                        │                        │
│  ┌──────────┐     ┌────▼─────┐                │
│  │   Logs   │────▶│   Loki   │                │
│  └──────────┘     └──────────┘                │
│                                                 │
└─────────────────────────────────────────────────┘
```

## Prerequisites

- Kubernetes cluster >= 1.28
- kubectl configured
- Helm >= 3.0
- At least 4GB free RAM
- StorageClass for persistent volumes (recommended)

## Quick Start

### 1. Install using Helm

```bash
# Add Prometheus community chart repo
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

# Create monitoring namespace
kubectl create namespace monitoring

# Install kube-prometheus-stack
helm install prometheus prometheus-community/kube-prometheus-stack \
  --namespace monitoring \
  --values values.yaml
```

### 2. Access Grafana

```bash
# Get Grafana password
kubectl get secret -n monitoring prometheus-grafana \
  -o jsonpath="{.data.admin-password}" | base64 --decode ; echo

# Port forward to access
kubectl port-forward -n monitoring svc/prometheus-grafana 3000:80
```

Open http://localhost:3000 and login:
- Username: `admin`
- Password: (from command above)

### 3. Access Prometheus

```bash
kubectl port-forward -n monitoring svc/prometheus-kube-prometheus-prometheus 9090:9090
```

Open http://localhost:9090

## Configuration

### Custom values.yaml

```yaml
# values.yaml
prometheus:
  prometheusSpec:
    retention: 15d
    storageSpec:
      volumeClaimTemplate:
        spec:
          accessModes: ["ReadWriteOnce"]
          resources:
            requests:
              storage: 50Gi

grafana:
  adminPassword: "change-me-in-production"
  persistence:
    enabled: true
    size: 10Gi

  # Pre-configured dashboards
  dashboardProviders:
    dashboardproviders.yaml:
      apiVersion: 1
      providers:
      - name: 'default'
        folder: 'General'
        type: file
        options:
          path: /var/lib/grafana/dashboards/default

alertmanager:
  config:
    route:
      receiver: 'email'
      group_by: ['alertname', 'cluster']
    receivers:
    - name: 'email'
      email_configs:
      - to: 'alerts@techblendconsult.io'
        from: 'prometheus@techblendconsult.io'
        smarthost: 'smtp.gmail.com:587'
```

## Pre-built Dashboards

The stack includes dashboards for:

- **Kubernetes Cluster** - Overall cluster health
- **Node Metrics** - CPU, memory, disk, network
- **Pod Metrics** - Resource usage by pod
- **Persistent Volumes** - Storage metrics
- **CoreDNS** - DNS query metrics
- **API Server** - K8s API performance

## Alerts

Default alerts include:

- **Node Down** - Node unreachable
- **High CPU** - Node CPU > 80%
- **High Memory** - Node memory > 80%
- **Pod CrashLoop** - Pod repeatedly crashing
- **Disk Full** - Node disk > 85%

### Custom Alerts

Add custom alerts via PrometheusRule:

```yaml
apiVersion: monitoring.coreos.com/v1
kind: PrometheusRule
metadata:
  name: custom-alerts
  namespace: monitoring
spec:
  groups:
  - name: custom
    rules:
    - alert: HighErrorRate
      expr: rate(http_requests_total{status=~"5.."}[5m]) > 0.05
      for: 5m
      annotations:
        summary: "High error rate detected"
```

## Production Considerations

### Security

1. **Change default passwords**
```bash
helm upgrade prometheus prometheus-community/kube-prometheus-stack \
  --set grafana.adminPassword=STRONG_PASSWORD_HERE
```

2. **Enable TLS** for Grafana and Prometheus

3. **Use RBAC** to restrict access

4. **Network Policies** to isolate monitoring namespace

### High Availability

For production, enable HA mode:

```yaml
prometheus:
  prometheusSpec:
    replicas: 2

alertmanager:
  alertmanagerSpec:
    replicas: 3

grafana:
  replicas: 2
```

### Resource Requests

Adjust based on cluster size:

```yaml
prometheus:
  prometheusSpec:
    resources:
      requests:
        memory: 4Gi
        cpu: 2000m
      limits:
        memory: 8Gi
        cpu: 4000m
```

### Data Retention

Balance between cost and data needs:

```yaml
prometheus:
  prometheusSpec:
    retention: 30d  # Adjust based on compliance requirements
```

## Cost Optimization

- Use `storageClass` with cost-effective storage
- Set appropriate retention periods
- Enable compression for long-term storage
- Consider remote storage (Thanos, Cortex) for large clusters

## Troubleshooting

### Prometheus Not Scraping Targets

```bash
# Check ServiceMonitor resources
kubectl get servicemonitor -n monitoring

# Check Prometheus config
kubectl get secret prometheus-prometheus-kube-prometheus-prometheus \
  -n monitoring -o jsonpath='{.data.prometheus\.yaml\.gz}' | \
  base64 -d | gunzip
```

### Grafana Dashboards Empty

```bash
# Verify Grafana datasource
kubectl exec -n monitoring prometheus-grafana-xxx -- \
  curl http://localhost:3000/api/datasources

# Check Prometheus connectivity
kubectl logs -n monitoring prometheus-grafana-xxx
```

### High Memory Usage

```bash
# Check Prometheus metrics
kubectl exec -n monitoring prometheus-prometheus-kube-prometheus-prometheus-0 -- \
  promtool tsdb analyze /prometheus
```

## Customization

### Add Custom Dashboards

```bash
# Export dashboard JSON from Grafana
# Create ConfigMap
kubectl create configmap custom-dashboard \
  --from-file=dashboard.json \
  -n monitoring
```

### Monitor Custom Applications

```yaml
apiVersion: monitoring.coreos.com/v1
kind: ServiceMonitor
metadata:
  name: my-app
  namespace: monitoring
spec:
  selector:
    matchLabels:
      app: my-app
  endpoints:
  - port: metrics
    interval: 30s
```

## Uninstall

```bash
helm uninstall prometheus -n monitoring
kubectl delete namespace monitoring
```

## Related Resources

- [Blog Post: Observability for Modern Systems](https://techblendconsult.io/blog/observability-modern-systems)
- [Prometheus Documentation](https://prometheus.io/docs/)
- [Grafana Documentation](https://grafana.com/docs/)

## Need Help?

**Free Resources:**
- [Discord Community](https://discord.gg/hk4ny22R)
- [Tech Blend Blog](https://techblendconsult.io/blog)

**Professional Services:**
- **Architecture Review**: 2-hour deep-dive ($997)
- **Custom Implementation**: Full setup and configuration ($5k-15k)
- **Team Training**: Hands-on observability workshop ($2k/day)

📅 [Schedule a free consultation](https://calendly.com/dennis-weston-techblendconsult/intro)
