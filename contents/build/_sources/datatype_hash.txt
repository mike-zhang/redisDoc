
散列类型
-----------
散列类型（hash）的键值也是一种字典结构，其存储了字段（field）和字段值的映射，
但字段值只能是字符串，不支持其他数据类型，也就是散列类型不能嵌套其他的数据类型。

*除了散列类型，Redis 的其他数据类型同样不支持数据类型嵌套。比如集合类型的每个元素都只能是字符串，不能是另一个集合或散列表等。*

散列类型适合存储对象：使用对象类别和 ID 构成键名，使用字段表示对象的属性，
而字段值则存储属性值。


常用命令如下：
* HSET
设置或修改字段值
::

    HSET key field value

* HGET
获取字段值
::

    HGET key field
    
* HMSET
同时设置多个字段
::

    HMSET key field value [field value ...]
        
* HMGET
同时获取多个字段值
::

    HMGET key field [field ...]

* HGETALL
获取键中所有字段和值
::

    HGETALL key
    
* HEXISTS    
判断字段是否存在，存在返回1，否则返回0（如果键不存在也返回0）
::

    HEXISTS key field
    
其它hashs命令参考官方手册 ： http://redis.io/commands#hash