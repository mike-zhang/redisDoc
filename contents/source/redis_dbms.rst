redis数据库管理工具
===============


命令行管理工具
^^^^^^^^^^^^^

redis_cli是redis自带的命令行工具。
    
用法示例：
::

    root@debian8:redis-3.0.7# redis-cli
    127.0.0.1:6379> keys *
    (empty list or set)
    127.0.0.1:6379>
    

图形管理工具
^^^^^^^^^^^^^

redis desktop

https://redisdesktop.com/

需要关闭保护模式才可以连接成功。

redis 关闭保护模式：
::

    redis-server --protected-mode no


   

