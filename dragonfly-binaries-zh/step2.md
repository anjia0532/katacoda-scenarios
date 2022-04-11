### Download the precompiled binaries

Download a binary package of the cdn. You can download one of the latest builds for Dragonfly on the [github releases page](https://github.com/dragonflyoss/Dragonfly2/releases)

Replace `x.y.z` to real version, e.g. `export version=2.0.2`

`export version=x.y.z`

`wget -o Dragonfly2_linux_amd64.tar.gz https://github.com/dragonflyoss/Dragonfly2/releases/download/v${version}/Dragonfly2_${version}_linux_amd64.tar.gz`{{execute T1}}

Wait for download success.

### Unzip the package

`tar -zxf Dragonfly2_linux_amd64.tar.gz -C /opt/dragonfly/`{{execute T1}}

### Configuration environment

`export PATH="/opt/dragonfly/:$PATH"`{{execute T1}}

### Configuration config file

```sh
mkdir -p /etc/dragonfly/ && \

ip=${IP:-$(hostname -i)} && \

sed "s,__IP__,$ip," template/cdn.template.yaml > /etc/dragonfly/cdn.yaml && \
sed "s,__IP__,$ip," template/dfget.template.yaml > /etc/dragonfly/dfget.yaml && \
sed "s,__IP__,$ip," template/scheduler.template.yaml > /etc/dragonfly/scheduler.yaml && \
sed "s,__IP__,$ip," template/manager.template.yaml > /etc/dragonfly/manager.yaml && \
```{{execute T1}}


`chmod +x /opt/dragonfly/manager && /opt/dragonfly/manager &`{{execute T1}}
`chmod +x /opt/dragonfly/cdn && /opt/dragonfly/cdn &`{{execute T1}}
`chmod +x /opt/dragonfly/scheduler  && /opt/dragonfly/scheduler &`{{execute T1}}
`chmod +x /opt/dragonfly/dfget && /opt/dragonfly/dfget daemon &`{{execute T1}}
