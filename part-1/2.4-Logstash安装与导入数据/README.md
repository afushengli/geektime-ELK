# Logstash 安装与测试数据导入
## 课程Demo
安装Logstash，并且导入Movielens的测试数据集
- Small: 100,000 ratings and 3,600 tag applications applied to 9,000 movies by 600 users. Last updated 9/2018.
- movielens/ml-latest-small/movies.csv movie数据
- movielens/logstash.conf //logstash 7.x 配置文件，
- movielens/logstash6.conf  //logstash 6.x 配置文件

```
#下载与ES相同版本号的logstash，（7.1.0），并解压到相应目录
#修改movielens目录下的logstash.conf文件
#path修改为,你实际的movies.csv路径
input {
  file {
    path => "YOUR_FULL_PATH_OF_movies.csv"
    start_position => "beginning"
    sincedb_path => "/dev/null"
  }
}

#启动Elasticsearch实例，然后启动 logstash，并制定配置文件导入数据
sudo  bin/logstash -f /YOUR_PATH_of_logstash.conf

```

本次做的操作是，在本机 安装的  logstash 向docker容器中的elaticsearch 中导入的数据
## 相关阅读
- 下载最MovieLens最小测试数据集：https://grouplens.org/datasets/movielens/
- Logstash下载：https://www.elastic.co/cn/downloads/logstash
- Logstash参考文档：https://www.elastic.co/guide/en/logstash/current/index.html


作者回复: logstash也可以集成进docker，讲课为了保持简洁，所以没有涵盖logstash的配置。如果你有兴趣 可以参考github这个项目

https://github.com/deviantony/docker-elk
