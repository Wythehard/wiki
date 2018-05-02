### 建立一个硬连接

ln (-s) 要连接目的地址  现在的地方

### 复制到剪切板

 Mac   echo 'Hello World!' | pbcopy

Linux    xsel



### 安装的软件

sudo apt-get install vim-gnome vim支持访问系统剪切板

sudo apt install xsel 系统支持剪切板



## 命令行

```
opt+ <- / -> 光标移动一个单词
Ctrl+r 然后输入若干字符，开始向上搜索包含该字符的命令，继续按Ctrl+r，搜索上一条匹配的命令
ctrl+a 命令行首
ctrl+e 命令行尾


```

# 删除

 find ./ -name ".DS*" -print -exec rm -fr {} \;





## linux修改域名解析系统

```
1)修改DNS配置文件，保存重启网卡后文件内容还原，修改失败：
# sudo vi /etc/resolv.conf
nameserver 8.8.8.8
2)原来Ubuntu要修改如下文件才会起效：
# cd /etc/resolvconf/resolv.conf.d/
# vi base
nameserver 8.8.8.8
nameserver 18.18.18.18
3)重启网卡
sudo /etc/init.d/networking restart
```



# 监测端口 

socat 印象笔记里有操作方法

监听9000端口动静 socat TCP-LISTEN:700 -

测试端口连通 socat - TCP:localhost:80





grep -rn ""



## scp

```
scp -P 2580 /opt/soft/demo.tar root@10.6.159.147:/opt/soft/scptest
```


强制使用密码 ssh

`ssh -o PreferredAuthentications=password -o PubkeyAuthentication=no  -v genee@192.168.0.26`



后台运行 `**xxx >/dev/null 2>&1 &**` `gollum >/tmp/gollum.log 2>&1 &`

tar 压缩   c or x  -zxvf

传输文件   rsync -azvP  origintarget genee@10.0:path


### 与 scp 类似的工具
[rsync 的介绍](https://www.cnblogs.com/f-ck-need-u/p/7220009.html)
    前提是需要已经设置好 ssh
    rsync -vzrt  linzhen.wu@192.168.0.5:~/* .  其中 -v 详细信息  -z 压缩  -r 递归 -t 保留文件的时间信息。
    

