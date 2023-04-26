# Autscaler

1. Install autoscaling [Ray cluster](https://ray-project.github.io/kuberay/guidance/autoscaler/):
```
kubectl apply -f https://raw.githubusercontent.com/ray-project/kuberay/release-0.5/ray-operator/config/samples/ray-cluster.autoscaler.yaml
```

2. Check the status of Ray head and worker pods:
```
$ kubectl get pods
NAME                                             READY   STATUS    RESTARTS   AGE
raycluster-autoscaler-head-mgwwk                 2/2     Running   0          4m41s
raycluster-autoscaler-worker-small-group-fg4fv   1/1     Running   0          4m41s
```

3. Check logs:
```
 kubectl logs -f raycluster-autoscaler-head-4h247 autoscaler
``` 

4. Test Autoscaling:
```
export HEAD_POD=$(kubectl get pods -o custom-columns=POD:metadata.name | grep raycluster-autoscaler-head)
kubectl exec $HEAD_POD -it -c ray-head -- python -c "import ray;ray.init();ray.autoscaler.sdk.request_resources(num_cpus=4)"
```

## References
https://ray-project.github.io/kuberay/guidance/autoscaler
https://docs.ray.io/en/latest/cluster/kubernetes/user-guides.html