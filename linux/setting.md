#linux 服务器基础设置
http://www.ruanyifeng.com/blog/2014/03/server_setup.html

#更改 apt-get 源
sudo vi /etc/apt/sources.list 即可 修改之前可以先备份。
每个版本的linux源地址不一样，可以去[阿里源](https://opsx.alibaba.com/mirror)上找
```
deb http://mirrors.aliyun.com/ubuntu/ xenial main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main

deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main

deb http://mirrors.aliyun.com/ubuntu/ xenial universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates universe

deb http://mirrors.aliyun.com/ubuntu/ xenial-security main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main
deb http://mirrors.aliyun.com/ubuntu/ xenial-security universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security universe
```
#设置 zsh 为默认shell
sudo chsh -s $(which zsh)设置zsh为默认shell


linux修改时区
TZ='Asia/Shanghai'; export TZ


mount -o remount,rw /dev/sda1 /
flkid

# docker 安装
 sudo apt-get install docker-ce
 sudo usermod -aG docker www

#linux 给用户加sudo权限
1、用root帐号登录或者su到root。

2、增加sudoers文件的写权限： chmod u+w /etc/sudoers

3、vim /etc/sudoers 找到 root ALL=(ALL) ALL 在这行下边添加 dituhui ALL=(ALL) ALL  (ps:dituhui代表是你要添加sudo权限的用户名)

4、除去sudoers文件的写权限： chmod u-w /etc/sudoers

### 终端翻墙
export http_proxy=http://127.0.0.1:1087;export https_proxy=http://127.0.0.1:1087;

### wordpress 更换网站
update wp_options set option_value='144.202.126.47' where option_name ='siteurl' or option_name='home';

### gollum 重定向操作
gollum > a.log 2>&1 &

### 生成 ssh key
ssh-keygen -t rsa -C "邮箱地址"
