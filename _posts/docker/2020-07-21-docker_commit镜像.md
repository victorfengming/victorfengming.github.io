---
title: "Docker之commit镜像"
tags: docker 
---



# commit镜像

```shell script
docker commit 提交容器成为一个新的副本
# 命令和git原理类似
docker commit -m="提交的描述信息" -a="作者" 容器id 目标镜像名:[TAG]

```
实战
```shell script
[root@iz8g9301trfnpxz ~]# docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS                    NAMES
48d9ea6fdb71        tomcat              "catalina.sh run"   4 minutes ago       Up 4 minutes        0.0.0.0:8080->8080/tcp   interesting_almeida
[root@iz8g9301trfnpxz ~]# docker commit -a="victor" -m"add webapps app" 48d9ea6fdb71 tomcat02:1.0
sha256:b17b415625d5ba90d1110824b0b3fe407d214945b2a20cefba3add4d060d027d
[root@iz8g9301trfnpxz ~]# docker images
REPOSITORY            TAG                 IMAGE ID            CREATED             SIZE
tomcat02              1.0                 b17b415625d5        7 seconds ago       657MB
tomcat                latest              9a9ad4f631f8        46 hours ago        647MB
portainer/portainer   latest              62771b0b9b09        8 days ago          79.1MB
nginx                 latest              8cf1bfb43ff5        8 days ago          132MB
redis                 latest              50541622f4f1        8 days ago          104MB
centos                latest              831691599b88        6 weeks ago         215MB
elasticsearch         7.6.2               f29a1ee41030        4 months ago        791MB
elasticsearch         latest              5acf0e8da90b        22 months ago       486MB
# 1. 启动一个默认的tomcat
# 2. 发现这个默认的tomcat是没有webapps应用,镜像的原因,官方的镜像默认webapps下面是没有文件的!
# 3. 我自己拷贝进去基本的文件
# 4. 将我们操作过的容器通过commit提交为一个镜像!我们以后就使用我们修改过的镜像即可,这就是我们自己的一个修改的镜像
```

学习方式说明:理解概念,但是一定要实践,最后实践与理论想结合一次搞定这个知识
```shell script
# 如果你想要保存当前容器的状态,就可以通过commit 提交,获得一个镜像
# 就好比我们以前学习vm时候,快照
```

到了这里才算是入门docker! 认真吸收练习

## 后面没讲的
- 容器数据卷 

- DockerFile

- Docker网络

- 企业实战

- Docker Compose

- Docker Swarm

- CI/CD Jenkins 流水线!!!