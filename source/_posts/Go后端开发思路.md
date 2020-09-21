---
title: Go后端开发思路
date: 2020-09-21 22:44:41
tags:
- Go
- 2020
---
![1584718662-2385a1d3902a9e494c62a900e2313305.png](https://i.loli.net/2020/09/17/KIZcWvMj4ApdJnG.png)
简洁 优雅 性能强劲 less is more
<!-- more-->
## 效率为王
go在多线程的方面上有着无与伦比的吸引力，相比于其他的语言，go的并发编程十分简单高效。只需要简单的几行代码就可以轻松完成。
```go
go func(){
  code
}()
```
不同于传统的多线程/进程，go使用一种叫做goroutine的协程来实现并发。简单往往意味着高效。goroutine非常轻量，这意味着，在一台机器上开启成千上万个goroutine而不会有很大的损耗，这使得go的高并发能力十分出众，凭借这点优势，go语言被广泛用在服务器编程，网络编程等方面，像是WEB应用，API应用......

## 站在巨人肩膀
go只有短短十年多的历史，但是在过去的几年间，go的流行程度却在不断的增长。
在过去的十年里，Go获得两次年度语言。
![TIM截图20200917213851.jpg](https://i.loli.net/2020/09/17/75FTQjtbLqsrA6f.jpg)

在最新的语言排名里，Go也名列前茅，快速上涨。
![TIM截图20200917213917.jpg](https://i.loli.net/2020/09/17/kgqGI8mQn9NB1dV.jpg)
Go在各大互联网企业中被广泛使用，像是google，Mozilla，CloudFlare，Bit.ly，Soundcloud......

也有很多用Go开发的成功项目docker，nsq，packer......

## 比hk记者还要快
在过去的两个月里，我都在使用go这门编程语言，公司之前的产品的后端是用Ruby写的，在几年的产品迭代中，逐渐面临一些瓶颈。于是决定转到Go。在后端组tony和shon老师的带领下，工作稳步推进中。

目前，后端形成了一套相对稳定的框架。

在web框架方面，使用的是[gin框架](https://github.com/gin-gonic/gin)，这是go目前最流行的web框架。方便灵活的中间件，超极速的[httprouter](https://github.com/julienschmidt/httprouter)以及强大的数据绑定。

gin的性能十分出色，下面是其benchmark

|Benchmark |name|	(1)|	(2)|	(3)|	(4)|
|---------|----|----|------|------|-------|
|BenchmarkGin_GithubAll	|43550|	27364| ns/op|	0 B/op|	0 allocs/op|
|BenchmarkAce_GithubAll|	40543|	29670| ns/op|	0 B/op|	0 allocs/op|
|BenchmarkAero_GithubAll|	57632|	20648| ns/op|	0 B/op|	0 allocs/op|
|BenchmarkBear_GithubAll|	9234|	216179| ns/op	|86448 B/op|	943 allocs/op|
|BenchmarkBeego_GithubAll	|7407	|243496 |ns/op|	71456 B/op|	609 allocs/op|
|BenchmarkBone_GithubAll|	420	|2922835| ns/op	|720160 B/op|	8620 allocs/op|
|BenchmarkChi_GithubAll	|7620|	238331 |ns/op|	87696 B/op|	609 allocs/op|
|BenchmarkDenco_GithubAll	|18355|	64494| ns/op|	20224 B/op|	167 allocs/op|

[完整结果](https://github.com/gin-gonic/gin/blob/master/BENCHMARKS.md)

数据库方面是用的是开源的[postgres数据库](https://www.postgresql.org/)，postgres稳定性极强，同时在高并发，高负载的情况下其性能指标都能维持双曲线甚至对数曲线，到顶峰之后不再下降。同时其支持的数据也十分丰富，满足各种需求。
操作数据库使用的是[gorm框架](https://github.com/go-gorm/gorm)，简化操作流程，配合postgres和gin来实现RESTful API 服务

中间件验证使用的jwt（JSON Web Token），这是一种简单而又有效的身份验证，能够快速安全的验证身份，从而确保安全性，同时jwt还能够保存使用者信息在其中，避免额外的数据库开销。token这些热数据保存在内存型数据库redis里从而提升其性能。

在一系列最优的选择下，迁移过后的后端性能得到了极大的提升，除此之外最为显著的改变是稳定性的极大提升，崩溃，错误都变少了，程序员的头发又回来了。
