# sgy-xtra-credit-test

## Deploy webapp (wordpress + mysql)
From the root of the project run:
```bash
kubectl apply -k ./`
```


## Deploy Prometheus Operator
_Requires helm v2.x_

Initialize helm and install prometheus-operator chart:
```bash
helm init
helm install stable/prometheus-operator --name prometheus-operator --namespace monitoring
```


## Monitoring
### Prometheus
Set up port forwarding:
```bash
kubectl port-forward -n monitoring prometheus-prometheus-operator-prometheus-0 9090
```
Then open http://localhost:9090.

### Grafana
Set up port forwarding:
```bash
kubectl port-forward $(kubectl get  pods --selector=app=grafana -n  monitoring --output=jsonpath="{.items..metadata.name}") -n monitoring  3000
```
Then open http://localhost:3000, and login as **admin** with password **prom-operator**.

