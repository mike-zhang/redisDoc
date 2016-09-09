
有序集合类型
-----------
在集合类型的基础上有序集合类型为每个元素都关联了一个分数，这使我们可以使用集合类型的操作之外，还能做与分数有关的操作。

常用命令如下：

* ZADD 
增加一个带分数的元素，如果已存在，则替换分数
::

    ZADD key score member[ score member..]

* ZSCORE 
获得元素分数
::

    ZSCORE key member

* ZRANGE 
获得排名在某个范围内的元素，返回按score升序排序的元素
::
    
    ZRANGE key start end[ WITHSCORES]    

* ZREVRANGE 
与zrange使用一致，返回按score降序的元素
::

    ZREVRANGE key start end[ WITHSCORES]

* ZRANGEBYSCORE
获得指定分数范围内的元素
::
    
    ZRANGEBYSCORE key min max WITHSCORES

* ZREVRANGEBYSCORE 
获得指定分数范围内的元素,降序排序
::
    
    ZREVRANGEBYSCORE key max min WITHSCORES
    
* ZINCREBY 
增加某个元素的分数
::

    ZINCREBY key increment member
    
* ZCARD 
获取集合中元素个数
::
    
    ZCARD key
    
* ZCOUNT
获得指定分数范围内的元素个数
::
    
    ZCOUNT KEY min max

* ZREM 
删除一个或多个元素
::
    
    ZREM key member[ member..]
    
* ZRANK 
获取分数从小到大排序的位置
::
    
    ZRANK key member

    
其它sorted_set命令参考官方手册 :  http://redis.io/commands#sorted_set


