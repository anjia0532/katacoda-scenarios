
### 配置 Docker Registry

Modify Docker Daemon Config file

```sh
cat << EOF > /etc/docker/daemon.json
{
    "bip":"172.18.0.1/24",
    "debug": true,
    "storage-driver": "overlay",
    "registry-mirrors": ["http://127.0.0.1:65001","http://docker-registry-mirror.katacoda.com"]
}
EOF
```{{execute T1}}

Restart Docker Service

`service docker restart`{{execute T1}}
