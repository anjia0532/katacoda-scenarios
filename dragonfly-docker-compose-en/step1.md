### View Docker version and  Docker Compose version

`docker version`{{execute T1}}

`docker-compose version`{{execute T1}}

### Clone Dragonfly repo

`git clone https://github.com/dragonflyoss/Dragonfly2.git`{{execute T1}}

Wait for clone success.

### Get Local ip

`export IP=$(hostname -I | cut -d' ' -f1)`{{execute T1}}

### Startup Dragonfly by Docker Compose

`cd Dragonfly2/deploy/docker-compose/ && ./run.sh`{{execute T1}}

`docker-compose ps`{{execute T1}}

### Access Dragonfly Manager Console Web UI

Click `Manager Console UI` dashboard or this link [Manager Console UI](https://[[HOST_SUBDOMAIN]]-31234-[[KATACODA_HOST]].environments.katacoda.com)
