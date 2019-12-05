---
title: "初识tornado"
subtitle: "python编写的web服务器兼web应用框架"
tags: Python solution web tornado
---

本文转自:https://www.jianshu.com/p/af6654deac4e


<div class="image-package">
    <div class="image-container" style="max-width: 700px; max-height: 545px; background-color: transparent;">
        <div class="image-container-fill" style="padding-bottom: 40.98%;"></div>
        <div class="image-view" data-width="1330" data-height="545"><img
                data-original-src="//upload-images.jianshu.io/upload_images/6078268-d18f863e1dfcb9d0.png"
                data-original-width="1330" data-original-height="545" data-original-format="image/png"
                data-original-filesize="344647" data-image-index="0" style="cursor: zoom-in;" class=""
                src="//upload-images.jianshu.io/upload_images/6078268-d18f863e1dfcb9d0.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp">
        </div>
    </div>
    <div class="image-caption">Tornado：Tornado web server</div>
</div>
<blockquote>
    <ul>
        <li><strong><a href="https://link.jianshu.com?t=http://www.tornadoweb.org/en/stable/" target="_blank"
                       rel="nofollow">官方文档</a></strong></li>
        <li><strong><a href="https://link.jianshu.com?t=http://tornado-zh.readthedocs.io/zh/latest/" target="_blank"
                       rel="nofollow">中文文档</a></strong></li>
        <li><strong><a href="https://link.jianshu.com?t=http://www.tornadoweb.cn/documentation" target="_blank"
                       rel="nofollow">Tornado概览</a></strong></li>
        <li><strong><a href="https://link.jianshu.com?t=https://zhuanlan.zhihu.com/p/25978330" target="_blank"
                       rel="nofollow">浅谈Python Web 框架：Django, Twisted, Tornado, Flask, Cyclone 和
            Pyramid</a></strong></li>
        <li><strong><a href="https://link.jianshu.com?t=http://demo.pythoner.com/itt2zh/index.html" target="_blank"
                       rel="nofollow">Tornado入门</a></strong></li>
    </ul>
</blockquote>
<h1>1.Tornado</h1>
<ul>
    <li>Tornado：python编写的web服务器兼web应用框架</li>
</ul>
<h3>1.Tornado的优势</h3>
<blockquote>
    <ul>
        <li>轻量级web框架</li>
        <li>异步非阻塞IO处理方式</li>
        <li>出色的抗负载能力</li>
        <li>优异的处理性能，不依赖多进程/多线程，一定程度上解决C10K问题</li>
        <li>WSGI全栈替代产品，推荐同时使用其web框架和HTTP服务器</li>
    </ul>
</blockquote>
<h3>2.Tornado VS Django</h3>
<ul>
    <li><strong>Django：重量级web框架，功能大而全，注重高效开发</strong></li>
</ul>
<blockquote>
    <ul>
        <li>内置管理后台</li>
        <li>内置封装完善的ORM操作</li>
        <li>session功能</li>
        <li>后台管理</li>
        <li>缺陷：高耦合</li>
    </ul>
</blockquote>
<ul>
    <li><strong>Tornado：轻量级web框架，功能少而精，注重性能优越</strong></li>
</ul>
<blockquote>
    <ul>
        <li>HTTP服务器</li>
        <li>异步编程</li>
        <li>WebSocket</li>
        <li>缺陷：入门门槛较高</li>
    </ul>
</blockquote>
<h1>2.安装</h1>
<p>输入命令：</p>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-undefined"><code class="  language-undefined">pip install tornado
<span aria-hidden="true" class="line-numbers-rows"><span></span></span></code></pre>
</div>
<p><strong>备注：</strong><br>
    Tornado应该运行在类Unix平台，为了达到最佳的性能和扩展性，仅推荐Linux和BSD(充分利用Linux的epoll工具和BSD的kqueue达到高性能处理的目的)</p>
<h1>3.使用</h1>
<h3>1.Tornado入门程序 - （一）</h3>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-python"><code class="  language-python"><span class="token comment">#-*- coding:utf-8 -*-</span>
<span class="token keyword">import</span> tornado<span class="token punctuation">.</span>web
<span class="token keyword">import</span> tornado<span class="token punctuation">.</span>ioloop


<span class="token comment">#定义处理类型</span>
<span class="token keyword">class</span> <span class="token class-name">IndexHandler</span><span
                class="token punctuation">(</span>tornado<span class="token punctuation">.</span>web<span
                class="token punctuation">.</span>RequestHandler<span class="token punctuation">)</span><span
                class="token punctuation">:</span>
    <span class="token comment">#添加一个处理get请求方式的方法</span>
    <span class="token keyword">def</span> <span class="token function">get</span><span
                class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                class="token punctuation">:</span>
        <span class="token comment">#向响应中，添加数据</span>
        self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                class="token string">'好看的皮囊千篇一律，有趣的灵魂万里挑一。'</span><span class="token punctuation">)</span>

<span class="token keyword">if</span> __name__ <span class="token operator">==</span> <span class="token string">'__main__'</span><span
                class="token punctuation">:</span>
    <span class="token comment">#创建一个应用对象</span>
    app <span class="token operator">=</span> tornado<span class="token punctuation">.</span>web<span
                class="token punctuation">.</span>Application<span class="token punctuation">(</span><span
                class="token punctuation">[</span><span class="token punctuation">(</span><span
                class="token string">r'/'</span><span class="token punctuation">,</span>IndexHandler<span
                class="token punctuation">)</span><span class="token punctuation">]</span><span
                class="token punctuation">)</span>
    <span class="token comment">#绑定一个监听端口</span>
    app<span class="token punctuation">.</span>listen<span class="token punctuation">(</span><span class="token number">8888</span><span
                class="token punctuation">)</span>
    <span class="token comment">#启动web程序，开始监听端口的连接</span>
    tornado<span class="token punctuation">.</span>ioloop<span class="token punctuation">.</span>IOLoop<span
                class="token punctuation">.</span>current<span class="token punctuation">(</span><span
                class="token punctuation">)</span><span class="token punctuation">.</span>start<span
                class="token punctuation">(</span><span class="token punctuation">)</span>
<span aria-hidden="true"
      class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre>
</div>
<blockquote>
    <p><strong>1 .</strong>在pycharm中直接运行代码<br>
        <strong>2 .</strong>如果是在ubuntu，在命令窗口输入</p>
    <div class="_2Uzcx_">
        <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy"
                                                                  class="anticon anticon-copy">
            <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
                 fill="currentColor" aria-hidden="true">
                <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
            </svg>
        </i></button>
        <pre class="line-numbers  language-css"><code class="  language-css">python 文件名.py
<span aria-hidden="true" class="line-numbers-rows"><span></span></span></code></pre>
    </div>
</blockquote>
<div class="image-package">
    <div class="image-container" style="max-width: 700px; max-height: 574px; background-color: transparent;">
        <div class="image-container-fill" style="padding-bottom: 66.44%;"></div>
        <div class="image-view" data-width="864" data-height="574"><img
                data-original-src="//upload-images.jianshu.io/upload_images/6078268-4c0139d5d13d7c89.png"
                data-original-width="864" data-original-height="574" data-original-format="image/png"
                data-original-filesize="27908" data-image-index="1" style="cursor: zoom-in;" class=""
                src="//upload-images.jianshu.io/upload_images/6078268-4c0139d5d13d7c89.png?imageMogr2/auto-orient/strip|imageView2/2/w/864/format/webp">
        </div>
    </div>
    <div class="image-caption">使用浏览器访问</div>
