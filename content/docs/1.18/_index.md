---
title: 介绍
weight: 1
children:
  - title: 特性
    url: features
---

欢迎来到 Jaeger 的文档门户！
下面，你会发现对于初学者和有经验的 Jaeger 用户信息.

如果你不能找到你在找什么, 或在这里没有覆盖的问题, 我们很乐意听取您的意见不管是在[Gitter chat](https://gitter.im/jaegertracing/Lobby), 我们的[邮件列表](https://groups.google.com/forum/#!forum/jaeger-tracing) 要么 [Github](https://github.com/jaegertracing/jaeger/issues).

## 关于

Jaeger, 灵感[Dapper][dapper] 和 [OpenZipkin](http://zipkin.io),
是一个分布式追踪系统 发布为开放源代码 通过 [Uber 技术][ubeross].
它用于监控和故障排除微服务为基础的分布式系统, 包含:

- 分布式环境传播
- 分布式事务监控
- 根本原因分析
- 服务依赖性分析
- 性能/延迟优化

Uber 发表博客文章, [在`Uber`不断发展分布式跟踪](https://eng.uber.com/distributed-tracing/), 他们解释为建筑选择的历史原因 在制作 `Jaeger`. [Yuri Shkuro](https://shkuro.com), Jaeger`的`创造者, 还出版了一本书[掌握分布式跟踪](https://shkuro.com/books/2019-mastering-distributed-tracing/) 在深入`Jaeger`设计和操作的许多方面覆盖, 以及分布在一般的跟踪.

## 特征

- [OpenTracing](http://opentracing.io/) 兼容的数据模型和仪器库
  - 在 [Go](https://github.com/jaegertracing/jaeger-client-go), [Java](https://github.com/jaegertracing/jaeger-client-java), [Node](https://github.com/jaegertracing/jaeger-client-node), [Python](https://github.com/jaegertracing/jaeger-client-python),
    [C++](https://github.com/jaegertracing/cpp-client) 和 [C#](https://github.com/jaegertracing/jaeger-client-csharp)
- 用途一致前期采样 同 每个服务/端点的概率个人
- 多个存储后端: Cassandra, Elasticsearch, memory.
- 自适应采样 (快来了)
- 后采集的数据处理管道 (快来了)

有关详细信息，请参见[特点](./features/)页。

## 技术规格

- 在`Go`实现后端组件
- React/Javascript UI
- 支持的存储后端:
  - [Cassandra 3.4+](./deployment/#cassandra)
  - [Elasticsearch 5.x, 6.x, 7.x](./deployment/#elasticsearch)
  - [Kafka](./deployment/#kafka)
  - 存储器

## 快速开始

参见[运行`docker`都在同一个镜像](getting-started#all-in-one).

## 截图

### 痕迹查看

[![Traces View](/img/traces-ss.png)](/img/traces-ss.png)

### 跟踪详细查看

[![Detail View](/img/trace-detail-ss.png)](/img/trace-detail-ss.png)

## 相关链接

- [不断变化的分布式跟踪在`Uber`工程](https://eng.uber.com/distributed-tracing/)
- [掌握分布式跟踪](https://shkuro.com/books/2019-mastering-distributed-tracing/)
- [跟踪 HTTP 请求的等待时间在`Go` 与 OpenTracing](https://medium.com/opentracing/tracing-http-request-latency-in-go-with-opentracing-7cc1282a100a)
- [分布式跟踪 同 Jaeger & Prometheus 上 Kubernetes](https://blog.openshift.com/openshift-commons-briefing-82-distributed-tracing-with-jaeger-prometheus-on-kubernetes/)
- [运用 Jaeger 同 Istio](https://istio.io/docs/tasks/telemetry/distributed-tracing.html)
- [运用 Jaeger 同 Envoy](https://www.envoyproxy.io/docs/envoy/latest/start/sandboxes/jaeger_tracing.html)

[dapper]: https://research.google.com/pubs/pub36356.html
[ubeross]: http://uber.github.io
