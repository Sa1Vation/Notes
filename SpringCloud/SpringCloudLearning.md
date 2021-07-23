# Spring Cloud 学习笔记

## Consul by HashiCorp

- 一个服务网状解决方案，提供了服务发现、配置、分区的全功能平台。
- 每个功能都可以独立被使用
- Proxy?

### 使用Consul作为注册中心

### 使用Consul作为配置中心

## Spring Cloud Hystrix

- 服务容错保护
- 当某个服务发生故障时，通过断路器的监控，给予调用方返回一个错误响应，而不是长时间的等待
- 服务降级、服务熔断、线程隔离、请求缓存、请求合并、服务监控

### 启动Hystrix

#### @EnableCircuitBreaker

添加在启动类上开启Hystrix断路器功能

### 服务降级

#### @HystrixCommand

- 添加在Service层方法上做服务降级

- 参数：
  - fallbackMethod：指定服务降级的处理方法
  - ignoreExceptions：忽略某些异常，不发生降级
  - commandKey：命令名称，用于区分命令
  - groupKey：分组名称，用于统计命令的告警和仪表盘信息
  - threadPoolKey：线程池名称，用于划分线程池

### 请求缓存

#### @CacheResult

- 添加在Service层方法上做请求缓存
- 参数：
  - cacheKeyMethod

#### @CacheRemove

- 移除缓存
- 参数：
  - commandKey：使用缓存的方法名
  - cacheKeyMethod

#### @CacheKey

- 指定缓存的key，可以指定参数或指定参数中的属性值为缓存key，cacheKeyMethod还可以通过返回String类型的方法指定；

#### 缓存使用过程中的问题

- 在缓存使用过程中，我们需要在每次使用缓存的请求前后对HystrixRequestContext进行初始化和关闭，否则会出现如下异常：

### 请求合并

- 合并远程调用的请求，减少资源占用

#### @HystrixCollapser

- 添加在Service层方法上，合并多次请求
- 参数：
  - batchMethod：用于设置请求合并的方法
  - collapserProperties：请求合并属性
  - timerDelayInMilliseconds：控制多少时间合并一次请求

## Spring Cloud OpenFeign

- 基于Ribbon和Hystrix的声明式服务调用，拥有负载均衡和服务容错功能

## Spring Cloud Zuul

## Spring Cloud Gateway

## 分布式事务

### 2PC

### 3PC

### T