</div>
<h1>4.Tornado 代码解析</h1>
<h3>1.入门程序代码解析</h3>
<ul>
    <li>
        <p><strong>tornado.web：tornado的基础web框架</strong></p>
        <ul>
            <li>
                <strong><code>RequestHandler</code>：</strong>封装对请求处理的所有信息和处理方法
            </li>
            <li>
                <code>get/post/..</code>：封装对应的请求方式
            </li>
            <li>
                <code>write()</code>：封装响应信息，写响应信息的一个方法
            </li>
        </ul>
    </li>
    <li>
        <p><strong>tornado.ioloop：核心io循环模块，封装linux的epoll和BSD的kqueue， tornado高性能处理的核心。</strong></p>
        <ul>
            <li>
                <strong><code>current()</code></strong>返回当前线程的IOLoop实例对象
            </li>
            <li>
                <strong><code>start()</code></strong>启动IOLoop实力对象的IO循环，开启监听
            </li>
        </ul>
    </li>
</ul>
<hr>
<h3>2.httpserver底层处理</h3>
<ul>
    <li>
        <strong>httpserver监听端口</strong>
        <ul>
            <li><strong><code>tornado.httpserver.HTTPServer(app)</code></strong></li>
            <li><strong><code>httpserver.listen(port)</code></strong></li>
        </ul>
    </li>
</ul>
<ul>
    <li>
        <strong>httpserver实现多进程操作</strong>
        <ul>
            <li><strong><code>tornado.httpserver.HTTPServer(app)</code></strong></li>
            <li><strong><code>httpserver.bind(port)</code></strong></li>
            <li><strong><code>httpserver.start(0/None/&lt;0/num)</code></strong></li>
        </ul>
    </li>
</ul>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-python"><code class="  language-python"><span class="token comment"># -*- coding:utf-8 -*-</span>
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>web <span class="token keyword">import</span> Application<span
                class="token punctuation">,</span>RequestHandler
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>ioloop <span
                class="token keyword">import</span> IOLoop
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>httpserver <span
                class="token keyword">import</span> HTTPServer

<span class="token keyword">class</span> <span class="token class-name">IndexHandler</span><span
                class="token punctuation">(</span>RequestHandler<span class="token punctuation">)</span><span
                class="token punctuation">:</span>
    <span class="token keyword">def</span> <span class="token function">get</span><span
                class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                class="token punctuation">:</span>
        self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                class="token string">'给自己一点时间，理清所有的荒唐与期望。'</span><span class="token punctuation">)</span>

<span class="token keyword">if</span> __name__ <span class="token operator">==</span> <span class="token string">'__main__'</span><span
                class="token punctuation">:</span>
    app <span class="token operator">=</span> Application<span class="token punctuation">(</span><span
                class="token punctuation">[</span><span class="token punctuation">(</span><span
                class="token string">r'/'</span><span class="token punctuation">,</span>IndexHandler<span
                class="token punctuation">)</span><span class="token punctuation">]</span><span
                class="token punctuation">)</span>
    http_server <span class="token operator">=</span> HTTPServer<span class="token punctuation">(</span>app<span
                class="token punctuation">)</span>
    <span class="token comment">#最原始的方式</span>
    http_server<span class="token punctuation">.</span>bind<span class="token punctuation">(</span><span
                class="token number">8888</span><span class="token punctuation">)</span>
    http_server<span class="token punctuation">.</span>start<span class="token punctuation">(</span><span
                class="token number">0</span><span class="token punctuation">)</span>

    <span class="token comment">#启动Ioloop轮循监听</span>
    IOLoop<span class="token punctuation">.</span>current<span class="token punctuation">(</span><span
                class="token punctuation">)</span><span class="token punctuation">.</span>start<span
                class="token punctuation">(</span><span class="token punctuation">)</span>
<span aria-hidden="true"
      class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre>
</div>
<blockquote>
    <div class="image-package">
        <div class="image-container" style="max-width: 700px; max-height: 215px; background-color: transparent;">
            <div class="image-container-fill" style="padding-bottom: 24.86%;"></div>
            <div class="image-view" data-width="865" data-height="215"><img
                    data-original-src="//upload-images.jianshu.io/upload_images/6078268-705d0ceb55c30592.png"
                    data-original-width="865" data-original-height="215" data-original-format="image/png"
                    data-original-filesize="18788" data-image-index="2" style="cursor: zoom-in;" class=""
                    src="//upload-images.jianshu.io/upload_images/6078268-705d0ceb55c30592.png?imageMogr2/auto-orient/strip|imageView2/2/w/865/format/webp">
            </div>
        </div>
        <div class="image-caption">同时打开两个窗口测试发现实现了多进程</div>
    </div>
</blockquote>
<hr>
<h3>3.options配置</h3>
<ul>
    <li>全局配置</li>
</ul>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-bash"><code class="  language-bash">tornado.options.define(
    name, default, type, multiple, help
)
<span aria-hidden="true" class="line-numbers-rows"><span></span><span></span><span></span></span></code></pre>
</div>
<ul>
    <li>命令行参数转换</li>
</ul>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-css"><code class="  language-css">tornado.options.parse_command_<span
            class="token function">line</span><span class="token punctuation">(</span><span
            class="token punctuation">)</span>
<span aria-hidden="true" class="line-numbers-rows"><span></span></span></code></pre>
</div>
<blockquote>
    <div class="_2Uzcx_">
        <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy"
                                                                  class="anticon anticon-copy">
            <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
                 fill="currentColor" aria-hidden="true">
                <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
            </svg>
        </i></button>
        <pre class="line-numbers  language-python"><code class="  language-python"><span class="token comment">#-*- coding:utf-8 -*-</span>

<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>web <span class="token keyword">import</span> RequestHandler<span
                    class="token punctuation">,</span>Application
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>ioloop <span
                    class="token keyword">import</span> IOLoop
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>httpserver <span
                    class="token keyword">import</span> HTTPServer
<span class="token keyword">import</span> tornado<span class="token punctuation">.</span>options

<span class="token comment">#定义变量</span>
tornado<span class="token punctuation">.</span>options<span class="token punctuation">.</span>define<span
                    class="token punctuation">(</span><span class="token string">'port'</span><span
                    class="token punctuation">,</span>default<span class="token operator">=</span><span
                    class="token number">8000</span><span class="token punctuation">,</span><span
                    class="token builtin">type</span><span class="token operator">=</span><span
                    class="token builtin">int</span><span class="token punctuation">,</span><span
                    class="token builtin">help</span><span class="token operator">=</span><span
                    class="token string">"this is the port &gt;for application"</span><span
                    class="token punctuation">)</span>

<span class="token keyword">class</span> <span class="token class-name">IndexHandler</span><span
                    class="token punctuation">(</span>RequestHandler<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
   <span class="token keyword">def</span> <span class="token function">get</span><span
                    class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
       self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                    class="token string">'我们既然改变不了规则，那就做到最好'</span><span class="token punctuation">)</span>

