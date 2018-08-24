`yum --enablerepo=extras install epel-release` 当出现 package not found 时执行




### iptables 和路由相关
`iptables-save > bak.bak` 备份 iptables 规则

`iptables-restore < bak.bak` 备份 iptables 规则

`iptables -F`慎用 清空所有规则

`iptables -nL` 列出所有规则

`iptables -t nat -nL`  nat 显示带端口号的规则

`iptables -t nat -S`  nat 的规则

`route -n` 列出本机路由表  -n 为列出数字

`service iptables restart` 重启防火墙

`\etc\sysconfig\iptables` 防火墙文件

#### 开启转发功能
`sysctl -p` 列出

`vim /etc/sysctl.conf`  修改net.ipv4.ip_forward = 1 

##### 通过文件修改重启不失效
`vi /etc/sysconfig/network-script/route-eth0 `  用于 cent OS  `0.0.0.0 via 172.16.0.3 dev eth0`

`vi /etc/sysconfig/network-script/ifcfg-eth0`   用于 centOS 仅能设置默认网关

#### route 配置

ip route default via gateway地址 dev eth0
```
add 增加路由
del 删除路由
-net 设置到某个网段的路由
-host 设置到某台主机的路由
gw 出口网关 IP地址
dev 出口网关 物理设备名
```
