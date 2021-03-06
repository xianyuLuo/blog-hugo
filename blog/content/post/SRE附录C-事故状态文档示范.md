---
title: SRE附录C~事故状态文档示范
tags:
  - sre
keywords:
  - sre
  - sre附录
  - 事故状态文档示范
  - 事故状态文档
description: "SRE事故状态文档示范模板"
abbrlink: 708220af
date: 2019-03-10T12:11:03+08:00
categories:
  - sre
---
# 莎士比亚搜索服务 新韵文+过载事故：2015-10-21
（沟通负责人会随时更新事故概要）

### 摘要
莎士比亚搜索服务由于新发现的韵文不在索引中而处于连锁故障状态

### 状态
活跃，事故编号 ##45

### 事故处理中心
IRC #shakespeare 频道

### 事故处理组织架构：（参与人）
+ 目前事故负责人：xxx
+ 运维负责人：
+ 计划负责人：
+ 沟通负责人：

+ 下一个事故总负责人：待定
（沟通负责人在交接班时或者每4小时更新一次）

### 细节状态
最终更新时间 2015-10-21 15:28 UTC，Jennifer

### 退出条件
+ 向莎士比亚搜索服务的Search 
+ Corpus中添加新的韵文（TODO）
+ 在30分钟内维持SLO，可用性为99.99%，延迟为99%<100ms（TODO）

### 代办列表以及提交的工单
+ 执行MapReduce任务，重新索引Shakespeare corpus（DONE）
+ 借用一些紧急资源来提高容量（DONE）
+ 启用 flux capacitor，在集群之间负载均衡（TODO）

### 事故时间线（倒叙排列，时区为UTC）
+ 2015-10-21 15:28 UTC jennifer

  ——全球服务容量提升为2倍

+ 2015-10-21 15:21 UTC jennifer

  ——将所有流量导向USA-2泄洪集群，同事将其他集群下线，以便让这些集群从连锁故障中恢复，同时启动更多任务

  ——MapReduce索引任务完成，等待Bigdata复制到所有集群

+ 2015-10-21 15:10 UTC martym

  ——向Shakespeare corpus中增加新的韵文，同时启动MapReduce任务

+ 2015-10-21 15:04 UTC martym

  ——从Shakespeare-discuss@ 邮件列表中获得了新发现的韵文全文

+ 2015-10-21 15:01 UTC docbrown
  
  ——由于出现连锁故障，声明目前进入紧急状态

+ 2015-10-21 14:55 UTC docbrown
  
  ——出现大量紧急报警，全部集群出现 ManyHttp500s
