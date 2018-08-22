`yum --enablerepo=extras install epel-release` 当出现 package not found 时执行

`iptables-save > bak.bak` 备份 iptables 规则

`iptables-restore < bak.bak` 备份 iptables 规则

`iptables -F`慎用 清空所有规则

`iptables -nL` 列出所有规则

`iptables -t nat -nL`  nat 显示带端口号的规则

`iptables -t nat -S`  nat 的规则

`route` 列出本机路由表

`service iptables restart` 重启防火墙

`\etc\sysconfig\iptables` 防火墙文件

`socat TCP_LISTEN:90 -` 监听本机 90 端口

`socat TCP:ip:90 -` 连接远程 90 端口

`netstat -anp` 查看端口占用情况