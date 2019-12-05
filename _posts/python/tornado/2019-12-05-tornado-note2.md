---
title: "tornado笔记02"
subtitle: "高并发性能web框架"
tags: Python solution web tornado
---

## tornado的安装
这里我使用的是[虚拟环境](https://victorfengming.github.io/2019/11/18/python-venv/)中的[pip](https://victorfengming.github.io/2019/10/12/python-install-pip/)安装,配合[清华大学镜像源](https://victorfengming.github.io/2019/11/20/pip-conf/)安装的

```shell
pip install tornado -i https://pypi.tuna.tsinghua.edu.cn/simple
```

## 我的第一个tornado程序
```python
import tornado.web
import tornado.ioloop


class IndexHandler(tornado.web.RequestHandler):
    '''
    主页处理函数
    '''
    def get(self):
        self.write("hello tornado!")


if __name__ == '__main__':
    app = tornado.web.Application([(r"/",IndexHandler)])
    app.listen(8000)
    tornado.ioloop.IOLoop.current().start()

```

在tornado中,直接执行就行,不用加任何参数也OK

因为在里面已经帮你创建了一个服务器了