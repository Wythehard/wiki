### lnmp安装

<https://lnmp.org/download.html>
```
### 下载，后边的路径直接粘贴就好。XShell上面复制快捷键是ctrl+insert，粘贴快捷键是Shift+insert，mac上面是我们熟悉的 command+c，command+v
wget http://soft.vpser.net/lnmp/lnmp1.4beta.tar.gz
### 解压
tar -zxvf lnmp1.4beta.tar.gz
###  进入lnmp目录
cd lnmp1.4
### 执行install.sh进行安装
./install.sh
```
### 一些配置信息
数据库密码 root
Database Directory: /usr/local/mariadb/var
Default Website Directory: /home/wwwroot/default

### 下载wordpress
wget https://cn.wordpress.org/wordpress-4.9.1-zh_CN.tar.gz

### 修改用户主目录
usermod -d dir username or -u uid

### 拷贝ssh公钥
ssh-copy-id www@xxxxxx

### 修改 zsh 主题
bira 非root用户想使用 oh-my-zsh 需要将root下的.oh-my-zsh/templates/zshrc.zsh-template文件复制到~/.zshrc 还有oh-my-zsh整个文件夹

### 安装docker
sudo usermod -aG $USER 添加当前用户到 docker 组

### 增加www到sudo权限中
chmod u+w /etc/sudoers
root    ALL=(ALL)       ALL
xiaofei ALL=(ALL)       ALL           
chmod u-w /etc/sudoers 不去除写权限会不让执行
### docker 安装
curl -fsSL https://get.docker.com/ | sh -s -- --mirror Aliyun

### nginx reload
/usr/nginx/sbin/nginx -s reload
### 检查远程端口是否打开
```
检测远程端口是否打开
 
常用telnet 110.101.101.101 80方式测试远程主机端口是否打开。
 
除此之外还可以使用：
 
方法1.nmap ip -p port 测试端口
 
nmap ip 显示全部打开的端口
 
根据显示close/open确定端口是否打开。
 
方法2. nc -v host port
 
端口未打开返回状态为非0

```

### mac中安装telnet
brew install inetutils

### 修改防火钱
sudo firewall-cmd --permanent --add-port=3690/tcp 
http://wangchujiang.com/linux-command/c/firewall-cmd.html

### php.ini
/usr/local/php/etc/php.ini

### 创建一个mysql docker
https://yq.aliyun.com/articles/138343
docker run -v /data/mysql/data:/var/lib/mysql -v /home/www/my.cnf:/etc/mysql/my.cnf  -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root --name mariadb -d mariadb:5.5.58
### 搭建一个私人网盘
http://geekplux.com/2016/10/25/how-to-setup-a-personal-cloud.html
### owncloud nginx配置文件
https://doc.owncloud.org/server/latest/admin_manual/installation/nginx_configuration.html
### 无视防火墙的docker
https://www.binss.me/blog/docker-pass-through-system-firewall/
### 解压缩
http://www.cnblogs.com/eoiioe/archive/2008/09/20/1294681.html
### 查看文件大小
ls -ahl
### 设置固定连接地址
http://www.bjhee.com/nginx-rewrite.html
location /wordpress/ {
    if (!-e $request_filename) {
        rewrite (.*) /wordpress/index.php;
    }
}


mysql config配置
/etc/my.cnf /etc/mysql/my.cnf ~/.my.cnf


### 添加虚拟内存

```
dd if=/dev/zero of=/swapfile count=1024 bs=1M
  mkswap /swapfile
  swapon /swapfile
  chmod 600 /swapfile
  [ -z "`grep swapfile /etc/fstab`" ] && echo '/swapfile    swap    swap    defaults    0 0' >> /etc/fstab
```

