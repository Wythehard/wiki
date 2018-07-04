`yum --enablerepo=extras install epel-release` 当出现 package not found 时执行
`iptables-save > bak.bak` 备份 iptables 规则
`iptables-restore < bak.bak` 备份 iptables 规则
`iptables -F`慎用 清空所有规则
`iptables -nL` 列出所有规则

`route` 列出本机路由表