<span class="token keyword">if</span> __name__ <span class="token operator">==</span> <span class="token string">'__main__'</span><span
                    class="token punctuation">:</span>
   app <span class="token operator">=</span> Application<span class="token punctuation">(</span><span
                    class="token punctuation">[</span><span class="token punctuation">(</span><span
                    class="token string">r'/'</span><span class="token punctuation">,</span>IndexHandler<span
                    class="token punctuation">)</span><span class="token punctuation">]</span><span
                    class="token punctuation">)</span>
   tornado<span class="token punctuation">.</span>options<span class="token punctuation">.</span>parse_command_line<span
                    class="token punctuation">(</span><span class="token punctuation">)</span>

   http_server <span class="token operator">=</span> HTTPServer<span class="token punctuation">(</span>app<span
                    class="token punctuation">)</span>
   http_server<span class="token punctuation">.</span>bind<span class="token punctuation">(</span>tornado<span
                    class="token punctuation">.</span>options<span class="token punctuation">.</span>options<span
                    class="token punctuation">.</span>port<span class="token punctuation">)</span>
   http_server<span class="token punctuation">.</span>start<span class="token punctuation">(</span><span
                    class="token number">1</span><span class="token punctuation">)</span>
   <span class="token comment">#启动IOLoop轮循监听</span>
   IOLoop<span class="token punctuation">.</span>current<span class="token punctuation">(</span><span
                    class="token punctuation">)</span><span class="token punctuation">.</span>start<span
                    class="token punctuation">(</span><span class="token punctuation">)</span>
<span aria-hidden="true"
      class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre>
    </div>
    <div class="image-package">
        <div class="image-container" style="max-width: 649px; max-height: 96px; background-color: transparent;">
            <div class="image-container-fill" style="padding-bottom: 14.790000000000001%;"></div>
            <div class="image-view" data-width="649" data-height="96"><img
                    data-original-src="//upload-images.jianshu.io/upload_images/6078268-bccf79d026ee242e.png"
                    data-original-width="649" data-original-height="96" data-original-format="image/png"
                    data-original-filesize="9767" data-image-index="3" style="cursor: zoom-in;" class=""
                    src="//upload-images.jianshu.io/upload_images/6078268-bccf79d026ee242e.png?imageMogr2/auto-orient/strip|imageView2/2/w/649/format/webp">
            </div>
        </div>
        <div class="image-caption">通过命令窗口输入port来访问</div>
    </div>
    <br>
    <div class="image-package">
        <div class="image-container" style="max-width: 678px; max-height: 275px; background-color: transparent;">
            <div class="image-container-fill" style="padding-bottom: 40.56%;"></div>
            <div class="image-view" data-width="678" data-height="275"><img
                    data-original-src="//upload-images.jianshu.io/upload_images/6078268-1ad79f25896841cc.png"
                    data-original-width="678" data-original-height="275" data-original-format="image/png"
                    data-original-filesize="18587" data-image-index="4" style="cursor: zoom-in;" class=""
                    src="//upload-images.jianshu.io/upload_images/6078268-1ad79f25896841cc.png?imageMogr2/auto-orient/strip|imageView2/2/w/678/format/webp">
            </div>
        </div>
        <div class="image-caption">通过使用我们命令窗口设定的port进行访问</div>
    </div>
</blockquote>
<ul>
    <li>配置文件</li>
</ul>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-bash"><code class="  language-bash">#即在当前py文件目录创建config文件，并在py代码中加入以下代码，
tornado.options.parse_config_file("./config")
<span aria-hidden="true" class="line-numbers-rows"><span></span><span></span></span></code></pre>
</div>
<ul>
    <li>配置模块：跟配置文件类似</li>
</ul>
<h3>4.application配置</h3>
<ul>
    <li>程序调试之debug配置</li>
</ul>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-php"><code class="  language-php"><span class="token shell-comment comment">#自动重启+取消缓存模板+取消缓存静态文件+提供追踪信息</span>
tornado<span class="token punctuation">.</span>web<span class="token punctuation">.</span><span class="token function">Application</span><span
                class="token punctuation">(</span><span class="token punctuation">[</span><span
                class="token punctuation">(</span><span class="token punctuation">.</span><span
                class="token punctuation">.</span><span class="token punctuation">)</span><span
                class="token punctuation">]</span><span class="token punctuation">,</span> debug<span
                class="token operator">=</span><span class="token boolean constant">True</span><span
                class="token punctuation">)</span>

注：开发之初可以设置debug<span class="token operator">=</span><span class="token boolean constant">True</span>方便调试，开发完毕改为<span
                class="token boolean constant">False</span><span class="token punctuation">.</span>
<span aria-hidden="true"
      class="line-numbers-rows"><span></span><span></span><span></span><span></span></span></code></pre>
</div>
<ul>
    <li>路由信息初始化参数配置</li>
</ul>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-ruby"><code class="  language-ruby">tonado<span
            class="token punctuation">.</span>web<span class="token punctuation">.</span><span
            class="token constant">Application</span><span class="token punctuation">(</span><span
            class="token punctuation">[</span><span class="token punctuation">(</span>r””<span
            class="token punctuation">,</span> <span class="token constant">Handler</span><span
            class="token punctuation">,</span> <span class="token punctuation">{</span>k<span
            class="token symbol">:v</span><span
            class="token punctuation">}</span><span class="token punctuation">)</span><span
            class="token punctuation">]</span><span class="token punctuation">)</span>
<span class="token keyword">def</span> <span class="token method-definition"><span
                class="token function">initialize</span></span><span class="token punctuation">(</span><span
                class="token keyword">self</span><span class="token punctuation">,</span> k<span
                class="token punctuation">)</span>
<span aria-hidden="true" class="line-numbers-rows"><span></span><span></span></span></code></pre>
</div>
<blockquote>
    <div class="_2Uzcx_">
        <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy"
                                                                  class="anticon anticon-copy">
            <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
                 fill="currentColor" aria-hidden="true">
                <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
            </svg>
        </i></button>
        <pre class="line-numbers  language-python"><code class="  language-python"><span class="token comment">#-*- coding:utf-8 -*-</span>
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>web <span class="token keyword">import</span> RequestHandler<span
                    class="token punctuation">,</span>Application
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>ioloop <span
                    class="token keyword">import</span> IOLoop
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>httpserver <span
                    class="token keyword">import</span> HTTPServer
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>options <span
                    class="token keyword">import</span> define<span class="token punctuation">,</span>options

define<span class="token punctuation">(</span><span class="token string">'port'</span><span
                    class="token punctuation">,</span>default<span class="token operator">=</span><span
                    class="token number">8000</span><span class="token punctuation">,</span><span
                    class="token builtin">type</span><span class="token operator">=</span><span
                    class="token builtin">int</span><span class="token punctuation">)</span>

<span class="token keyword">class</span> <span class="token class-name">IndexHandler</span><span
                    class="token punctuation">(</span>RequestHandler<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
   <span class="token keyword">def</span> <span class="token function">get</span><span
                    class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
       self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                    class="token string">'get--&gt;先自沉稳，而后爱人'</span><span class="token punctuation">)</span>


<span class="token keyword">class</span> <span class="token class-name">ArticleHandler</span><span
                    class="token punctuation">(</span>RequestHandler<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
   <span class="token keyword">def</span> <span class="token function">initialize</span><span class="token punctuation">(</span>self<span
                    class="token punctuation">,</span>title<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
       <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">'--&gt;initialize()'</span><span
                    class="token punctuation">)</span>
       self<span class="token punctuation">.</span>title <span class="token operator">=</span> title

   <span class="token keyword">def</span> <span class="token function">get</span><span
                    class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
       self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                    class="token string">'你正在查看文章：%s'</span><span class="token operator">%</span> self<span
                    class="token punctuation">.</span>title<span class="token punctuation">)</span>

