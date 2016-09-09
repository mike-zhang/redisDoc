python客户端
-----------
Redis官方推荐的Python客户端是redis-py，
github地址： https://github.com/andymccurdy/redis-py

安装方式：

pip install redis

或者

easy_install redis

**使用方法**


1. 导入redis
::

    import redis
    
2. 连接到redis
::

    r = redis.StrictRedis() # 默认 127.0.0.1:6379
也可以显式指定需要连接的地址：
::

    r = redis.StrictRedis(host='127.0.0.1',port=6379,db=0)
    
3. 操作redis

以SET和GET命令为例：
::
    
    r.set('var','1') 
    print r.get('var')
    
    
异步方式redis客户端请参考asyncio_redis：
http://asyncio-redis.readthedocs.org/en/latest/    
    






