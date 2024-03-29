# DNS (Domain Name System)

> 一个用于将域名(Domain Name)与IP地址进行映射的数据库

- 基于UDP报文
- 递归与迭代相结合的查询方式

## 域名

所有的域名形成了一个域名树, 根下面是顶级域名, 再往下是二级域名, 三级域名, 四级域名...

顶级域名

- 国家顶级域名: cn, us, uk

- 通用顶级域名: com, net, org, gov, int

二级域名

类别域名: ac, com, edu, gov, mil, net, org

三级域名

如: tju.edu.cn

## 域名服务器

- 根域名服务器
  -知道所有顶级域名服务器的域名和ip地址
- 顶级域名服务器
- 权限域名服务器
- 本地域名服务器

当一个主机发出DNS请求时, 这个查询请求报文就发送给本地域名服务器

本地的互联网提供商, 大学等, 都有可能拥有自己的一个本地域名服务器

## 域名解析过程

- 应用程序需要解析一个dns，交付给resolver进行查询
- 查询hosts文件
- 查询浏览器缓存
- 查询本地isp提供商的dns服务
- isp负责递归查询

**递归查询和迭代查询**

- 最开始都是由主机去查询本地域名服务器, 这个过程是 **递归查询**

- 本地域名服务器迭代的查询顶级域名服务器, 权限域名服务器, 这个过程

## Zone file

## SOA记录

start of authority

- 一个zone file只能有一个soa记录

## A 记录

A record stands for a Address Record

maps a domain name to the IP address (Version 4) of the computer hosting the domain.

### 使用 dig 获取相应的 A 记录

```shell
dig A api.dnsimple.com
```
