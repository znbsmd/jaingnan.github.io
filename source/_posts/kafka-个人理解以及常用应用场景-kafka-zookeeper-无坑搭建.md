---
title: kafka 个人理解以及常用应用场景 & kafka zookeeper 无坑搭建
date: 2019-08-07 23:41:53
tags:
categories: Kafka zookeeper
---
# kafka 个人理解以及常用应用场景 & kafka zookeeper 无坑搭建
## 一. kafka zookeeper简介 & 应用场景

ApacheKafka是一个分布式流媒体平台。由Scala和Java编写，是一种高吞吐量的分布式发布订阅消息系统。由于负载能力高，存储容量大，通常被我们用在大规模的日志收集和处理上，以及处理消息系统，例如用户操作记录、推送、用户相关任务信息。

ZooKeeper是一种用于分布式应用程序的高性能协调服务。ZooKeeper背后的动机是减轻分布式应用程序从头开始实施协调服务的责任。ZooKeeper数据保存在内存中。

在Kafka的设计中，选择了使用Zookeeper来进行所有Broker的管理。

## 二. 搭建

### 环境依赖

>新版本要求JDK版本为**1.8**, 低版本无法运行。
<br>基础环境是 Ubuntu/Debian
<br>集群实现用三台虚拟机完成，ip为 10.20.1.153, 10.20.1.154, 10.20.1.155

 - jdk 1.8
 - zookeeper
 - scala
 - kafka 2.3.0

 
### JDK安装
 ```bash
 # 安装jdk的ppa源，因为默认的源可能没有1.8
sudo add-apt-repository ppa:openjdk-r/ppa
sudo apt-get update

 # 安装jdk1.8
apt-get install openjdk-8-jdk
 # 验证安装
java -version
 ```
### zookeeper 安装
```bash
# 安装zookeeper
sudo apt-get install zookeeper
```
或者 手动下载，下载地址为 http://mirror.bit.edu.cn/apache/zookeeper/zookeeper-3.4.14/zookeeper-3.4.14.tar.gz

```bash
# 重命名一个配置文件 
cp conf/zoo_sample.cfg conf/zoo.cfg
```
现在已创建配置文件，可以启动ZooKeeper：
```
bin/zkServer.sh start
```
### kafka 安装
去官网下载最新release版本，地址 [http://kafka.apache.org/downloads](http://kafka.apache.org/downloads)，或者直接wget获取

```bash
# 下载
wget http://apache.javapipe.com/kafka/1.0.0/kafka_2.12-1.0.0.tgz

# 解压
tar -zxvf kafka_2.12-1.0.0.tgz

cd kafka_2.12-1.0.0
```
**这里注意一下，下载完直接运行会出错，必须先下载Scala或者下载kafka二进制版本(二进制版本官方也可以下)**

### Scala安装

```bash
# 安装scala
apt-get install scala

# 验证安装
scala -version
> Scala code runner version 2.9.2 -- Copyright 2002-2011, LAMP/EPFL
```
### kafka 启动
```
bin/zookeeper-server-start.sh config/zookeeper.properties
```
### 创建主题
```
bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic test

```
### 发送消息

```
bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test
This is a message
This is another message

```
### 启动消费者

```
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning
This is a message
This is another message
```
至此，基本的搭建已经完成 可以配合编程语音做一些简单的日志处理服务。