<span class="token keyword">if</span> __name__ <span class="token operator">==</span> <span class="token string">'__main__'</span><span
                    class="token punctuation">:</span>
   options<span class="token punctuation">.</span>parse_command_line<span class="token punctuation">(</span><span
                    class="token punctuation">)</span>

   app <span class="token operator">=</span> Application<span class="token punctuation">(</span><span
                    class="token punctuation">[</span><span class="token punctuation">(</span><span
                    class="token string">r'/'</span><span class="token punctuation">,</span>IndexHandler<span
                    class="token punctuation">)</span><span class="token punctuation">,</span><span
                    class="token punctuation">(</span><span class="token string">r'/article'</span><span
                    class="token punctuation">,</span>ArticleHandler<span class="token punctuation">,</span><span
                    class="token punctuation">{</span><span class="token string">'title'</span><span
                    class="token punctuation">:</span><span
                    class="token string">'你&gt;希望自己成为什么样的人，最终就会成为那样的人。'</span><span
                    class="token punctuation">}</span><span class="token punctuation">)</span><span
                    class="token punctuation">]</span><span class="token punctuation">,</span>debug<span
                    class="token operator">=</span><span class="token boolean">True</span><span
                    class="token punctuation">)</span>
   http_server <span class="token operator">=</span> HTTPServer<span class="token punctuation">(</span>app<span
                    class="token punctuation">)</span>
   http_server<span class="token punctuation">.</span>bind<span class="token punctuation">(</span>options<span
                    class="token punctuation">.</span>port<span class="token punctuation">)</span>
   http_server<span class="token punctuation">.</span>start<span class="token punctuation">(</span><span
                    class="token number">1</span><span class="token punctuation">)</span>

   IOLoop<span class="token punctuation">.</span>current<span class="token punctuation">(</span><span
                    class="token punctuation">)</span><span class="token punctuation">.</span>start<span
                    class="token punctuation">(</span><span class="token punctuation">)</span>
<span aria-hidden="true"
      class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre>
    </div>
    <div class="image-package">
        <div class="image-container" style="max-width: 700px; max-height: 202px;">
            <div class="image-container-fill" style="padding-bottom: 21.44%;"></div>
            <div class="image-view" data-width="942" data-height="202"><img
                    data-original-src="//upload-images.jianshu.io/upload_images/6078268-1c50921fb9fb7ac2.png"
                    data-original-width="942" data-original-height="202" data-original-format="image/png"
                    data-original-filesize="21642" data-image-index="5" style="cursor: zoom-in;"
                    class="image-loading"></div>
        </div>
        <div class="image-caption">输入路径，显示结果</div>
    </div>
</blockquote>
<ul>
    <li>路由名称设置及反解析</li>
</ul>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-bash"><code class="  language-bash">#名称设置
tornado.web.Application([
    url(r””, handler, {k,v}, name=“”)
])

#反解析操作
reverse_url(name)
<span aria-hidden="true"
      class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre>
</div>
<blockquote>
    <div class="_2Uzcx_">
        <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy"
                                                                  class="anticon anticon-copy">
            <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
                 fill="currentColor" aria-hidden="true">
                <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
            </svg>
        </i></button>
        <pre class="line-numbers  language-python"><code class="  language-python"><span class="token comment"># -*- coding:utf-8 -*-</span>

<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>web <span class="token keyword">import</span> Application<span
                    class="token punctuation">,</span> RequestHandler<span class="token punctuation">,</span> url
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>ioloop <span
                    class="token keyword">import</span> IOLoop
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>httpserver <span
                    class="token keyword">import</span> HTTPServer
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>options <span
                    class="token keyword">import</span> options<span class="token punctuation">,</span>define

define<span class="token punctuation">(</span><span class="token string">"port"</span><span
                    class="token punctuation">,</span> default<span class="token operator">=</span><span
                    class="token number">8000</span><span class="token punctuation">,</span> <span
                    class="token builtin">type</span><span class="token operator">=</span><span
                    class="token builtin">int</span><span class="token punctuation">)</span>

<span class="token keyword">class</span> <span class="token class-name">IndexHandler</span><span
                    class="token punctuation">(</span>RequestHandler<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>

   <span class="token keyword">def</span> <span class="token function">get</span><span
                    class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
       self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                    class="token string">"&lt;a href='"</span><span class="token operator">+</span>self<span
                    class="token punctuation">.</span>reverse_url<span class="token punctuation">(</span><span
                    class="token string">"login"</span><span class="token punctuation">)</span><span
                    class="token operator">+</span><span class="token string">"'&gt;用户登录&lt;/a&gt;"</span><span
                    class="token punctuation">)</span>


<span class="token keyword">class</span> <span class="token class-name">RegistHandler</span><span
                    class="token punctuation">(</span>RequestHandler<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
   <span class="token keyword">def</span> <span class="token function">initialize</span><span class="token punctuation">(</span>self<span
                    class="token punctuation">,</span> title<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
       self<span class="token punctuation">.</span>title <span class="token operator">=</span> title

   <span class="token keyword">def</span> <span class="token function">get</span><span
                    class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
       self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                    class="token string">"注册业务处理:"</span> <span class="token operator">+</span> <span
                    class="token builtin">str</span><span class="token punctuation">(</span>self<span
                    class="token punctuation">.</span>title<span class="token punctuation">)</span><span
                    class="token punctuation">)</span>


<span class="token keyword">class</span> <span class="token class-name">LoginHandler</span><span
                    class="token punctuation">(</span>RequestHandler<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
   <span class="token keyword">def</span> <span class="token function">get</span><span
                    class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
       self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                    class="token string">"用户登录页面展示"</span><span class="token punctuation">)</span>

   <span class="token keyword">def</span> <span class="token function">post</span><span
                    class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
      self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                    class="token string">"用户登录功能处理"</span><span class="token punctuation">)</span>


<span class="token keyword">if</span> __name__ <span class="token operator">==</span> <span class="token string">"__main__"</span><span
                    class="token punctuation">:</span>
   app <span class="token operator">=</span> Application<span class="token punctuation">(</span>
       <span class="token punctuation">[</span>
           <span class="token punctuation">(</span><span class="token string">r"/"</span><span
                    class="token punctuation">,</span> IndexHandler<span class="token punctuation">)</span><span
                    class="token punctuation">,</span>
           <span class="token punctuation">(</span><span class="token string">r"/regist"</span><span
                    class="token punctuation">,</span> RegistHandler<span class="token punctuation">,</span> <span
                    class="token punctuation">{</span><span class="token string">"title"</span><span
                    class="token punctuation">:</span> <span class="token string">"会员注册"</span><span
                    class="token punctuation">}</span><span class="token punctuation">)</span><span
                    class="token punctuation">,</span>
           url<span class="token punctuation">(</span><span class="token string">r"/login"</span><span
                    class="token punctuation">,</span> LoginHandler<span
                    class="token punctuation">,</span> name<span class="token operator">=</span><span
                    class="token string">"login"</span><span class="token punctuation">)</span><span
                    class="token punctuation">,</span>
       <span class="token punctuation">]</span>
   <span class="token punctuation">)</span>

   http_server <span class="token operator">=</span> HTTPServer<span class="token punctuation">(</span>app<span
                    class="token punctuation">)</span>
   http_server<span class="token punctuation">.</span>listen<span class="token punctuation">(</span><span
                    class="token number">8000</span><span class="token punctuation">)</span>

   IOLoop<span class="token punctuation">.</span>current<span class="token punctuation">(</span><span
                    class="token punctuation">)</span><span class="token punctuation">.</span>start<span
                    class="token punctuation">(</span><span class="token punctuation">)</span>
