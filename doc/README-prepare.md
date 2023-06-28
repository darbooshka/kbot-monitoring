# kbot-monitoring

## intruction

TBD

## preparation

```


kompose convert --file ./kbot/otel/docker-compose.yaml --out ./kbot-monitoring/otel

kompose convert --file ./kbot/otel/docker-compose.yaml --out ./kbot-monitoring/helm --chart

kompose convert --file ./kbot/otel/docker-compose.yaml --out ./kbot-monitoring/helm --chart --volumes configMap

kompose convert --file ./kbot/otel/docker-compose.yaml --out ./kbot-monitoring/helm --chart --volumes hostPath  --controller daemonSet
```

```
# Week 5
helm lint ./helm
helm template otel ./helm
helm package ./helm   
```

```
gcloud container clusters get-credentials main --zone us-central1-c --project k8s-k3s-386419 \
 && kubectl port-forward --namespace otel-monitoring $(kubectl get pod --namespace otel-monitoring --selector="io.kompose.service=grafana" --output jsonpath='{.items[0].metadata.name}') 8080:3002

 
```

```
  -c, --chart                    Create a Helm chart for converted objects
  -o, --out string                   Specify a file name or directory to save objects to (if path does not exist, a file will be created)
  --volumes string               Volumes to be generated ("persistentVolumeClaim"|"emptyDir"|"hostPath" | "configMap") (default "persistentVolumeClaim")
  -f, --file stringArray    Specify an alternative compose file
  --controller string            Set the output controller ("deployment"|"daemonSet"|"replicationController")
```
