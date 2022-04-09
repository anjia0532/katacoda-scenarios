
Startup Kubernetes by minikube

`minikube start`{{execute T1}}

`kubectl get nodes`{{execute T1}}

`wget https://get.helm.sh/helm-v3.8.1-linux-amd64.tar.gz`{{execute T1}}

`tar -zxvf helm-v3.8.1-linux-amd64.tar.gz && mv linux-amd64/helm /usr/local/bin/helm`{{execute T1}}

`helm --help`{{execute T1}}

`helm repo add dragonfly https://dragonflyoss.github.io/helm-charts/`{{execute T1}}

`/root/values.yaml`{{open}}

`helm install --create-namespace --namespace dragonfly-system dragonfly dragonfly/dragonfly -f /root/values.yaml`{{execute T1}}

`kubectl -n dragonfly-system wait --for=condition=ready --all --timeout=10m pod`{{execute T1}}

`kubectl -n dragonfly-system patch svc dragonfly-manager --type merge -p '{"spec":{"ports": [{"name": "http-rest","nodePort": 31234,"port": 8080,"protocol": "TCP","targetPort": 8080}]}}'`{{execute T1}}

https://[[HOST_SUBDOMAIN]]-31234-[[KATACODA_HOST]].environments.katacoda.com

`docker pull registry.cn-hangzhou.aliyuncs.com/alidragonfly/supernode:0.2.0`{{execute T1}}

`kubectl -n dragonfly-system exec -it $(kubectl -n dragonfly-system get pods --no-headers -o custom-columns=":metadata.name" -l component=dfdaemon | head -n1 ) -- tail -f /var/log/dragonfly/daemon/core.log`{{execute T2}}

`kubectl -n dragonfly-system exec -it $(kubectl -n dragonfly-system get pods --no-headers -o custom-columns=":metadata.name" -l component=dfdaemon | head -n1 ) -- grep "peer task done" /var/log/dragonfly/daemon/core.log | jq .`{{execute T2}}