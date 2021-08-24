# Storm-REST-API

官方文档

https://github.com/apache/storm/blob/master/docs/STORM-UI-REST-API.md

参考

https://blog.csdn.net/AbnerSunYH/article/details/55520511


Storm UI 提供的 REST API 获取集群数据，基本上 Storm UI 上的所有数据都可以获取到。
应该是 storm 0.9.6 版本后才开始支持，试过 storm 0.9.0.1 版本并没有支持该系列接口。



请求前缀：

http://\<ui-host>:\<ui-port>/api/v1/...



GET Operations

/api/v1/cluster/configuration     返回集群配置数据

/api/v1/cluster/summary                   返回集群简要信息，例如 nimbus 更新时间、supervisors 数量等

/api/v1/supervisor/summary            返回所有 supervisors 简要信息

/api/v1/topology/summary                 返回所有 Topology 简要信息

/api/v1/topology/:id                          返回 Topology id 的统计信息

/api/v1/topology/:id/component/:component   返回 Topology id 下 component 组件的统计信息



POST Operations

/api/v1/topology/:id/activate                              Activates a topology.

/api/v1/topology/:id/deactivate                          Deactivates a topology.

/api/v1/topology/:id/rebalance/:wait-time   Rebalances a topology.

/api/v1/topology/:id/kill/:wait-time               Kills a topology.



组件纬度字段说明：

completeLatency:Total latency for processing the message
  
processLatency:Average time of the bolt to ack a message after it was received

executeLatency:Average time to run the execute method of the bolt

capacity:This value indicates number of messages executed * average execute latency / time window
