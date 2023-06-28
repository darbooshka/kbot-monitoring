# kbot-monitoring

## Instruction

Monitoring stack is deployed using flux-gitops automation 
to namespace `otel-monitoring` in the `main` cluster.

### How to open Grafana Dashboard

1. Authenticate to Google Cloud.

```
gcloud init
gcloud auth login
```

2. Connect to cluster main. 

```
gcloud container clusters get-credentials main --zone us-central1-c --project k8s-k3s-386419
```

3. Activate port-forwarding to port `8080`.

```
gcloud container clusters get-credentials main --zone us-central1-c --project k8s-k3s-386419 \
 && kubectl port-forward --namespace otel-monitoring $(kubectl get pod --namespace otel-monitoring --selector="io.kompose.service=grafana" --output jsonpath='{.items[0].metadata.name}') 8080:3002
```

4. Open [localhost:8080](http://localhost:8080/) 

You can explore data-sources Prometheus, Loki and Node Exporter Full dashboard.

### Grafana dashboard demo

[![Grafana dashboard demo](https://img.youtube.com/vi/TAMhOHmhSBk/0.jpg)](https://www.youtube.com/watch?v=TAMhOHmhSBk)

