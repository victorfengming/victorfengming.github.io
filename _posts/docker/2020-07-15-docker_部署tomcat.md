---
title: "Docker部署tomcat"
tags: docker tomcat
---




# 作业2:使用docker来装一个tomcat

```shell script
# 官方的使用
docker run -it --rm tomcat:9.0
# 我们之前的启动都是后台,停止了容器之后,容器还是可以查到 
docker run -it --rm ,一般用于测试,用完即删除
# 先下载 在启动
docker pull tomcat:9.0
# 启动运行
docker run -d -p 3355:8080 --name tomcat01 tomcat
# 测试访问没有问题
root@f1421fbdf093:/usr/local/tomcat# ls
BUILDING.txt	 LICENSE  README.md	 RUNNING.txt  conf  logs	    temp     webapps.dist
CONTRIBUTING.md  NOTICE   RELEASE-NOTES  bin	      lib   native-jni-lib  webapps  work
root@f1421fbdf093:/usr/local/tomcat# cd webapps
root@f1421fbdf093:/usr/local/tomcat/webapps# l
# 进入容器
[root@iz8g9301trfnpxz home]# docker exec -it tomcat01 /bin/bash
# 发现问题:1,linux 命令少了,2.没有webapps .阿里云镜像的原因,他使用最小的
```

思考问题:我们每次进入容器十分麻烦,如果要是可以在容器外部提供一个映射路径,然后能够在我们的外部放置项目,就自动同步到内容就好了! 

docker 容器 tomcat

mysql放到docker 不科学

删掉容器就能够删库跑路了