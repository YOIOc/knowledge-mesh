## 1.Spring Cloud的5大组件
1. [注册中心](Nacos.md#1.2实现注册中心)+[配置中心](Nacos.md#2.2实现配置中心)：[Nacos](Nacos.md)
2. 负载均衡：Ribbon
3. 远程调用：OpenFeign
4. 服务熔断：Sentinel
5. 网关：Gateway
## 2.Spring Cloud如何实现服务注册和发现
微服务架构中可采用[Nacos](Nacos.md)作为 [注册中心](Nacos.md#1.2实现注册中心)
- [服务注册](Nacos.md#^ee6b8e)：服务提供者将自己的服务名称、Ip、Port等信息注册到Nacos
- [服务发现](Nacos.md#^621019)：消费者向Nacos订阅并获取所需服务的Ip、Port，通过负载均衡算法，远程调用所需服务
- [服务监控](Nacos.md#^f7fd73)：服务提供者每隔5s向Nacos发送心跳，如果Nacos服务在固定时间窗口内没有接收到心跳，就会将该服务从Nacos中剔除（非临时示例不会被剔除）
## 3.Nacos与Eureka的区别
- [Nacos](Nacos.md)与Eureka的共同点（[注册中心](Nacos.md#1.2实现注册中心)）
   1. 都支持[服务注册和服务拉取](Nacos.md#1.1注册中心原理)
   2. 都支持心跳方式对服务提供者做健康检测
- Nacos与Eureka的区别
   1. Nacos支持服务端主动检测提供者状态：[临时示例](Nacos.md#^882c40)采用心跳模式，[非临时示例](Nacos.md#^66b2e9)采用主动检测模式
   2. 临时示例心跳不正常会被剔除，非临时示例则不会被剔除
   3. Nacos中的服务信息发生变更时，会主动向消费者推动变更消息，服务列表更新更及时
   4. Nacos集群默认采用AP方式，当集群中存在非临时示例时，采用CP模式；Eureka采用AP方式
   5. Nacos支持配置中心
## 4.负载均衡是如何实现的