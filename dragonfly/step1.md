
Startup Kubernetes by minikube

`minikube start`{{execute}}

`kubectl get nodes`{{execute}}

`wget https://get.helm.sh/helm-v3.8.1-linux-amd64.tar.gz`{{execute}}

`tar -zxvf helm-v3.8.1-linux-amd64.tar.gz && mv linux-amd64/helm /usr/local/bin/helm`{{execute}}

`helm --help`{{execute}}

`helm repo add dragonfly https://dragonflyoss.github.io/helm-charts/`{{execute}}

```sh
cat << EOF > /tmp/values.yaml
apiVersion: v1
kind: Secret
metadata:
name: "storageos-api"
namespace: "storageos-operator"
labels:
app: "storageos"
type: "kubernetes.io/storageos"
EOF
```{{execute}}

`helm install --create-namespace --namespace dragonfly-system dragonfly dragonfly/dragonfly`{{execute}}

`kubectl -n dragonfly-system wait --for=condition=ready --all --timeout=10m pod`{{execute}}