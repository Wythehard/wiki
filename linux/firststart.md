> 主要来源 阮一峰老师的博客 [Linux服务器的初步配置流程](http://www.ruanyifeng.com/blog/2014/03/server_setup.html)

> 主要来源 阮一峰老师的博客 [Linux服务器的初步配置流程](http://www.ruanyifeng.com/blog/2014/03/server_setup.html)


主要针对Debian/Ubuntu系统

第一次登陆

    ssh root@128.199.209.242 登陆
    passwd 设置密码

创建一个新用户 -m 目录不存在则新建

    addgroup admin
    useradd -d /home/bill -s /bin/bash -m bill  
    passwd bill 
    usermod -a -G admin bill  //添加 bill 到 admin 组
    visudo     //为新用户设置 sudo 权限
  

//有的时候用的是 nano 编辑器，我一直不太会用，刚刚学了一下，记住 ctrl+o 是保存就可以啦。上下左右光标，就跟 text 一样，没有 vim 那么复杂

找到 
root    ALL=(ALL:ALL) ALL
添加一行
bill    ALL=(ALL) NOPASSWD: ALL

接下来就是配置 ssh 了。
首先，确定本机有SSH公钥（一般是文件~/.ssh/id_rsa.pub），如果没有的话，使用ssh-keygen命令生成一个
ssh 的基本命令  ssh -p 2222 (端口号)  username@ip 
如果你没有公钥，需要使用 ssh-keygen 生成一个公钥，一路回车即可。
在$HOME/.ssh/目录下，会新生成两个文件：id_rsa.pub和id_rsa。前者是你的公钥，后者是你的私钥。
ssh-copy-id user@host 命令，将自己的公钥上传到服务器中。
实际的原理操作是
`cat ~/.ssh/id_rsa.pub | ssh bill@128.199.209.242 'mkdir -p .ssh && cat - >> ~/.ssh/authorized_keys'`
ssh user@ip -t '在远程执行命令'        -t是交互式执行,会将结果展示出来。

然后需要配置服务端的 ssh 服务来保证安全然后，编辑SSH配置文件/etc/ssh/sshd_config。
sudo cp /etc/ssh/sshd_config ~ //备份
sudo nano /etc/ssh/sshd_config // 可安装 vim sudo apt-get install vim

Port 25000 连接端口。

```
Protocol 2

PermitRootLogin no
PermitEmptyPasswords no
PasswordAuthentication no

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile .ssh/authorized_keys

UseDNS no

AllowUsers bill       //一定要 allow 这个用户    ##指定允许通过远程访问的用户，多个用户以空格隔开
```


接着，改变authorized_keys文件的权限。


    sudo chmod 600 ~/.ssh/authorized_keys && chmod 700 ~/.ssh/


service ssh restart 重启 ssh 服务。ssh 还有隧道的功能，较为复杂。

下面的一步是可选的。在本机~/.ssh文件夹下创建config文件，内容如下。


    Host s1
    HostName 128.199.209.242
    User bill
    Port 25000

配置完成之后在本机上直接输入 ssh s1 就可以直接连接，十分方便。

第四步：运行环境配置

首先，检查服务器的区域设置。


    locale

如果结果不是en_US.UTF-8，建议都设成它。


    sudo locale-gen en_US en_US.UTF-8 en_CA.UTF-8
    sudo dpkg-reconfigure locales

然后，更新软件。


    sudo apt-get update
    sudo apt-get upgrade


最后，再根据需要，做一些安全设置，比如搭建防火墙，关闭HTTP、HTTPs、SSH以外的端口，再比如安装Fail2Ban，详细可参考这篇《Securing a Linux Server》。








