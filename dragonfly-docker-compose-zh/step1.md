### 查看 Docker 版本和 Docker Compose 版本

`docker version`{{execute T1}}

`docker-compose version`{{execute T1}}

### 克隆 Dragonfly 库

`git clone https://github.com/dragonflyoss/Dragonfly2.git`{{execute T1}}

等待 clone 成功。

### 获取本机 ip

`export IP=$(hostname -I | cut -d' ' -f1)`{{execute T1}}

### 使用 Docker Compose 启动 Dragonfly

`cd deploy/docker-compose && ./run.sh`{{execute T1}}

`docker-compose ps`{{execute T1}}
