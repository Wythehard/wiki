mysql：

mysql的几个变量： show GLOBAL variables like ‘%log%’;
set GLOBAL  general_log=0;
包括：

innodb\_log\_buffer\_size：日志缓冲区大小

show variables like ‘innodb\_file\_per\_table’ 是否独立的表空间

set session tx_isolation='read-committed' 设置数据库事物隔离级别;
show variables like '%iso%';查看数据库事物隔离级别
丢失修改-读脏数据-不可重复读-幻觉出现
未提交读(READ UNCOMMITED) 脏读,两个事务之间互相可见；
已提交读(READ COMMITED)符合隔离性的基本概念,一个事务进行时，其它已提交的事物对于该事务是可见的，即可以获取其它事务提交的数据。
可重复读(REPEATABLE READ) InnoDB的默认隔离等级。事务进行时，其它所有事务对其不可见，即多次执行读，得到的结果是一样的！
可串行化（SERIALIZABLE） 在读取的每一行数据上都加锁，会造成大量的锁超时和锁征用，严格数据一致性且没有并发是可使用。

##innoDB 数据库特性
- 事务性数据库引擎 完全支持ACID特性   myISAM 是表锁
- 支持行锁 1.锁可以最大限度支持并发 2.锁能实现事务隔离

阻塞和死锁：
（1）阻塞是由于资源不足引起的排队等待现象。
（2）死锁是由于两个对象在拥有一份资源的情况下申请另一份资源，而另一份资源恰好又是这两对象正持有的，导致两对象无法完成操作，且所持资源无法释放。

确定MySQL的每个连接单独使用的内存
sort_buffer_size #定义了每个线程排序缓存区的大小，MySQL在有查询、需要做排序操作时才会为每个缓冲区分配内存（直接分配该参数的全部内存）；
join_buffer_size #定义了每个线程所使用的连接缓冲区的大小，如果一个查询关联了多张表，MySQL会为每张表分配一个连接缓冲，导致一个查询产生了多个连接缓冲；
read_buffer_size #定义了当对一张MyISAM进行全表扫描时所分配读缓冲池大小，MySQL有查询需要时会为其分配内存，其必须是4k的倍数；
read_rnd_buffer_size #索引缓冲区大小，MySQL有查询需要时会为其分配内存，只会分配需要的大小。


#数据库索引
###3.2.1 为什么要使用索引
  1、索引大大减少了存储引擎需要扫描的数据量；
  
  2、索引可以帮助我们进行排序以避免使用临时表；
  
  3、索引可以把随机I/O变为顺序I/O。
  
3.2.2 索引不是越多越好
  1、索引会增加写操作的成本；
  
  2、太多的索引会增加查询优化器的选择时间。
索引就好比一本书的目录，它会让你更快的找到内容，显然目录（索引）并不是越多越好，假如这本书1000页，而有500页是目录，它当然效率低，目录是要占纸张的,而索引是要占磁盘空间的。


mysql 主从配置 http://www.cnblogs.com/zhaobingqing/p/7077269.html
redis 集群配置 http://www.cnblogs.com/zhaobingqing/p/7514616.html
nginx 反向代理配置 http://www.cnblogs.com/zhaobingqing/p/7488660.html
mysql 慢查询日志 http://www.cnblogs.com/zhaobingqing/p/7074527.html
**mysql 索引优化** http://www.cnblogs.com/zhaobingqing/p/7071331.html
mysql 索引介绍 http://www.cnblogs.com/zhaobingqing/p/7066112.html
mysql索引 B+树 http://www.cnblogs.com/zhoujinyi/p/5731861.html

数据库索引
http://blog.codinglabs.org/articles/theory-of-mysql-index.html

order by 和 group by 可能会生成临时表，降低速度，加大IO，与数据库配置也有关系。

SQL 调优
一、如何分析

　　1、观察、至少跑1天，看看生产的慢SQL情况。

　　2、开启慢查询日志，设置阙值比如超过5秒钟的就是慢SQL，并将它抓取出来。

　　3、explain + 慢SQL分析

　　4、show profile

　　5、运维经理OR DBA，进行SQL数据库服务器参数调优。


