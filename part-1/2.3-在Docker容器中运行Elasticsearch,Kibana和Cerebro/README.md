# 在Docker容器中运行Elasticsearch, Kibana和Cerebro
## 课程Demo
### 在 docker 中运行 Elasticsearch
进入 7.x-docker-2-es-instance目录

```
#启动
docker-compose up

#停止容器
docker-compose down

#停止容器并且移除数据
docker-compose down -v

#一些docker 命令
docker ps
docker stop Name/ContainerId
docker start Name/ContainerId

#删除单个容器
$docker rm Name/ID
-f, –force=false; -l, –link=false Remove the specified link and not the underlying container; -v, –volumes=false Remove the volumes associated to the container

#删除所有容器
$docker rm `docker ps -a -q`  
停止、启动、杀死、重启一个容器
$docker stop Name/ID  
$docker start Name/ID  
$docker kill Name/ID  
$docker restart name/ID

```
## 相关阅读
- 安装docker  https://www.docker.com/products/docker-desktop
- 安装 docker-compose https://docs.docker.com/compose/install/
- 如何创建自己的Docker Image - https://www.elastic.co/cn/blog/how-to-make-a-dockerfile-for-elasticsearch
- 如何在为docker image安装 Elasticsearch 插件 - https://www.elastic.co/cn/blog/elasticsearch-docker-plugin-management
- 如何设置 Docker 网络 - https://www.elastic.co/cn/blog/docker-networking
- Cerebro 源码 https://github.com/lmenezes/cerebro
- 一个开源的 ELK（Elasticsearch + Logstash + Kibana） docker-compose 配置 https://github.com/deviantony/docker-elk
- Install Elasticsearch with Docker https://www.elastic.co/guide/en/elasticsearch/reference/7.2/docker.html


注意： es集群起不来。报错如下：
es7_01 | "stacktrace": ["org.elasticsearch.discovery.MasterNotDiscoveredException: null",
es7_01 | "at org.elasticsearch.action.support.master.TransportMasterNodeAction$AsyncSingleAction$4.onTimeout(TransportMasterNodeAction.java:259) [elasticsearch-7.1.0.jar:7.1.0]",
es7_01 | "at org.elasticsearch.cluster.ClusterStateObserver$ContextPreservingListener.onTimeout(ClusterStateObserver.java:322) [elasticsearch-7.1.0.jar:7.1.0]",
es7_01 | "at org.elasticsearch.cluster.ClusterStateObserver$ObserverClusterStateListener.onTimeout(ClusterStateObserver.java:249) [elasticsearch-7.1.0.jar:7.1.0]",
es7_01 | "at org.elasticsearch.cluster.service.ClusterApplierService$NotifyTimeout.run(ClusterApplierService.java:555) [elasticsearch-7.1.0.jar:7.1.0]",
es7_01 | "at org.elasticsearch.common.util.concurrent.ThreadContext$ContextPreservingRunnable.run(ThreadContext.java:681) [elasticsearch-7.1.0.jar:7.1.0]",
es7_01 | "at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128) [?:?]",
es7_01 | "at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628) [?:?]",
es7_01 | "at java.lang.Thread.run(Thread.java:835) [?:?]"] }
es7_01 | {"type": "server", "timestamp": "2019-07-03T08:44:36,151+0000", "level": "WARN", "component": "o.e.c.c.ClusterFormationFailureHelper", "cluster.name": "geektime", "node.name": "es7_01", "message": "master not discovered or elected yet, an election requires a node with id [-NtPuq1vRzGRi8CKL1st-A], have discovered [] which is not a quorum; discovery will continue using [] from hosts providers and [{es7_01}{Rl60TSJ3SUqhrb8hl0B0-Q}{8iiqMNQMSreXXgbyzWylfg}{172.19.0.3}{172.19.0.3:9300}{ml.machine_memory=2096164864, xpack.installed=true, ml.max_open_jobs=20}] from last-known cluster state; node term 2, last-accepted version 75 in term 2" }
展开
作者回复: docker-compose down -v
再重新docker-compose up
同时记得把docker的memory调大