<span aria-hidden="true"
      class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre>
    </div>
    <div class="image-package">
        <div class="image-container" style="max-width: 509px; max-height: 235px;">
            <div class="image-container-fill" style="padding-bottom: 46.17%;"></div>
            <div class="image-view" data-width="509" data-height="235"><img
                    data-original-src="//upload-images.jianshu.io/upload_images/6078268-d365925a59e9e8b3.gif"
                    data-original-width="509" data-original-height="235" data-original-format="image/gif"
                    data-original-filesize="74573" data-image-index="6" style="cursor: zoom-in;"
                    class="image-loading"></div>
        </div>
        <div class="image-caption">浏览器显示结果</div>
    </div>
</blockquote>
<h3>5.参数传递</h3>
<ul>
    <li>get方式传递参数</li>
</ul>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-php"><code class="  language-php"><span class="token function">get_query_arguments</span><span
            class="token punctuation">(</span>name<span class="token punctuation">,</span><span
            class="token keyword">default</span><span class="token operator">=</span><span class="token constant">_ARG_DEFAULT</span><span
            class="token punctuation">,</span>strip<span class="token operator">=</span><span
            class="token boolean constant">True</span><span class="token punctuation">)</span>
<span class="token function">get_query_argument</span><span class="token punctuation">(</span>name <span
                class="token punctuation">,</span>strip<span class="token operator">=</span><span
                class="token boolean constant">True</span><span class="token punctuation">)</span>
<span aria-hidden="true" class="line-numbers-rows"><span></span><span></span></span></code></pre>
</div>
<blockquote>
    <div class="_2Uzcx_">
        <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy"
                                                                  class="anticon anticon-copy">
            <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
                 fill="currentColor" aria-hidden="true">
                <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
            </svg>
        </i></button>
        <pre class="line-numbers  language-python"><code class="  language-python"><span class="token comment"># -*- coding:utf-8 -*-</span>

<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>web <span class="token keyword">import</span> Application<span
                    class="token punctuation">,</span> RequestHandler
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>ioloop <span
                    class="token keyword">import</span> IOLoop
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>httpserver <span
                    class="token keyword">import</span> HTTPServer
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>options <span
                    class="token keyword">import</span> options<span class="token punctuation">,</span> define

define<span class="token punctuation">(</span><span class="token string">"port"</span><span
                    class="token punctuation">,</span> default<span class="token operator">=</span><span
                    class="token number">8000</span><span class="token punctuation">,</span> <span
                    class="token builtin">type</span><span class="token operator">=</span><span
                    class="token builtin">int</span><span class="token punctuation">)</span>


<span class="token keyword">class</span> <span class="token class-name">IndexHandler</span><span
                    class="token punctuation">(</span>RequestHandler<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>

   <span class="token keyword">def</span> <span class="token function">get</span><span
                    class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
       <span class="token comment"># 获取get方式传递的参数</span>
       username <span class="token operator">=</span> self<span
                    class="token punctuation">.</span>get_query_argument<span
                    class="token punctuation">(</span><span class="token string">"username"</span><span
                    class="token punctuation">)</span>
       usernames <span class="token operator">=</span> self<span
                    class="token punctuation">.</span>get_query_arguments<span
                    class="token punctuation">(</span><span class="token string">"username"</span><span
                    class="token punctuation">)</span>

       <span class="token keyword">print</span> <span class="token punctuation">(</span>username<span
                    class="token punctuation">)</span>
       <span class="token keyword">print</span> <span class="token punctuation">(</span>usernames<span
                    class="token punctuation">)</span>

<span class="token keyword">if</span> __name__ <span class="token operator">==</span> <span class="token string">"__main__"</span><span
                    class="token punctuation">:</span>
   app <span class="token operator">=</span> Application<span class="token punctuation">(</span><span
                    class="token punctuation">[</span><span class="token punctuation">(</span><span
                    class="token string">r"/"</span><span class="token punctuation">,</span> IndexHandler<span
                    class="token punctuation">)</span><span class="token punctuation">]</span><span
                    class="token punctuation">)</span>

   app<span class="token punctuation">.</span>listen<span class="token punctuation">(</span><span class="token number">8000</span><span
                    class="token punctuation">)</span>

   IOLoop<span class="token punctuation">.</span>current<span class="token punctuation">(</span><span
                    class="token punctuation">)</span><span class="token punctuation">.</span>start<span
                    class="token punctuation">(</span><span class="token punctuation">)</span>
<span aria-hidden="true"
      class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre>
    </div>
    <div class="image-package">
        <div class="image-container" style="max-width: 700px; max-height: 338px;">
            <div class="image-container-fill" style="padding-bottom: 46.43%;"></div>
            <div class="image-view" data-width="728" data-height="338"><img
                    data-original-src="//upload-images.jianshu.io/upload_images/6078268-51d3d5638480d718.png"
                    data-original-width="728" data-original-height="338" data-original-format="image/png"
                    data-original-filesize="28344" data-image-index="7" style="cursor: zoom-in;"
                    class="image-loading"></div>
        </div>
        <div class="image-caption"></div>
    </div>
</blockquote>
<ul>
    <li>post方式传递参数</li>
</ul>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-php"><code class="  language-php"><span
            class="token function">get_body_arguments</span><span
            class="token punctuation">(</span>name<span class="token punctuation">,</span> <span
            class="token keyword">default</span><span class="token operator">=</span><span class="token constant">_ARG_DEFAULT</span><span
            class="token punctuation">,</span>strip<span class="token operator">=</span><span
            class="token boolean constant">True</span><span class="token punctuation">)</span>
<span class="token function">get_body_argument</span><span class="token punctuation">(</span>name <span
                class="token punctuation">,</span>strip<span class="token operator">=</span><span
                class="token boolean constant">True</span><span class="token punctuation">)</span>
<span aria-hidden="true" class="line-numbers-rows"><span></span><span></span></span></code></pre>
</div>
<ul>
    <li>混合方式</li>
</ul>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-undefined"><code class="  language-undefined">get_arguments(..)/get_argument(..)
<span aria-hidden="true" class="line-numbers-rows"><span></span></span></code></pre>
</div>
<blockquote>
    <div class="_2Uzcx_">
        <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy"
                                                                  class="anticon anticon-copy">
            <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
                 fill="currentColor" aria-hidden="true">
                <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
            </svg>
        </i></button>
        <pre class="line-numbers  language-python"><code class="  language-python"><span class="token comment"># -*- coding:utf-8 -*-</span>

<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>web <span class="token keyword">import</span> Application<span
                    class="token punctuation">,</span> RequestHandler
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>ioloop <span
                    class="token keyword">import</span> IOLoop
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>options <span
                    class="token keyword">import</span> options<span class="token punctuation">,</span> define

define<span class="token punctuation">(</span><span class="token string">"port"</span><span
                    class="token punctuation">,</span> default<span class="token operator">=</span><span
                    class="token number">8000</span><span class="token punctuation">,</span> <span
                    class="token builtin">type</span><span class="token operator">=</span><span
                    class="token builtin">int</span><span class="token punctuation">)</span>


<span class="token keyword">class</span> <span class="token class-name">IndexHandler</span><span
                    class="token punctuation">(</span>RequestHandler<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>

   <span class="token keyword">def</span> <span class="token function">get</span><span
                    class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
       <span class="token comment"># 获取get方式的参数</span>
       user <span class="token operator">=</span> self<span class="token punctuation">.</span>get_argument<span
                    class="token punctuation">(</span><span class="token string">"user"</span><span
                    class="token punctuation">)</span>
       <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"get方式获取参数："</span> <span
                    class="token operator">+</span> <span class="token builtin">str</span><span
                    class="token punctuation">(</span>user<span class="token punctuation">)</span><span
                    class="token punctuation">)</span>

   <span class="token keyword">def</span> <span class="token function">post</span><span
                    class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                    class="token punctuation">:</span>
       <span class="token comment"># 获取post方式的参数</span>
       user <span class="token operator">=</span> self<span class="token punctuation">.</span>get_argument<span
                    class="token punctuation">(</span><span class="token string">"user"</span><span
                    class="token punctuation">)</span>
       <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"post方式获取参数："</span> <span
                    class="token operator">+</span> user<span class="token punctuation">.</span>encode<span
                    class="token punctuation">(</span><span class="token string">"utf-8"</span><span
                    class="token punctuation">)</span><span class="token punctuation">)</span>


