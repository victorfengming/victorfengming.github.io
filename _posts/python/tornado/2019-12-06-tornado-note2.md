---
title: "tornado学习笔记day02"
subtitle: "小而精的python web框架"
tags: Python solution web tornado
---



* content
{:toc}





# tornado提升
整理基础工程

搭建一个框架的基础目录

```

D:.
│  config.py
│  readme.md
│  server.py
│  application.py
│  
├─.idea
│  │  .gitignore
│  │  itcast_tornado.iml
│  │  misc.xml
│  │  modules.xml
│  │  vcs.xml
│  │  workspace.xml
│  │
│  └─inspectionProfiles
│          profiles_settings.xml
│
├─static # 静态资源文件夹    
├─templates # 模板文件
├─upfile  # 上传文件
│
└─views # 视图
   │  index.py # 首页视图
   └─ __init__.py

```




### version1.0
创建一个`index.py`文件在`views`包下面,内容如下
```python
from tornado.web import RequestHandler


class IndexHandler(RequestHandler):
    def get(self):
        self.write("main page info tornado!")

```
在`server.py`文件中修改如下
```python
import tornado.web
import tornado.ioloop
import tornado.httpserver
import tornado.options
import config
from views.index import IndexHandler

if __name__ == '__main__':
    app = tornado.web.Application(
        [
            (r"/", IndexHandler)
        ]
    )
    httpServer = tornado.httpserver.HTTPServer(app)
    httpServer.bind(config.options["port"])
    httpServer.start(1)
    tornado.ioloop.IOLoop.current().start()

```
其中的`config.py`不用动
```python
options = {
    "port": 8080,
    "list": ["good", "nice", "handsome"]
}
```

### version2.0

创建一个`application.py`的文件,内容如下
```python
import tornado.web
from views.index import IndexHandler

class Application(tornado.web.Application):
    def __init__(self):
        handlers = [
            (r"/", IndexHandler)
        ]
        super(Application,self).__init__(handlers)
```

然后服务端这么改
```python
import tornado.ioloop
import tornado.httpserver
import tornado.options

import config
from application import Application


if __name__ == '__main__':
    app = Application()
    httpServer = tornado.httpserver.HTTPServer(app)
    httpServer.bind(config.options["port"])
    httpServer.start(1)
    tornado.ioloop.IOLoop.current().start()

```

视图都不用动
```python
from tornado.web import RequestHandler


class IndexHandler(RequestHandler):
    def get(self):
        self.write("main page info tornado!")
```

因为tornado不是Django那种大而全的,而是小而精的

所以配置也不用怎么动
```python
# 参数
options = {
    "port": 8080
}

# 配置
settings = {
    # static_path = "/",
    "debug" : True
}
```

成了这就

然后我们再配置一个路由`home`  
在application里面直接加就OK
```python
import tornado.web
from views import index

class Application(tornado.web.Application):
    def __init__(self):
        handlers = [
            (r"/", index.IndexHandler),
            (r"/home", index.HomeHandler),
        ]
        super(Application,self).__init__(handlers)
```
然后在视图中再创建一个对应的类
```python
from tornado.web import RequestHandler


class IndexHandler(RequestHandler):
    def get(self):
        self.write("main page info tornado!")

class HomeHandler(RequestHandler):
    def get(self):
        self.write(" this is home page content!")
```
重启服务即可在浏览器中访问/home看到结果
