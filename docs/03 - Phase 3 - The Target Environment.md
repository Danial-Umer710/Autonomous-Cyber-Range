

# Phase 3: Observability & Monitoring

## Objectives
- [x] Deploy Prometheus to scrape cluster and application metrics
- [x] Install Grafana for telemetry visualization
- [x] Build a dashboard to monitor honeypot health and resource usage
- [x] Test ArgoCD self-healing and automated drift correction

## Tools Used
- Prometheus (Metrics scraping)
- Grafana (Visualization UI)

# Phase 3: Observability & Monitoring

## 1. Stack Deployment
- **Goal:** Deploy Prometheus and Grafana for cluster and honeypot telemetry.
- **Method:** Utilized Helm with the `prometheus-community/kube-prometheus-stack` chart in a dedicated `monitoring` namespace.

### Commands Used:
```bash
helm repo add prometheus-community [https://prometheus-community.github.io/helm-charts](https://prometheus-community.github.io/helm-charts)
helm repo update
kubectl create namespace monitoring
helm upgrade --install monitoring prometheus-community/kube-prometheus-stack --namespace monitoring 

Grafana Password: 2ft99EQTJmK5m282YtrsjJpgRjGlx6lRCx0QaOS1
```

## 2. Accessing Grafana
- **Goal:** Retrieve credentials and port-forward Grafana to visualize metrics.

### Commands Used:
```bash
# Retrieve admin password
kubectl get secret -n monitoring monitoring-grafana -o jsonpath="{.data.admin-password}" | base64 -d

# Port-forward to local machine
kubectl port-forward svc/monitoring-grafana -n monitoring 3000:80
```


