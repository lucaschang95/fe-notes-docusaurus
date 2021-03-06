# 压力测试

这里我们有几个工具, 分别给大家提供一些文档, 大家可以按需要选取.

## apache bench

apache bench: 这是一个简易的压测工具. 上手简单, 可以使用 csv 数据文件. 但不能检查响应数据. 测试报告相对简单. 如果想快速验证可以使用一下.

- 官网: http://httpd.apache.org/docs/2.0/programs/ab.html

## jMeter

jMeter 一个基于 Java 有可视化配置页面的压测工具. 功能丰富, 可以进行循环/使用csv数据/结果检查等. 可以在自己的电脑上直接使用, 上手比较简单.

官网: https://jmeter.apache.org/

## 如何进行压力测试

一般地, 我们遵守以下几条原则:

- 不影正常用户体验
  - 压测时系统正常为用户提供服务
  - 压测数据链路不影响正常用户
- 模拟压力最好与正常流量压力一致
  - 模拟 QPS >= 正常 QPS
  - 功能完备: 增删改查都要覆盖

对一个单一接口/模块进行压测是比较容易做到的. 但是想要真正地回归整个系统的稳定性, 就需要进行全链路压测.

全链路压测是基于实际的生产业务场景、系统环境，模拟海量的用户请求和数据对整个业务链进行压力测试，并持续调优的过程。