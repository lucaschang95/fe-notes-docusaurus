# IP

> 细腰结构

## 网络层功能

网络层功能: IP寻址, 选路, 封装打包, 分片

IPv4: 32位二进制数, 一共2^32个地址

> 地址分类

- A类地址:
0xxx, 特大网络的单播传输

- B类地址:
10xx, 中大型网络

- C类地址:
110x, 小型网络的多播传输

- D类地址:
1110, IP多播

- E类地址:
1111, 预留试验用

## ip地址分类

**ip地址分为: A类, B类, C类, D类, E类地址**



#### A类地址

**网络地址**: 1 - 8位

​	- 其中第一位为**`0`**

**主机地址**: 9 - 32位



#### B地址

- **网络地址**: 1 - 16位

​	- 其中前两位为**`10`**

- **主机地址**: 17 - 32位

#### C类地址

- **网络地址**: 1 - 24位

​	- 其中前三位为**`110`**

- **主机地址**: 25 - 32位

#### D类地址

**广播地址**



#### E类地址

**保留, 用作实验**

### CIDR

Classless Inter-Domain Routing

> 表示方法

- A.B.C.D/N

### 全0全1

网络号 + 主机号: 某个主机
网络号 + 主机号全0: 指定某个网络
网络号全0 + 主机号: 指定当前所属网络下的某个主机
网络号全0 + 主机号全0: 指定自己的默认IP地址
网络号 + 主机号全1: 指定某个网络下的所有主机
网络号全1 + 主机号全1: 所有主机

### 路由表 Routing Table

### NAT
network address tranlation

升级版 NAPT prot tranlation



### 如何传输IP报文
- 直接传输
- 本地间网络传输
    - 内部选路协议(RIP, OSPF)
- 公网间接传输
    - 外部选路协议(BGP)



### RIP内部选路协议

- Routing Information Protocal
- 特点
    - 基于跳数确定路由
    - 使用UDP协议向相邻路由器通知路由表



### OSPF

- Open Shortest Path First
- 直接使用IP协议传递路由信息



### MTU
- 分片主体: 源主机, 路由器
- 重组主机: 目的主机



ping command 就是利用ICMP来的
第一次TTL=1, 第二次TTL=2



### IGMP