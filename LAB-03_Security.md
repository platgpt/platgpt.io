# Security

1. Install [pre-commit](https://pre-commit.com):

```
brew install pre-commit
pre-commit install
pre-commit run --all-files
TruffleHog...............................................................Passed
```

2. Install [trufflehog](https://github.com/trufflesecurity/trufflehog):
```
brew install trufflesecurity/trufflehog/trufflehog
```

3. Install [checkov](https://github.com/bridgecrewio/checkov):
```
brew install checkov
```

4. Install [trivy](https://github.com/aquasecurity/trivy):
```
brew install trivy
trivy k8s --report summary cluster
```

Trivy scans:
```
Container Image
Filesystem
Git Repository (remote)
Virtual Machine Image
Kubernetes
AWS
```
Findings:
```
OS packages and software dependencies in use (SBOM)
Known vulnerabilities (CVEs)
IaC issues and misconfigurations
Sensitive information and secrets
Software licenses
```

5. Install [cnspec](https://github.com/mondoohq/cnspec):
```
bash -c "$(curl -sSL https://install.mondoo.com/sh)"
cnspec scan k8s
```

6. Install [cnquery](https://github.com/mondoohq/cnquery):
```
bash -c "$(curl -sSL https://install.mondoo.com/sh)"
cnquery scan k8s
```

7. Install [Teleport](https://github.com/gravitational/teleport):
```
brew install teleport
helm repo add teleport https://charts.releases.teleport.dev

helm install teleport-cluster teleport/teleport-cluster --create-namespace --namespace=teleport-cluster --set clusterName=teleport.platgpt.io --set acme=true --set acmeEmail=sako@goupaz.com

MYIP=$(kubectl get services teleport-cluster -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
```

Add local user and role to login k8s cluster:
```
POD=$(kubectl get pod -l app=teleport-cluster -o jsonpath='{.items[0].metadata.name}' -n teleport-cluster)

kubectl exec -i ${POD} -n teleport-cluster -- tctl create -f < member.yaml 
kubectl exec -ti ${POD} -n teleport-cluster -- tctl  users add sako --roles=member
kubectl exec -i ${POD} -n teleport-cluster -- tctl get role/sako
export KUBECONFIG=teleport-kubeconfig.yaml
KUBECONFIG=teleport-kubeconfig.yaml tsh login --proxy=teleport.platgpt.io:443 --user=sako
```

## Reference
[Getting Started Teleport](https://goteleport.com/docs/kubernetes-access/getting-started/cluster)

