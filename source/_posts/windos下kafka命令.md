---
title: windos下kafka命令
date: 2017-05-24 14:24:18
tags: [kafka, code]
---


记录 kafka 相关命令
目录 %kafuka% = d:\kafka_2.11-0.10.0.1

<!-- more -->

# 开启服务  （%kafuka%下）
> .\bin\windows\kafka-server-start.bat .\config\server.properties

# 以下下在目录 %kafuka%\bin\windows\ 运行命令

## 创建topic
> kafka-topics.bat --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic topic名称

## 为topic增加partition
> kafka-topics.bat –zookeeper 127.0.0.1:2181 –alter –partitions 数量 –topic opic名称

## 删除topic
> kafka-run-class.bat  kafka.admin.DeleteTopicCommand --topic topic名称 --zookeeper 127.0.0.1:2181
> kafka-topics.bat  --zookeeper localhost:2181 --delete --topic topic名称

## 打开topic生产者
> kafka-console-producer.bat --broker-list localhost:9092 --topic topic名称

## 打开topic消费者
> kafka-console-consumer.bat --zookeeper localhost:2181 --topic topic名称

## 查看所有top
> kafka-topics.bat --list --zookeeper 127.0.0.1:2181

## 查看单个top信息
> kafka-topics.bat --zookeeper 127.0.0.1:2181  -describe -topic opic名称