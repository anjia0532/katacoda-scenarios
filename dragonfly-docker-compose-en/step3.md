
Pull demo images and wait it done

`time docker pull registry.cn-hangzhou.aliyuncs.com/alidragonfly/supernode:0.2.0`{{execute T1}}

Watching dfdaemon log

`docker exec dfdaemon tail -f /var/log/dragonfly/daemon/core.log`{{execute T2}}

Remove demo image

`docker rmi registry.cn-hangzhou.aliyuncs.com/alidragonfly/supernode:0.2.0`{{execute T1}}

Rerun the pull command line

`time docker pull registry.cn-hangzhou.aliyuncs.com/alidragonfly/supernode:0.2.0`{{execute T1}}

Pickup `peer task done` log from `/var/log/dragonfly/daemon/core.log`

`docker exec dfdaemon grep "peer task done" /var/log/dragonfly/daemon/core.log`{{execute T2}}
