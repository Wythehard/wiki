#PHP相关


#算法与数据结构

###BTree和B+tree

多路搜索树
https://www.jianshu.com/p/da59af78ec59 
###排序算法
快速排序
![快速排序](https://mmbiz.qpic.cn/mmbiz_jpg/mpEnHdrckpTcibfAo173PUFa4mQj8mXY7MbeQYBLWT4Jrr34PdeDLUj4p0VOY1BkMPZwhyrLktuTXGyjpvhiaKNg/640?wx_fmt=jpeg)

#计算机网络
###TCP/UDP区别
TCP
> TCP是一种面向连接的、可靠的、基于字节流的传输层通信协议
TCP面向连接，提供可靠地数据服务
TCP首部开销20字节
TCP逻辑通信信道是全双工的可靠信道
TCP连接只能是点到点的

UDP
> UDP是参考模型中一种无连接的传输层协议，提供面向事务的简单不可靠的信息传递服务
UDP无连接，不可靠
UDP首部开销8字节
UDP逻辑通信信道是不可靠信道
UDP没有拥塞机制，因此网络出现拥堵不会使源主机的发送效率降低
UDP支持一对一，多对一，多对多的交互通信

###三次握手，四次挥手
流程，原因 time_wait 2*MSL
计算机网络相关的知识
https://github.com/jawil/blog/issues/14
###从浏览器输入域名到展示页面都发生了什么
DNS域名解析:本地->DNS服务器
建立TCP连接：三次握手
发送HTTP请求：get post
服务器处理请求：cdn->负载均衡->web server->fastcgi-fpm
返回响应结果：
> 1XX 信息性状态码 接收的请求正在处理
2XX 成功状态码 请求正常处理完毕
3XX 重定向状态码 需要附加操作以完成请求
4XX 客户端错误状态码 服务器也无法处理的请求
5XX 服务器错误状态码 服务器请求处理出错

浏览器解析HTML
浏览器布局渲染 css js等 图片等

#设计模式
单例模式，工厂模式

#缓存相关：
###Redis和Memcached的区别
> Redis和Memcache都是将数据存放在内存中，都是内存数据库。但是Memcache还可以缓存其他东西，比如图片、视频
Redis不只支持简单的k/v类型的数据，同时还提供list、set、hash等数据结构的存储
虚拟内存，当物理内存用完时Redis可以将一些很久没有用到的value交换到磁盘
过期策略，memcache在set时就指定，例如 setkey1008即永不过期，redis可以通过expire设定，例如： expire name10
分布式，设定memcache集群，利用magent做一主多从；redis也可以做一主多从。
存储安全，memcache挂掉后，数据没了；redis可以定期保存在磁盘（持久化）
灾难恢复，memcache挂掉后数据不可恢复；redis数据丢失后可以通过aof恢复
redis支持数据的备份，即master-slave模式的数据备份
应用场景不同：redis除了可以做nosql数据库之外，还能做消息队列、数据堆栈和数据缓存等。memcache适合于缓存sql语句、数据集、用户临时性数据、延迟查询数据和session等

###Redis数据结构
> - String
字符串、数字、二进制（图片、音频），单最大不能超过512M。
- Hash
- List——列表
- Set——集合
- Sorted Set——有序集合



