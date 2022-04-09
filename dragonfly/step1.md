
Startup Kubernetes by minikube

`minikube start`{{execute}}

`kubectl get nodes`{{execute}}

`wget https://get.helm.sh/helm-v3.8.1-linux-amd64.tar.gz`{{execute}}

`tar -zxvf helm-v3.8.1-linux-amd64.tar.gz && mv linux-amd64/helm /usr/local/bin/helm`{{execute}}

`helm --help`{{execute}}

`helm repo add dragonfly https://dragonflyoss.github.io/helm-charts/`{{execute}}

`helm install --create-namespace --namespace dragonfly-system dragonfly dragonfly/dragonfly -f /root/values.yaml`{{execute}}

`kubectl -n dragonfly-system wait --for=condition=ready --all --timeout=10m pod`{{execute}}

https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com