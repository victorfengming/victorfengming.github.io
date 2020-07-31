---
title: "Run的流程和Docker原理"
tags: docker 
---





# docker是怎么工作的
Docker 是一个Client - Server 结构的系统,Docker的守护进行运行在主机上.通过Socket从客户端访问!

DockerServer 接收到Docker-Client的指令,就会执行这个命令!

## Docker为什么比VM块

1. docker 有着比虚拟机更少的抽象层
2. docker 利用的是宿主机的内核vm需要时GuestOS.

所以说,新建一个容器的时候,docker不需要像虚拟机一样重新加载一个操作系统内核,避免引导.

虚拟机是加载GuestOS,分钟级别的,而docker是利用宿主机的操作系统吗,省略了这个复杂的过程,秒级别

之后学习完毕所有的命令,再回过头来看这段理论就会很清晰!
理论 实践
