
订阅发布模式
---------------------

实现思想很简单，Publisher调用redis的publish方法往特定的channel发送消息，Subscriber在初始化的时候要subscribe到该channel，一旦有消息就会立即接收。

订阅消息（redis-cli终端1）：
::
    
    SUBSCRIBE first second
    
发布消息（redis-cli终端2）：
::
    
    PUBLISH first 1
    PUBLISH second 2
    
其它命令参考： http://redis.io/commands#pubsub

更多关于pubsub的描述详见：http://redis.io/topics/pubsub
