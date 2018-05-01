### 修改docker0网卡

sudo vi /etc/default/docker

行尾追加:

DOCKER_OPTS="--bip=172.17.42.1/24"

sudo vim /lib/systemd/system/docker.service  中的内容应该如下

```
[Unit]
Description=Docker Application Container Engine
Documentation=https://docs.docker.com
After=network.target docker.socket firewalld.service
#After=network-online.target docker.socket firewalld.service
#Wants=network-online.target ---del
Requires=docker.socket
[Service]
Type=notify
# the default is not to use systemd for cgroups because the delegate issues still
# exists and systemd currently does not support the cgroup feature set required
# for containers run by docker
ExecStart=/usr/bin/dockerd -H fd:// $DOCKER_OPTS
ExecReload=/bin/kill -s HUP $MAINPID
LimitNOFILE=1048576
# Having non-zero Limit*s causes performance problems due to accounting overhead
# in the kernel. We recommend using cgroups to do container-local accounting.
LimitNPROC=infinity
LimitCORE=infinity
# Uncomment TasksMax if your systemd version supports it.
# Only systemd 226 and above support this version.
TasksMax=infinity
TimeoutStartSec=0
# set delegate yes so that systemd does not reset the cgroups of docker containers
Delegate=yes
# kill only the docker process, not all processes in the cgroup
KillMode=process
EnvironmentFile=-/etc/default/docker
[Install]
WantedBy=multi-user.target

```

sudo systemctl daemon-reload

sudo service docker restart

Warning:docker.service changed on disk. Run 'systemctl daemon-reload' to reload units.





### 自动重启

docker up



### 查看容器日志

docker logs  -f --tail 10 contain-name 



### docker切换镜像源

```
一、预备工作：image 仓库的镜像网址
本教程需要从仓库下载 image 文件，但是国内访问 Docker 的官方仓库很慢，还经常断线，所以要把仓库网址改成国内的镜像站。这里推荐使用官方镜像 registry.docker-cn.com 。
下面是我的 Debian 系统的默认仓库修改方法，其他系统的修改方法参考[官方文档](https://www.docker-cn.com/registry-mirror)
打开/etc/default/docker文件（需要sudo权限），在文件的底部加上一行。DOCKER_OPTS="--registry-mirror=https://registry.docker-cn.com"

然后，重启 Docker 服务。

$ sudo service docker restart

现在就会自动从镜像仓库下载 image 文件了。
```


### docker container cp 容器文件复制

`docker container cp`命令用于从正在运行的 Docker 容器里面，将文件拷贝到本机。下面是拷贝到当前目录的写法。$ docker container cp [containID]:[/path/to/file] .





### node.js



### 展示绑定目录

docker inspect --format='{{json .Mounts}}'



`docker run -v /home/www/data/cgi.log:/tmp/cgi.log -v /home/www/data:/data -v  /home/www/data/php.ini:/usr/local/etc/php/php.ini -p 9000:9000 -d --name php7 php:v3`