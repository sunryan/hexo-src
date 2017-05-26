---
title: Windows搭建Kafka环境
date: 2017-05-24 11:38:30
tags: kafka
---
# Windows上搭建Kafka运行环境

<!-- more -->

## 安装JDK
    
> 自行百度，这里不说了

## 安装Zookeeper


> Kafka的运行依赖于Zookeeper，所以在运行Kafka之前我们需要安装并运行Zookeeper

1. 下载安装文件： [http://zookeeper.apache.ord/releases.html](http://zookeeper.apache.ord/releases.html)
2. 解压文件（本文解压到 d:\zookeeper-3.4.8）
3. 打开d:\zookeeper-3.4.8\conf，把zoo_sample.cfd重命名成zoo.cfd
4. 从文本编辑器里打开zoo.cfd
5. 把dataDir的值改成“d:\zookeeper-3.4.8\data”
6. 添加如下系统变量：
7. ZOOKEEPER_HOME: d:\zookeeper-3.4.8
8. Path: 在现有的值后面添加 ";%ZOOKEEPER_HOME%\bin;"
9. 运行Zookeeper: 打开cmd然后执行


## 安装并运行Kafka

1. 下载安装文件： http://kafka.apache.ord/downloads.html
2. 解压文件（本文解压到 d:\kafka_2.11-0.10.0.1）
3. 打开d:\kafka_2.11-0.10.0.1\confid
4. 从文本编辑器里打开 server.properties
5. 把 lod.dirs的值改成 d:\kafka_2.11-0.10.0.1\kafka-logs
6. 打开cmd
7. 进入kafka文件目录: cd d:\kafka_2.11-0.10.0.1\
8. 输入并执行以打开kafka:

``` bash
.\bin\windows\kafka-server-start.bat .\config\server.properties
```
    
## 创建topics

创建一个topics test
``` bash
cd d:\kafka_2.11-0.10.0.1\bin\windows
kafka-topics.bat --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test
```

## 打开一个Producer

``` bash
cd d:\kafka_2.11-0.10.0.1\bin\windows
kafka-console-producer.bat --broker-list localhost:9092 --topic test
```

## 打开一个Consumer

``` bash
cd d:\kafka_2.11-0.10.0.1\bin\windows
kafka-console-consumer.bat --zookeeper localhost:2181 --topic test
```
    
> 然后就可以在Producer控制台窗口输入消息了。
> 在消息输入过后，很快Consumer窗口就会显示出Producer发送的消息。
