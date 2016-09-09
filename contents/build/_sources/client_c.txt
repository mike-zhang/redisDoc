c客户端
-----------
Redis官方推荐的C客户端是hiredis，
github地址：https://github.com/redis/hiredis

同步API
^^^^^^^^^^^^^

* redisConnect
连接redis数据库（同步方式）
::

    redisContext *redisConnect(const char *ip, int port);
    
用法示例：
::

    redisContext *c = redisConnect("127.0.0.1", 6379);
    if (c == NULL || c->err) {
        if (c) {
            printf("Error: %s\n", c->errstr);
            // handle error
        } else {
            printf("Can't allocate redis context\n");
        }
    }    

* redisCommand
给redis发送命令
::
    
    void *redisCommand(redisContext *c, const char *format, ...);
    
用法示例：    
::

    reply = redisCommand(context, "SET foo bar");
    
    reply = redisCommand(context, "SET foo %s", value);
    
    reply = redisCommand(context, "SET foo %b", value, (size_t)valuelen);
    
    reply = redisCommand(context, "SET key:%s %s", myid, value);
    
* freeReplyObject
释放redis资源
::
    
    void freeReplyObject(void *reply);

其它api参考hiredis.h    
  
异步API
^^^^^^^^^^^^^^^^^^^^^^
* redisAsyncConnect 
连接redis数据库（异步方式）
::
    
    redisAsyncContext *redisAsyncConnect(const char *ip, int port);
    
示例代码：
::

    redisAsyncContext *c = redisAsyncConnect("127.0.0.1", 6379);
    if (c->err) {
        printf("Error: %s\n", c->errstr);
        // handle error
    }

* redisAsyncSetConnectCallback    
redis连接回调函数
::

    int redisAsyncSetConnectCallback(redisAsyncContext *ac, redisConnectCallback *fn);

示例代码：
::

    void connectCallback(const redisAsyncContext *c, int status) {
        if (status != REDIS_OK) {
            printf("Error: %s\n", c->errstr);           
            return;
        }

        printf("Connected...\n");
    }

    redisAsyncSetConnectCallback(c,connectCallback);

* redisAsyncSetDisconnectCallback
redis断开连接的回调函数
::
    
    int redisAsyncSetDisconnectCallback(redisAsyncContext *ac, redisDisconnectCallback *fn);
    
示例代码：
::

    void disconnectCallback(const redisAsyncContext *c, int status) {
        if (status != REDIS_OK) {
            printf("Error: %s\n", c->errstr);            
            return;
        }
        printf("Disconnected...\n");        
    }

    redisAsyncSetDisconnectCallback(c,disconnectCallback);    
* redisAsyncCommand
以异步方式给redis发送命令。
::
    
    int redisvAsyncCommand(redisAsyncContext *ac, redisCallbackFn *fn, void *privdata, const char *format, va_list ap);
    int redisAsyncCommand(redisAsyncContext *ac, redisCallbackFn *fn, void *privdata, const char *format, ...);
   
示例代码：
::

    void getCallback(redisAsyncContext *c, void *r, void *privdata) {
        redisReply *reply = r;
        if (reply == NULL) return;
        printf("argv[%s]: %s\n", (char*)privdata, reply->str);

        /* Disconnect after receiving the reply to GET */
        redisAsyncDisconnect(c);
    }

    redisAsyncCommand(c, NULL, NULL, "SET key %b", argv[argc-1], strlen(argv[argc-1]));
    redisAsyncCommand(c, getCallback, (char*)"end-1", "GET key");
        
* redisAsyncDisconnect
断开异步连接
::
    
    void redisAsyncDisconnect(redisAsyncContext *ac);
    

其它api参考async.h  




