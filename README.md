# spring-boot-rocketmq

## 1 启动 nameServer
脚本：`sh mqnamesrv`

```bash
nohup ./bin/mqnamesrv&
tail -f ~/logs/rocketmqlogs/namesrv.log
```

## 2 启动 broker
脚本：`sh mqbroker -n localhost:9876 autoCreateTopicEnable=true`

```bash
nohup ./bin/mqbroker -n localhost:9876 &
tail -f ~/logs/rocketmqlogs/broker.log
```

## 3 环境变量
export NAMESRV_ADDR=localhost:9876

## 4 启动console
打包：`mvn clean package -Dmaven.test.skip=true`
运行：
```bash
java -jar spring-boot-rocketmq-console-2.0.0.jar --server.port=10086 --rocketmq.config.namesrvAddr=localhost:9876
#java -jar -Drocketmq.config.namesrvAddr=localhost:9876 -Drocketmq.config.isVIPChannel=false rspring-boot-rocketmq-console-2.0.0.jar --server.port=12581
```

[参考](http://rocketmq.apache.org/docs/quick-start/)
[参考](https://www.bilibili.com/video/BV124411b7Xm)