<span class="token keyword">if</span> __name__ <span class="token operator">==</span> <span class="token string">"__main__"</span><span
                    class="token punctuation">:</span>
   app <span class="token operator">=</span> Application<span class="token punctuation">(</span><span
                    class="token punctuation">[</span><span class="token punctuation">(</span><span
                    class="token string">r"/"</span><span class="token punctuation">,</span> IndexHandler<span
                    class="token punctuation">)</span><span class="token punctuation">]</span><span
                    class="token punctuation">)</span>
   app<span class="token punctuation">.</span>listen<span class="token punctuation">(</span><span class="token number">8888</span><span
                    class="token punctuation">)</span>
   IOLoop<span class="token punctuation">.</span>current<span class="token punctuation">(</span><span
                    class="token punctuation">)</span><span class="token punctuation">.</span>start<span
                    class="token punctuation">(</span><span class="token punctuation">)</span>
<span aria-hidden="true"
      class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre>
    </div>
    <div class="image-package">
        <div class="image-container" style="max-width: 700px; max-height: 658px;">
            <div class="image-container-fill" style="padding-bottom: 55.34%;"></div>
            <div class="image-view" data-width="1189" data-height="658"><img
                    data-original-src="//upload-images.jianshu.io/upload_images/6078268-d8be0662d0b22591.gif"
                    data-original-width="1189" data-original-height="658" data-original-format="image/gif"
                    data-original-filesize="355972" data-image-index="8" style="cursor: zoom-in;"
                    class="image-loading"></div>
        </div>
        <div class="image-caption">使用谷歌浏览器的应用postman可以看到get和post请求</div>
    </div>
</blockquote>
<ul>
    <li>其他参数</li>
</ul>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-undefined"><code class="  language-undefined">通过request获取参数数据
method/host/uri/path/query/version/headers/body/remote_ip/files
<span aria-hidden="true" class="line-numbers-rows"><span></span><span></span></span></code></pre>
</div>
<h3>6.响应头设置</h3>
<ul>
    <li>set_header(name, value)</li>
    <li>set_default_headers(self)</li>
    <li>add_header(name, value)</li>
    <li>clear_header(name)</li>
</ul>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-python"><code class="  language-python"><span class="token comment"># -*- coding:utf-8 -*-</span>

<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>web <span class="token keyword">import</span> Application<span
                class="token punctuation">,</span> RequestHandler
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>ioloop <span
                class="token keyword">import</span> IOLoop
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>options <span
                class="token keyword">import</span> options<span class="token punctuation">,</span> define

define<span class="token punctuation">(</span><span class="token string">"port"</span><span
                class="token punctuation">,</span> default<span class="token operator">=</span><span
                class="token number">8000</span><span class="token punctuation">,</span> <span
                class="token builtin">type</span><span class="token operator">=</span><span
                class="token builtin">int</span><span
                class="token punctuation">)</span>


<span class="token keyword">class</span> <span class="token class-name">IndexHandler</span><span
                class="token punctuation">(</span>RequestHandler<span class="token punctuation">)</span><span
                class="token punctuation">:</span>
    <span class="token keyword">def</span> <span class="token function">set_default_headers</span><span
                class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                class="token punctuation">:</span>
        <span class="token comment"># 第二种响应头设置方式</span>
        <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"---------&gt; 响应头set_default_headers()执行"</span><span
                class="token punctuation">)</span>
        self<span class="token punctuation">.</span>set_header<span class="token punctuation">(</span><span
                class="token string">"Content-type"</span><span class="token punctuation">,</span> <span
                class="token string">"application/json; charset=utf-8"</span><span
                class="token punctuation">)</span>
        self<span class="token punctuation">.</span>set_header<span class="token punctuation">(</span><span
                class="token string">"js"</span><span class="token punctuation">,</span> <span
                class="token string">"zj"</span><span
                class="token punctuation">)</span>

    <span class="token keyword">def</span> <span class="token function">get</span><span
                class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                class="token punctuation">:</span>
        <span class="token comment"># 第一种操作响应头的方式：</span>
        <span class="token comment"># self.set_header("Content-type", "application/json")</span>
        <span class="token keyword">print</span><span class="token punctuation">(</span><span class="token string">"----------&gt;get方法执行"</span><span
                class="token punctuation">)</span>
        self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                class="token string">"{'简书':'知几'}"</span><span class="token punctuation">)</span>
        self<span class="token punctuation">.</span>set_header<span class="token punctuation">(</span><span
                class="token string">"jianshu"</span><span class="token punctuation">,</span> <span
                class="token string">"zhiji"</span><span class="token punctuation">)</span>


<span class="token keyword">if</span> __name__ <span class="token operator">==</span> <span class="token string">"__main__"</span><span
                class="token punctuation">:</span>
    app <span class="token operator">=</span> Application<span class="token punctuation">(</span><span
                class="token punctuation">[</span><span class="token punctuation">(</span><span
                class="token string">r"/"</span><span class="token punctuation">,</span> IndexHandler<span
                class="token punctuation">)</span><span class="token punctuation">]</span><span
                class="token punctuation">)</span>

    app<span class="token punctuation">.</span>listen<span class="token punctuation">(</span><span class="token number">8000</span><span
                class="token punctuation">)</span>

    IOLoop<span class="token punctuation">.</span>current<span class="token punctuation">(</span><span
                class="token punctuation">)</span><span class="token punctuation">.</span>start<span
                class="token punctuation">(</span><span class="token punctuation">)</span>
<span aria-hidden="true"
      class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre>
</div>
<div class="image-package">
    <div class="image-container" style="max-width: 700px; max-height: 644px;">
        <div class="image-container-fill" style="padding-bottom: 74.53999999999999%;"></div>
        <div class="image-view" data-width="864" data-height="644"><img
                data-original-src="//upload-images.jianshu.io/upload_images/6078268-f041c23aaf86a077.png"
                data-original-width="864" data-original-height="644" data-original-format="image/png"
                data-original-filesize="66245" data-image-index="9" style="cursor: zoom-in;" class="image-loading">
        </div>
    </div>
    <div class="image-caption">浏览器显示结果</div>
</div>
<h3>7.cookie操作</h3>
<ul>
    <li>cookies</li>
</ul>
<blockquote>
    <ul>
        <li><p>set/get_cookie(name, value)</p></li>
        <li><p>set/get_secure_cookie(name, value)</p></li>
        <li><p>clear_cookie(name)</p></li>
        <li><p>clear_all_cookie()</p></li>
    </ul>
