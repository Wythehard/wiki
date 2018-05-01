###1. 错误日志输出

```markdown
php.ini 	display_error error_log error_reporting log_errors
日志文件可以手动创建防止权限不足
重启nginx
```

### 2. redis

```markdown
###配置redis保存session
extension=redis.so
session.save_handler = redis
session.save_path = "tcp://172.17.42.1:6379"
重启 gini
###redis连接
redis-cli -h172.17.42.1 -p6379
###查看所有key
keys *

```



####PHP加速

OPcache PHP 5.5 自带 opcode 缓存  但是 5.6  好像没有



firePHP:

composer require firephp/firephp-core



Closure 匿名函数的类

PHP的正则中，分隔符可以是## // {} 等



php.ini 执行任何文件先加载一下下面的文件。

auto_prepend_file = /data/gini-modules/girl/vendor/autoload.php


排错增强器
composer require firephp/firephp-core  同时需要去下载 firefox 的插件