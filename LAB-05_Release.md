
1. Install ArgoCD in k8s cluster:
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

2. Install ArgoCD CLI:
```
brew install argocd
```

The initial password for the admin account is auto-generated and stored as clear text in the field password in a secret named argocd-initial-admin-secret:
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

3. ArgoCD UI:
```
kubectl port-forward svc/argocd-server -n argocd 8080:443 &
```

4. Update pwd:
```
argocd login 127.0.0.1:8080
argocd account update-password
```

5. Add cluster:
```
argocd cluster add xxx
```

## Reference

[Getting started with ArgoCD](https://argo-cd.readthedocs.io/en/stable/getting_started)