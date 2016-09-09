脚本支持
==========

Redis提供了通过eval命令来执行Lua 5.1脚本。

下面通过几个小例子来讲述如何在Redis服务端执行Lua脚本。

* redis-cli中直接执行lua脚本

::

    127.0.0.1:6379> eval "return redis.call('set','var','123')" 0
    OK
    127.0.0.1:6379> get var
    "123"
    127.0.0.1:6379>
    
* bash调用redis-cli执行
::

    ~$ redis-cli EVAL "return redis.call('set','var','456')" 0
    OK
    ~$ redis-cli GET var
    "456"
    ~$

如果lua脚本内容比较长，可以将lua脚本写入文件，
然后通过redis-cli执行：

::

    ~$ cat test1.lua
    local msg = "test1"
    print(msg)
    redis.call('set','var',msg)
    return msg
    ~$ redis-cli EVAL "$(cat test1.lua)" 0
    "test1"
    ~$ redis-cli get var
    "test1"
    
    



