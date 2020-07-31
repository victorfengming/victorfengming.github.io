---
title: "Docker之初始dockerfile"
tags: docker 
---




# 初始dockerfile
dockerfile 就是用来构建docker镜像的构建文件!命令脚本! 先体验一下!

```shell script
# 通过这脚本可以生成一个镜像,镜像是一层一层的,脚本是一个个命令,每个命令都是一层

```

```shell script
# 创建一个dockerfile文件,名字可以随机 建议dockerfile
# 文件中的内容指令(大写) 参数
FROM centos

VOLUME ["volume01","volume02"]

CMD echo "------end------"

CMD /bin/bash/
 
# 这里的每一个命令都是镜像的一层

```

试一下

```shell script
[root@iz8g9301trfnpxz docker-test-volume]# docker build -f /home/docker-test-volume/dockerfile1 -t kuangshen/centos:1.0 .
Sending build context to Docker daemon  2.048kB
Step 1/4 : FROM centos
 ---> 831691599b88
Step 2/4 : VOLUME ["volume01","volume02"]
 ---> Running in cfe1a7c20843
Removing intermediate container cfe1a7c20843
 ---> e0877f9a102a
Step 3/4 : CMD echo "------end------"
 ---> Running in 4ba75004d5d0
Removing intermediate container 4ba75004d5d0
 ---> 04b1dbef792a
Step 4/4 : CMD /bin/bash/
 ---> Running in 94b3954a4d3e
Removing intermediate container 94b3954a4d3e
 ---> 5c7e025fc4ff
Successfully built 5c7e025fc4ff
Successfully tagged kuangshen/centos:1.0
[root@iz8g9301trfnpxz docker-test-volume]# 

```
启动一下自己写的容器
```shell script
[root@iz8g9301trfnpxz docker-test-volume]# clear
[root@iz8g9301trfnpxz docker-test-volume]# docker images
REPOSITORY            TAG                 IMAGE ID            CREATED             SIZE
kuangshen/centos      1.0                 5c7e025fc4ff        5 minutes ago       215MB
tomcat02              1.0                 b17b415625d5        2 hours ago         657MB
tomcat                latest              9a9ad4f631f8        2 days ago          647MB
portainer/portainer   latest              62771b0b9b09        8 days ago          79.1MB
mysql                 5.7                 8679ced16d20        8 days ago          448MB
nginx                 latest              8cf1bfb43ff5        8 days ago          132MB
redis                 latest              50541622f4f1        9 days ago          104MB
centos                latest              831691599b88        6 weeks ago         215MB
elasticsearch         7.6.2               f29a1ee41030        4 months ago        791MB
elasticsearch         latest              5acf0e8da90b        22 months ago       486MB
[root@iz8g9301trfnpxz docker-test-volume]# docker run -it 5c7e025fc4ff /bin/bash
[root@1e52e32ab8e7 /]# ls
bin  dev  etc  home  lib  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var  volume01	volume02

```

上面的`volume01`和`volume02`就是我们自己挂载的,这个卷和外部一定是有一个同步的

