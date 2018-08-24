### cent OS 的防火墙命令
[centOS](../centOS)

#### 添加端口。

firewall-cmd --permanent --add-port=3690/tcp

#### 永久打开端口好像需要reload一下，临时打开好像不用，如果用了reload临时打开的端口就失效了
#### 其它服务也可能是这样的，这个没有测试
firewall-cmd --reload

#### 查看防火墙，添加的端口也可以看到
firewall-cmd --list-all

cat /var/log/auth.log  查看登陆日志 相关网站 https://yepster.me/ssh-scan/

统计代码 sudo grep "Failed password for root" /var/log/auth.log | awk '{print $11}' | sort | uniq -c | sort -nr | more
sudo grep "Failed password for invalid user" /var/log/auth.log | awk '{print $13}' | sort | uniq -c | sort -nr | more

阻止 IP 名单 /etc/hosts.deny


