# SpringCloud

## SpringCloud相关面试题

### 什么是Spring Cloud？ 

Spring Cloud是一系列框架的有序集合。它利用Spring Boot的开发便利性巧妙地简化了分布式系统基础设施的开发，如服务发现注册、配置中心、智能路由、消息总线、负载均衡、断路器、数据监控等，都可以用Spring Boot的开发风格做到一键启动和部署。 Spring Cloud是将各家公司开发的成熟服务框架组合起来，通过Spring Boot风格进行再封装屏蔽掉了复杂的配置和实现原理，最终给开发者留出了一套简单易懂、易部署和易维护的分布式系统开发工具包。

**SpringCloud的优点**（利于开发）

1. 耦合度低。既能并行开发又能降低成本，可以不关注他人开发而先关注自己的开发，同时还不会影响其他模块的开发。
2. 配置简单，基本用注解就能实现，不用使用过多的配置文件。
3. 直接写后端的代码，不用关注前端怎么开发，直接写自己的后端代码即可，然后暴露接口，通过组件进行服务通信。

**SpringCloud的缺点**（运维比较麻烦）

1. 部署比较麻烦，给运维工程师带来一定的麻烦。
2. 针对系统数据的管理、系统的集成测试以及性能的监控都比较麻烦



###  springcloud中的组件有那些？

- Spring Cloud Eureka,**服务注册与发现**中心,特性有失效剔除、服务保护
- Spring Cloud Zuul,API**服务网关**,功能有路由分发和过滤
- Spring Cloud Config,**分布式配置中心**，支持本地仓库、SVN、Git、Jar包内配置等模式
- Spring Cloud Ribbon,**客户端负载均衡**,特性有区域亲和,重试机制
- Spring Cloud Hystrix,**客户端容错保护**,特性有服务降级、服务熔断、请求缓存、请求合并、依赖隔离
- Spring Cloud Feign,声明式**服务调用**本质上就是Ribbon+Hystrix
- Spring Cloud Stream,消息驱动,有Sink、Source、Processor三种通道,特性有订阅发布、消费组、消息分区
- Spring Cloud Bus,消息总线,配合Config仓库修改的一种Stream实现，
- Spring Cloud Sleuth,分布式服务追踪,需要搞清楚TraceID和SpanID以及抽样,如何与ELK整合



### springcloud Alibaba的常用组件

服务注册与发现：Nacos

服务配置中心：Spring Cloud Config / Nacos

服务网关：SpringCloud Gateway

服务调用：Spring Cloud Feign / Dubbo

服务负载均衡：Ribbon

服务容错保护：Sentinel

服务追踪：...



###  Nginx与Ribbon的区别？

两者都可以实现负载均衡。

Nginx是反向代理同时可以实现负载均衡，**nginx拦截客户端请求采用负载均衡策略**根据upstream配置进行转发，相当于请求**通过nginx服务器进行转发**。**Ribbon是客户端负载均衡**，从注册中心**读取目标服务器信息**，然后客户端采用**轮询策略对服务直接访问，全程在客户端操作**。