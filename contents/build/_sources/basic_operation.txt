基本操作
-----------
这里字符串类型为例描述redis的基本操作命令，其它数据类型参考文档。

* SET
如果key不存在，该命令可以完成添加操作；如果key存在，该命令实现更新操作；
::
    
    SET key value

* GET
获取某个key所对应的值，格式如下:
:: 
    
    GET key
    
* DEL
删除操作，格式如下：
::

    DEL key
* KEYS
获取符合规律的键名列表，格式如下：
::
    
    KEYS pattern
    
pattern支持glob风格通配符格式，具体如下：
::
    
    ?       匹配一个字符
    *       匹配任意个（包括0个）字符
    []      匹配括号间的任一字符，可以使用"-"符号表示一个
            范围，如a[b-d]可以匹配"ab","ac"和"ad"
    \x      匹配字符x，用于转义符号。   

* EXISTS
用于判断一个键是否存在，格式：
::
    
    EXISTS key
    
   
* EXPIRE
设置key的超时时间TTL(Time To Live),生存时间到期后键会自动被删除，格式：
::

    EXPIRE key seconds
    
    

    