</blockquote>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-python"><code class="  language-python"><span class="token comment"># -*- coding:utf-8 -*-</span>

<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>web <span class="token keyword">import</span> Application<span
                class="token punctuation">,</span> RequestHandler
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>ioloop <span
                class="token keyword">import</span> IOLoop
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>options <span
                class="token keyword">import</span> options<span class="token punctuation">,</span> define

define<span class="token punctuation">(</span><span class="token string">"port"</span><span
                class="token punctuation">,</span> default<span class="token operator">=</span><span
                class="token number">8000</span><span class="token punctuation">,</span> <span
                class="token builtin">type</span><span class="token operator">=</span><span
                class="token builtin">int</span><span
                class="token punctuation">)</span>


<span class="token keyword">class</span> <span class="token class-name">IndexHandler</span><span
                class="token punctuation">(</span>RequestHandler<span class="token punctuation">)</span><span
                class="token punctuation">:</span>

    <span class="token keyword">def</span> <span class="token function">get</span><span
                class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                class="token punctuation">:</span>
        self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                class="token string">"hello jianshu.com"</span><span class="token punctuation">)</span>

        self<span class="token punctuation">.</span>set_cookie<span class="token punctuation">(</span><span
                class="token string">"loginuser"</span><span class="token punctuation">,</span> <span
                class="token string">"admin"</span><span class="token punctuation">)</span>

        <span class="token keyword">print</span> self<span class="token punctuation">.</span>get_cookie<span
                class="token punctuation">(</span><span class="token string">"loginuser"</span><span
                class="token punctuation">)</span>

        <span class="token keyword">print</span> self<span class="token punctuation">.</span>cookies


<span class="token keyword">if</span> __name__ <span class="token operator">==</span> <span class="token string">"__main__"</span><span
                class="token punctuation">:</span>
    app <span class="token operator">=</span> Application<span class="token punctuation">(</span><span
                class="token punctuation">[</span><span class="token punctuation">(</span><span
                class="token string">r"/"</span><span class="token punctuation">,</span> IndexHandler<span
                class="token punctuation">)</span><span class="token punctuation">]</span><span
                class="token punctuation">)</span>

    app<span class="token punctuation">.</span>listen<span class="token punctuation">(</span><span class="token number">8000</span><span
                class="token punctuation">)</span>

    IOLoop<span class="token punctuation">.</span>current<span class="token punctuation">(</span><span
                class="token punctuation">)</span><span class="token punctuation">.</span>start<span
                class="token punctuation">(</span><span class="token punctuation">)</span>
<span aria-hidden="true"
      class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre>
</div>
<div class="image-package">
    <div class="image-container" style="max-width: 700px; max-height: 640px;">
        <div class="image-container-fill" style="padding-bottom: 61.9%;"></div>
        <div class="image-view" data-width="1034" data-height="640"><img
                data-original-src="//upload-images.jianshu.io/upload_images/6078268-d6c7b52cbb044b76.png"
                data-original-width="1034" data-original-height="640" data-original-format="image/png"
                data-original-filesize="72122" data-image-index="10" style="cursor: zoom-in;" class="image-loading">
        </div>
    </div>
    <div class="image-caption">可以看到cookie已生效</div>
</div>
<h3>8.响应错误码 &amp; 错误描述</h3>
<ul>
    <li>set_status(status_code, reason=None)</li>
</ul>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-python"><code class="  language-python"><span class="token comment"># -*- coding:utf-8 -*-</span>

<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>web <span class="token keyword">import</span> Application<span
                class="token punctuation">,</span> RequestHandler
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>ioloop <span
                class="token keyword">import</span> IOLoop
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>options <span
                class="token keyword">import</span> options<span class="token punctuation">,</span> define

define<span class="token punctuation">(</span><span class="token string">"port"</span><span
                class="token punctuation">,</span> default<span class="token operator">=</span><span
                class="token number">8000</span><span class="token punctuation">,</span> <span
                class="token builtin">type</span><span class="token operator">=</span><span
                class="token builtin">int</span><span
                class="token punctuation">)</span>


<span class="token keyword">class</span> <span class="token class-name">IndexHandler</span><span
                class="token punctuation">(</span>RequestHandler<span class="token punctuation">)</span><span
                class="token punctuation">:</span>

    <span class="token keyword">def</span> <span class="token function">get</span><span
                class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                class="token punctuation">:</span>
        self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                class="token string">"hello 简书"</span><span class="token punctuation">)</span>
        <span class="token comment"># self.set_status(404) # 标准错误码 无描述使用默认描述</span>
        self<span class="token punctuation">.</span>set_status<span class="token punctuation">(</span><span
                class="token number">201</span><span class="token punctuation">,</span> reason<span
                class="token operator">=</span><span class="token string">"zhiji is cool"</span><span
                class="token punctuation">)</span> <span class="token comment"># 自定义错误码，设置reason描述</span>
        <span class="token comment"># self.set_status(230) # 自定义错误码，无reason 报错</span>

<span class="token keyword">if</span> __name__ <span class="token operator">==</span> <span class="token string">"__main__"</span><span
                class="token punctuation">:</span>
    app <span class="token operator">=</span> Application<span class="token punctuation">(</span><span
                class="token punctuation">[</span><span class="token punctuation">(</span><span
                class="token string">r"/"</span><span class="token punctuation">,</span> IndexHandler<span
                class="token punctuation">)</span><span class="token punctuation">]</span><span
                class="token punctuation">)</span>

    app<span class="token punctuation">.</span>listen<span class="token punctuation">(</span><span class="token number">8000</span><span
                class="token punctuation">)</span>

    IOLoop<span class="token punctuation">.</span>current<span class="token punctuation">(</span><span
                class="token punctuation">)</span><span class="token punctuation">.</span>start<span
                class="token punctuation">(</span><span class="token punctuation">)</span>
<span aria-hidden="true"
      class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre>
</div>
<div class="image-package">
    <div class="image-container" style="max-width: 700px; max-height: 619px;">
        <div class="image-container-fill" style="padding-bottom: 52.68000000000001%;"></div>
        <div class="image-view" data-width="1175" data-height="619"><img
                data-original-src="//upload-images.jianshu.io/upload_images/6078268-d5c7a5fbd0544ec4.png"
                data-original-width="1175" data-original-height="619" data-original-format="image/png"
                data-original-filesize="71212" data-image-index="11" style="cursor: zoom-in;" class="image-loading">
        </div>
    </div>
    <div class="image-caption">通过审查元素我们可以测试定义的错误码有没有生效</div>
</div>
<ul>
    <li>send_error(status_code, reason=None)</li>
</ul>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-python"><code class="  language-python"><span class="token comment"># -*- coding:utf-8 -*-</span>

<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>web <span class="token keyword">import</span> Application<span
                class="token punctuation">,</span> RequestHandler
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>ioloop <span
                class="token keyword">import</span> IOLoop
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>options <span
                class="token keyword">import</span> options<span class="token punctuation">,</span> define

define<span class="token punctuation">(</span><span class="token string">"port"</span><span
                class="token punctuation">,</span> default<span class="token operator">=</span><span
                class="token number">8000</span><span class="token punctuation">,</span> <span
                class="token builtin">type</span><span class="token operator">=</span><span
                class="token builtin">int</span><span
                class="token punctuation">)</span>


