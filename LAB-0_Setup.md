## Setup tooling

1. Create instance in GCP using [Google Free Credits](https://cloud.google.com/free)

2. Install [kind](https://kind.sigs.k8s.io/docs/user/quick-start/):

```
brew install kind
```

3. Install [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/#install-with-homebrew-on-macos):

```
brew install kubectl
```

4. Install [kubectx](https://formulae.brew.sh/formula/kubectx):
```
brew install kubectx
```

5. Install [Helm](https://helm.sh/docs/intro/install/):
```
brew install helm
```

6. Install [Docker Desktop](https://docs.docker.com/desktop/install/mac-install):


7. Install [Istio](https://istio.io/latest/docs/setup/platform-setup/kind):

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml

kubectl create serviceaccount -n kubernetes-dashboard admin-user
kubectl create clusterrolebinding -n kubernetes-dashboard admin-user --clusterrole cluster-admin --serviceaccount=kubernetes-dashboard:admin-user
 token=$(kubectl -n kubernetes-dashboard create token admin-user)
 echo $token
```

Login to [k8s Dashboard](http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/workloads?namespace=default)

8. Install [Helm Dashboard](https://github.com/komodorio/helm-dashboard.git):

```
helm plugin install https://github.com/komodorio/helm-dashboard.git
```

Start Helm Dashboard UI:
```
helm dashboard
```

# Install Ray

1. Install Ray using Helm:
```
helm repo add kuberay https://ray-project.github.io/kuberay-helm
helm install kuberay-operator kuberay/kuberay-operator --version 0.5.0
helm install raycluster kuberay/ray-cluster --version 0.5.0 --set image.tag=nightly-aarch64
```

3. Check the Kuberay Operator status:
```
kubectl get pods
NAME                                READY   STATUS    RESTARTS   AGE
kuberay-operator-86957f45c4-rr4bl   1/1     Running   0          113s
```