```shell script
[root@iz8g9301trfnpxz home]# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                   NAMES
1e52e32ab8e7        5c7e025fc4ff        "/bin/bash"              2 minutes ago       Up 2 minutes                                goofy_feistel
33d87d73cf81        nginx               "/docker-entrypoint.…"   25 minutes ago      Up 25 minutes       0.0.0.0:32769->80/tcp   nginx03
8ec30de68329        nginx               "/docker-entrypoint.…"   28 minutes ago      Up 28 minutes       0.0.0.0:32768->80/tcp   nginx02
[root@iz8g9301trfnpxz home]# docker inspect 1e52e32ab8e7
[
    {
        "Id": "1e52e32ab8e7c00c87346c65bb75915dc4cfa557c03a78ae9cdb30fa2d6f125f",
        "Created": "2020-07-31T02:44:24.621394005Z",
        "Path": "/bin/bash",
        "Args": [],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 1318,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2020-07-31T02:44:24.951669958Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:5c7e025fc4ff374c40b48eba10fccfeb6c6e00fb5499837e76755f8d22927229",
        "ResolvConfPath": "/var/lib/docker/containers/1e52e32ab8e7c00c87346c65bb75915dc4cfa557c03a78ae9cdb30fa2d6f125f/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/1e52e32ab8e7c00c87346c65bb75915dc4cfa557c03a78ae9cdb30fa2d6f125f/hostname",
        "HostsPath": "/var/lib/docker/containers/1e52e32ab8e7c00c87346c65bb75915dc4cfa557c03a78ae9cdb30fa2d6f125f/hosts",
        "LogPath": "/var/lib/docker/containers/1e52e32ab8e7c00c87346c65bb75915dc4cfa557c03a78ae9cdb30fa2d6f125f/1e52e32ab8e7c00c87346c65bb75915dc4cfa557c03a78ae9cdb30fa2d6f125f-json.log",
        "Name": "/goofy_feistel",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "CapAdd": null,
            "CapDrop": null,
            "Capabilities": null,
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "ConsoleSize": [
                0,
                0
            ],
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": null,
            "BlkioDeviceWriteBps": null,
            "BlkioDeviceReadIOps": null,
            "BlkioDeviceWriteIOps": null,
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "KernelMemory": 0,
            "KernelMemoryTCP": 0,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/b788b8fbe178271f742f242cd0cdced934cb5d4c004fe5fb6af6e7c03ac7a15c-init/diff:/var/lib/docker/overlay2/7be18956fd4a8679af67244a0bb9d19b4abc7e060c5712ce24bf3489c93ea32b/diff",
                "MergedDir": "/var/lib/docker/overlay2/b788b8fbe178271f742f242cd0cdced934cb5d4c004fe5fb6af6e7c03ac7a15c/merged",
                "UpperDir": "/var/lib/docker/overlay2/b788b8fbe178271f742f242cd0cdced934cb5d4c004fe5fb6af6e7c03ac7a15c/diff",
                "WorkDir": "/var/lib/docker/overlay2/b788b8fbe178271f742f242cd0cdced934cb5d4c004fe5fb6af6e7c03ac7a15c/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [
            {
                "Type": "volume",
                "Name": "e113c26dfe915b20080e5a9f7ae700713d4f443ca95b9e80d82d351ace6b88ca",
                "Source": "/var/lib/docker/volumes/e113c26dfe915b20080e5a9f7ae700713d4f443ca95b9e80d82d351ace6b88ca/_data",
                "Destination": "volume02",
                "Driver": "local",
                "Mode": "",
                "RW": true,
                "Propagation": ""
            },
            {
                "Type": "volume",
                "Name": "b78af0b69e7fdfa0c87d2247f895021f6772b52e0d57b0f6ac3bef66dfd58964",
                "Source": "/var/lib/docker/volumes/b78af0b69e7fdfa0c87d2247f895021f6772b52e0d57b0f6ac3bef66dfd58964/_data",
                "Destination": "volume01",
                "Driver": "local",
                "Mode": "",
                "RW": true,
                "Propagation": ""
            }
        ],
        "Config": {
            "Hostname": "1e52e32ab8e7",
            "Domainname": "",
            "User": "",
            "AttachStdin": true,
            "AttachStdout": true,
            "AttachStderr": true,
            "Tty": true,
            "OpenStdin": true,
            "StdinOnce": true,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/bin/bash"
            ],
            "Image": "5c7e025fc4ff",
            "Volumes": {
                "volume01": {},
                "volume02": {}
            },
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {
                "org.label-schema.build-date": "20200611",
                "org.label-schema.license": "GPLv2",
                "org.label-schema.name": "CentOS Base Image",
                "org.label-schema.schema-version": "1.0",
                "org.label-schema.vendor": "CentOS"
            }
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "20dbaff762c3e3f81ec4497c34edcf3ff34842bddabb3d0705d1c90551729f4d",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {},
            "SandboxKey": "/var/run/docker/netns/20dbaff762c3",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "ce3538bdbc3b50aad38552ea578a45fd4f1db6cbc2e567012efc8b2421433691",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.4",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:04",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "68c30b64280cd79fbbee1895f55c67d9febdb11a032fcbd4326319b1ea5c5075",
                    "EndpointID": "ce3538bdbc3b50aad38552ea578a45fd4f1db6cbc2e567012efc8b2421433691",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.4",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:04",
                    "DriverOpts": null
                }
            }
        }
    }
]

# 外部挂载信息
"Mounts": [
            {
                "Type": "volume",
                "Name": "e113c26dfe915b20080e5a9f7ae700713d4f443ca95b9e80d82d351ace6b88ca",
                "Source": "/var/lib/docker/volumes/e113c26dfe915b20080e5a9f7ae700713d4f443ca95b9e80d82d351ace6b88ca/_data",
                "Destination": "volume02",
                "Driver": "local",
                "Mode": "",
                "RW": true,
                "Propagation": ""
            },
            {
                "Type": "volume",
                "Name": "b78af0b69e7fdfa0c87d2247f895021f6772b52e0d57b0f6ac3bef66dfd58964",
                "Source": "/var/lib/docker/volumes/b78af0b69e7fdfa0c87d2247f895021f6772b52e0d57b0f6ac3bef66dfd58964/_data",
                "Destination": "volume01",
                "Driver": "local",
                "Mode": "",
                "RW": true,
                "Propagation": ""
            }
        ],

```
测试一下刚才的文件是否同步出去了
```shell script
[root@iz8g9301trfnpxz home]# cd /var/lib/docker/volumes/e113c26dfe915b20080e5a9f7ae700713d4f443ca95b9e80d82d351ace6b88ca/_data
[root@iz8g9301trfnpxz _data]# ls
[root@iz8g9301trfnpxz _data]# cd /var/lib/docker/volumes/b78af0b69e7fdfa0c87d2247f895021f6772b52e0d57b0f6ac3bef66dfd58964/_data
[root@iz8g9301trfnpxz _data]# ls
container.txt
[root@iz8g9301trfnpxz _data]# 


```
这种方式我们未来使用的十分多,因为我们通常会构建自己的镜像

假设构建镜像的时候没有挂载卷,要手动镜像挂载 -v 卷名:容器内路径!

容器间也可以数据共享

# 数据卷容器
比如我们两个mysql同步数据