<span class="token keyword">class</span> <span class="token class-name">IndexHandler</span><span
                class="token punctuation">(</span>RequestHandler<span class="token punctuation">)</span><span
                class="token punctuation">:</span>

    <span class="token keyword">def</span> <span class="token function">get</span><span
                class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                class="token punctuation">:</span>
        self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                class="token string">"hello qikuedu.com"</span><span class="token punctuation">)</span>

        self<span class="token punctuation">.</span>send_error<span class="token punctuation">(</span><span
                class="token number">500</span><span class="token punctuation">,</span> reason<span
                class="token operator">=</span><span class="token string">"出错啦出错啦"</span><span
                class="token punctuation">)</span>

<span class="token keyword">if</span> __name__ <span class="token operator">==</span> <span class="token string">"__main__"</span><span
                class="token punctuation">:</span>
    app <span class="token operator">=</span> Application<span class="token punctuation">(</span><span
                class="token punctuation">[</span><span class="token punctuation">(</span><span
                class="token string">r"/"</span><span class="token punctuation">,</span> IndexHandler<span
                class="token punctuation">)</span><span class="token punctuation">]</span><span
                class="token punctuation">)</span>

    app<span class="token punctuation">.</span>listen<span class="token punctuation">(</span><span class="token number">8000</span><span
                class="token punctuation">)</span>

    IOLoop<span class="token punctuation">.</span>current<span class="token punctuation">(</span><span
                class="token punctuation">)</span><span class="token punctuation">.</span>start<span
                class="token punctuation">(</span><span class="token punctuation">)</span>
<span aria-hidden="true"
      class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre>
</div>
<div class="image-package">
    <div class="image-container" style="max-width: 700px; max-height: 183px;">
        <div class="image-container-fill" style="padding-bottom: 22.56%;"></div>
        <div class="image-view" data-width="811" data-height="183"><img
                data-original-src="//upload-images.jianshu.io/upload_images/6078268-142055a6a84b7379.png"
                data-original-width="811" data-original-height="183" data-original-format="image/png"
                data-original-filesize="8557" data-image-index="12" style="cursor: zoom-in;" class="image-loading">
        </div>
    </div>
    <div class="image-caption">浏览器显示结果</div>
</div>
<ul>
    <li>write_error(self, status_code, **kw)</li>
</ul>
<div class="_2Uzcx_">
    <button class="VJbwyy" type="button" aria-label="复制代码"><i aria-label="icon: copy" class="anticon anticon-copy">
        <svg viewBox="64 64 896 896" focusable="false" class="" data-icon="copy" width="1em" height="1em"
             fill="currentColor" aria-hidden="true">
            <path d="M832 64H296c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h496v688c0 4.4 3.6 8 8 8h56c4.4 0 8-3.6 8-8V96c0-17.7-14.3-32-32-32zM704 192H192c-17.7 0-32 14.3-32 32v530.7c0 8.5 3.4 16.6 9.4 22.6l173.3 173.3c2.2 2.2 4.7 4 7.4 5.5v1.9h4.2c3.5 1.3 7.2 2 11 2H704c17.7 0 32-14.3 32-32V224c0-17.7-14.3-32-32-32zM350 856.2L263.9 770H350v86.2zM664 888H414V746c0-22.1-17.9-40-40-40H232V264h432v624z"></path>
        </svg>
    </i></button>
    <pre class="line-numbers  language-python"><code class="  language-python"><span class="token comment"># -*- coding:utf-8 -*-</span>

<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>web <span class="token keyword">import</span> Application<span
                class="token punctuation">,</span> RequestHandler
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>ioloop <span
                class="token keyword">import</span> IOLoop
<span class="token keyword">from</span> tornado<span class="token punctuation">.</span>options <span
                class="token keyword">import</span> options<span class="token punctuation">,</span> define

define<span class="token punctuation">(</span><span class="token string">"port"</span><span
                class="token punctuation">,</span> default<span class="token operator">=</span><span
                class="token number">8000</span><span class="token punctuation">,</span> <span
                class="token builtin">type</span><span class="token operator">=</span><span
                class="token builtin">int</span><span
                class="token punctuation">)</span>


<span class="token keyword">class</span> <span class="token class-name">IndexHandler</span><span
                class="token punctuation">(</span>RequestHandler<span class="token punctuation">)</span><span
                class="token punctuation">:</span>

    <span class="token keyword">def</span> <span class="token function">get</span><span
                class="token punctuation">(</span>self<span class="token punctuation">)</span><span
                class="token punctuation">:</span>
        self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                class="token string">"hello qikuedu.com"</span><span class="token punctuation">)</span>

        self<span class="token punctuation">.</span>send_error<span class="token punctuation">(</span><span
                class="token number">404</span><span class="token punctuation">,</span> msg<span
                class="token operator">=</span><span class="token string">"页面丢失"</span><span
                class="token punctuation">,</span> info<span class="token operator">=</span><span
                class="token string">"家里服务器搞对象去了"</span><span class="token punctuation">)</span>

    <span class="token keyword">def</span> <span class="token function">write_error</span><span
                class="token punctuation">(</span>self<span class="token punctuation">,</span> status_code<span
                class="token punctuation">,</span> <span class="token operator">**</span>kwargs<span
                class="token punctuation">)</span><span class="token punctuation">:</span>
        self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                class="token string">"&lt;h1&gt;出错啦，工程师MM正在赶来的途中...&lt;/h1&gt;"</span><span
                class="token punctuation">)</span>
        self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                class="token string">"&lt;p&gt;错误信息:%s&lt;/p&gt;"</span> <span
                class="token operator">%</span> kwargs<span
                class="token punctuation">[</span><span class="token string">"msg"</span><span
                class="token punctuation">]</span><span class="token punctuation">)</span>
        self<span class="token punctuation">.</span>write<span class="token punctuation">(</span><span
                class="token string">"&lt;p&gt;错误描述:%s&lt;/p&gt;"</span> <span
                class="token operator">%</span> kwargs<span
                class="token punctuation">[</span><span class="token string">"info"</span><span
                class="token punctuation">]</span><span class="token punctuation">)</span>


<span class="token keyword">if</span> __name__ <span class="token operator">==</span> <span class="token string">"__main__"</span><span
                class="token punctuation">:</span>
    app <span class="token operator">=</span> Application<span class="token punctuation">(</span><span
                class="token punctuation">[</span><span class="token punctuation">(</span><span
                class="token string">r"/"</span><span class="token punctuation">,</span> IndexHandler<span
                class="token punctuation">)</span><span class="token punctuation">]</span><span
                class="token punctuation">)</span>

    app<span class="token punctuation">.</span>listen<span class="token punctuation">(</span><span class="token number">8000</span><span
                class="token punctuation">)</span>

    IOLoop<span class="token punctuation">.</span>current<span class="token punctuation">(</span><span
                class="token punctuation">)</span><span class="token punctuation">.</span>start<span
                class="token punctuation">(</span><span class="token punctuation">)</span>
<span aria-hidden="true"
      class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre>
</div>
<div class="image-package">
    <div class="image-container" style="max-width: 700px; max-height: 188px;">
        <div class="image-container-fill" style="padding-bottom: 22.17%;"></div>
        <div class="image-view" data-width="848" data-height="188"><img
                data-original-src="//upload-images.jianshu.io/upload_images/6078268-0831167456838eee.png"
                data-original-width="848" data-original-height="188" data-original-format="image/png"
                data-original-filesize="9846" data-image-index="13" style="cursor: zoom-in;" class="image-loading">
        </div>
    </div>
    <div class="image-caption">浏览器显示结果</div>
</div>