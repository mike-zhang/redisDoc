字符串类型
-----------

字符串是redis最基础的数据类型，常用命令如下：

* SET
赋值操作
::

    SET key value 
    
示例：
::

    SET a 5 ==> OK

* GET
取值操作
::

    GET key

示例：
::

    GET a  ==> "5"
    
* INCR
递增操作，键不存在时创建并赋0，否则+1
::

    INCR key
示例：
::
    
    INCR a ==> 6
    
* DECR
递减操作
::
    
    DECR key
示例：
::
    
    DECR a ==> 5
    
* INCRBY 
与incr一样，不过可以指定增加的数值
::

    INCRBY key num
示例：
::
    
    INCRBY a 10   ==>  15

* APPEND
追加,返回追加后字符串长度
::

    APPEND key value
示例：
::

    APPEND a 6  ==>  156

* STRLEN
获取字符串长度
::

    STRLEN key
示例：
::
    
    STRLEN a  ==> 3
   
* MSET 
同时设置多个键值
::

    MSET key value[key2 value2 ...]
    
示例：

    MSET key1 1 key2 2 ==> OK
    
* MGET
同时获取多个键值
::
    
    MGET key1 key2 => 
    1) "1"
    2) "2"

其它string命令参考官方手册 ： http://redis.io/commands#string
