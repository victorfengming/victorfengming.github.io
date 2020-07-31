---
title: "Docker部署nginx"
tags: docker nginx
---



# 作业1:部署nginx
## docker 安装nginx

```shell script
# 1.搜索镜像 search 建议大家去docker hub上面去搜索
# 2.下载镜像 pull
```

试一下
```shell script
[root@iz8g9301trfnpxz home]# docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
6ec8c9369e08: Pull complete 
d3cb09a117e5: Pull complete 
7ef2f1459687: Pull complete 
e4d1bf8c9482: Pull complete 
795301d236d7: Pull complete 
Digest: sha256:0e188877aa60537d1a1c6484b8c3929cfe09988145327ee47e8e91ddf6f76f5c
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest


# -d 后台运行
# -name 起名字
# -p 宿主机端口对应的里面的端口  端口暴漏 映射
[root@iz8g9301trfnpxz home]# docker run -d --name nginx01 -p 3344:80 nginx
f9277b55c181bd12515f53953c82ac8514879a16da9e14968f35923dca5b0537
[root@iz8g9301trfnpxz home]# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                  NAMES
f9277b55c181        nginx               "/docker-entrypoint.…"   4 seconds ago       Up 3 seconds        0.0.0.0:3344->80/tcp   nginx01
[root@iz8g9301trfnpxz home]# curl
curl: try 'curl --help' or 'curl --manual' for more information
[root@iz8g9301trfnpxz home]# curl localhost:3344
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
[root@iz8g9301trfnpxz home]# 

```



端口暴漏的概念

思考问题: 我们每次改动nginx配置文件,都需要进入容器内部?十分麻烦,我要是可以在容器外部提供一个映射路径,达到在容器外部修改文件,容器内部就可以自动更改,那就NB了

# 作业2:使用docker来装一个tomcat