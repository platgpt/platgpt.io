

4. Ray Cluster: Monitoring with [Prometheus & Grafana](https://github.com/ray-project/kuberay/blob/master/docs/guidance/prometheus-grafana.md):


```
# Forward the port of Grafana
kubectl port-forward --address 0.0.0.0 deployment/prometheus-grafana -n prometheus-system 3000:3000

# Check ${YOUR_IP}:3000 for the Grafana login page (e.g. 127.0.0.1:3000).
# The default username is "admin" and the password is "prom-operator".
```