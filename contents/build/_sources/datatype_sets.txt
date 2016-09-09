
集合类型
-----------
集合中的每个元素都不同，且没有顺序。

常用命令如下：

* SADD
增加一个或多个元素
::
    
    SADD key member[ member..]

* SREM
移除一个或多个元素
::

    SREM key member[ member..]
    
* SMEMBERS
获取集合中所有的元素
::
    
    SMEMBERS key

* SISMEMBER
判断元素是否存在集合中
::

    SISMEMBER key member

* SCARD
获取集合的元素个数
::
    
    SCARD key

* SRANDMEMBER
返回1个或count个随机元素
::
    
    SRANDMEMBER key[ count]

* SDIFF
集合差运算
::
    
    SDIFF key[ key..]

* SINTER
集合交集运算
::
        
    SINTER key[ key..]

* SUNION
集合并集运算
::
    
    SUNION key[ key..]

    
    
其它sets命令参考官方手册 :  http://redis.io/commands#set
    