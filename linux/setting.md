#linux 服务器基础设置
http://www.ruanyifeng.com/blog/2014/03/server_setup.html

#更改 apt-get 源
sudo vi /etc/apt/sources.list 即可 修改之前可以先备份。
每个版本的linux源地址不一样，可以去阿里源上找
```
deb-src http://archive.ubuntu.com/ubuntu xenial main restricted #Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main restricted multiverse universe #Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted multiverse universe #Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates universe
deb http://mirrors.aliyun.com/ubuntu/ xenial multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse #Added by software-properties
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner
deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted multiverse universe #Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial-security universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-security multiverse
```
#设置 zsh 为默认shell
sudo chsh -s $(which zsh)设置zsh为默认shell


linux修改时区
TZ='Asia/Shanghai'; export TZ


mount -o remount,rw /dev/sda1 /
flkid

#docker 
 sudo apt-get install docker-ce
 sudo usermod -aG docker www

#linux 给用户加sudo权限
1、用root帐号登录或者su到root。

2、增加sudoers文件的写权限： chmod u+w /etc/sudoers

3、vim /etc/sudoers 找到 root ALL=(ALL) ALL 在这行下边添加 dituhui ALL=(ALL) ALL  (ps:dituhui代表是你要添加sudo权限的用户名)

4、除去sudoers文件的写权限： chmod u-w /etc/sudoers
