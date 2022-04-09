
Startup Kubernetes by minikube

`minikube start`{{execute T1}}

`kubectl get nodes`{{execute T1}}

`wget https://get.helm.sh/helm-v3.8.1-linux-amd64.tar.gz`{{execute T1}}

`tar -zxvf helm-v3.8.1-linux-amd64.tar.gz && mv linux-amd64/helm /usr/local/bin/helm`{{execute T1}}

`helm --help`{{execute T1}}

`helm repo add dragonfly https://dragonflyoss.github.io/helm-charts/`{{execute T1}}

`vim /root/values.yaml`{{execute T2}}

`:q`{{execute T2}}

`helm install --create-namespace --namespace dragonfly-system dragonfly dragonfly/dragonfly -f /root/values.yaml`{{execute T1}}

`kubectl -n dragonfly-system wait --for=condition=ready --all --timeout=10m pod`{{execute T1}}

https://[[HOST_SUBDOMAIN]]-32531-[[KATACODA_HOST]].environments.katacoda.com