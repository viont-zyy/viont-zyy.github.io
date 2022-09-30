# Redis

## Redis相关面试题

### Redis是什么，为什么使用 Redis？

Redis 是内存中的数据结构存储系统，它可以用作数据库、缓存和消息中间件，支持存储的 包括string(字符串)、list(链表)、set(集合)、zset(sorted set --有序集合)和hash（哈希类型）五种基本数据类型以及bitmap等高级的数据类型。 

 在日常的 Web 应用对数据库的访问中，**读操作的次数远超写操作**， 当我们使用 SQL 语句去数据库进行读写操作时，数据库就会 **去磁盘把对应的数据索引取回来**，这是一个相对较慢的过程。  如果我们把数据放在 Redis 中，也就是直接放在内存之中，让服务端直接去读取内存中的数据，那么这样速度明显就会快上不少 *(高性能)*，并且会 **极大减小数据库的压力** *(特别是在高并发情况下)*。 



### Redis 都支持哪些数据类型？这些数据类型的常用指令？

Redis 不是简单的键值存储，它实际上是一个数据结构服务器，支持不同类型的值。

- String（字符串）：二进制安全字符串
- List（列表）：根据插入顺序排序的字符串元素的集合。它们基本上是链表
- Hash（字典）：是一个键值对集合。KV模式不变，但V是一个键值对
- Set（集合）：唯一，未排序的字符串元素的集合
- zset(sorted set：有序集合)：相当于有序的 Set集合，每个字符串元素都与一个称为 *score* 的浮点值相关联。元素总是按它们的分数排序（eg，找出前10名或后10名）

常用指令：

String： SET、GET、MSET、MGET、INCR、DECR

List：LPUSH、RPUSH、LRANGE、LINDEX

Hash：HSET、HMSET、HSETNX、HKEYS、HVALS

Set：SADD、SCARD、SDIFF、SREM

SortSet：ZADD、ZCARD、ZCOUNT、ZRANGE

### 未完待续