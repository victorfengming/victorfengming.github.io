---
title: "python之禅"
subtitle: "python的设计哲学：优雅，简洁。。。"
tags: Python solution interview
---




<div id="cnblogs_post_body" class="blogpost-body ">
    <p><span style="font-family: 'courier new', courier; font-size: 13px;">可以在编译器里面输入如下语句来查看python语言的设计哲学：</span></p>
    <p>&nbsp;</p>
    <div class="cnblogs_code">
        <div class="cnblogs_code_toolbar"><span class="cnblogs_code_copy"><a href="javascript:void(0);"
                                                                             onclick="copyCnblogsCode(this)"
                                                                             title="复制代码"><img
                src="//common.cnblogs.com/images/copycode.gif" alt="复制代码"></a></span></div>
        <pre><span style="color: #008080;"> 1</span> &gt;&gt;&gt; <span style="color: #0000ff;">import</span><span
                style="color: #000000;"> this
</span><span style="color: #008080;"> 2</span> <span style="color: #000000;">The Zen of Python, by Tim Peters
</span><span style="color: #008080;"> 3</span>
<span style="color: #008080;"> 4</span> Beautiful <span style="color: #0000ff;">is</span><span style="color: #000000;"> better than ugly.
</span><span style="color: #008080;"> 5</span> Explicit <span style="color: #0000ff;">is</span><span
                    style="color: #000000;"> better than implicit.
</span><span style="color: #008080;"> 6</span> Simple <span style="color: #0000ff;">is</span><span
                    style="color: #000000;"> better than complex.
</span><span style="color: #008080;"> 7</span> Complex <span style="color: #0000ff;">is</span><span
                    style="color: #000000;"> better than complicated.
</span><span style="color: #008080;"> 8</span> Flat <span style="color: #0000ff;">is</span><span
                    style="color: #000000;"> better than nested.
</span><span style="color: #008080;"> 9</span> Sparse <span style="color: #0000ff;">is</span><span
                    style="color: #000000;"> better than dense.
</span><span style="color: #008080;">10</span> <span style="color: #000000;">Readability counts.
</span><span style="color: #008080;">11</span> Special cases aren<span style="color: #800000;">'</span><span
                    style="color: #800000;">t special enough to break the rules.</span>
<span style="color: #008080;">12</span> <span style="color: #000000;">Although practicality beats purity.
</span><span style="color: #008080;">13</span> Errors should never <span style="color: #0000ff;">pass</span><span
                    style="color: #000000;"> silently.
</span><span style="color: #008080;">14</span> <span style="color: #000000;">Unless explicitly silenced.
</span><span style="color: #008080;">15</span> <span style="color: #000000;">In the face of ambiguity, refuse the temptation to guess.
</span><span style="color: #008080;">16</span> There should be one-- <span style="color: #0000ff;">and</span> preferably only one --<span
                    style="color: #000000;">obvious way to do it.
</span><span style="color: #008080;">17</span> Although that way may <span style="color: #0000ff;">not</span> be obvious at first unless you<span
                    style="color: #800000;">'</span><span style="color: #800000;">re Dutch.</span>
<span style="color: #008080;">18</span> Now <span style="color: #0000ff;">is</span><span style="color: #000000;"> better than never.
</span><span style="color: #008080;">19</span> Although never <span style="color: #0000ff;">is</span> often better than *right*<span
                    style="color: #000000;"> now.
</span><span style="color: #008080;">20</span> If the implementation <span style="color: #0000ff;">is</span> hard to explain, it<span
                    style="color: #800000;">'</span><span style="color: #800000;">s a bad idea.</span>
<span style="color: #008080;">21</span> If the implementation <span style="color: #0000ff;">is</span><span
                    style="color: #000000;"> easy to explain, it may be a good idea.
</span><span style="color: #008080;">22</span> Namespaces are one honking great idea -- let<span
                    style="color: #800000;">'</span><span style="color: #800000;">s do more of those!</span></pre>
        <div class="cnblogs_code_toolbar"><span class="cnblogs_code_copy"><a href="javascript:void(0);"
                                                                             onclick="copyCnblogsCode(this)"
                                                                             title="复制代码"><img
                src="//common.cnblogs.com/images/copycode.gif" alt="复制代码"></a></span></div>
    </div>
    <p>&nbsp;</p>
    <p><span style="font-family: 'courier new', courier; font-size: 13px;">中英文释义如下：</span></p>
    <div class="cnblogs_code">
        <div class="cnblogs_code_toolbar"><span class="cnblogs_code_copy"><a href="javascript:void(0);"
                                                                             onclick="copyCnblogsCode(this)"
                                                                             title="复制代码"><img
                src="//common.cnblogs.com/images/copycode.gif" alt="复制代码"></a></span></div>
        <pre><span style="color: #008080;"> 1</span> Beautiful <span style="color: #0000ff;">is</span><span
                style="color: #000000;"> better than ugly.
</span><span style="color: #008080;"> 2</span> <span style="color: #008000;">#</span><span style="color: #008000;"> 优美胜于丑陋（Python以编写优美的代码为目标）</span>
<span style="color: #008080;"> 3</span> Explicit <span style="color: #0000ff;">is</span><span style="color: #000000;"> better than implicit.
</span><span style="color: #008080;"> 4</span> <span style="color: #008000;">#</span><span style="color: #008000;"> 明了胜于晦涩（优美的代码应当是明了的，命名规范，风格相似） </span>
<span style="color: #008080;"> 5</span> Simple <span style="color: #0000ff;">is</span><span style="color: #000000;"> better than complex.
</span><span style="color: #008080;"> 6</span> <span style="color: #008000;">#</span><span style="color: #008000;"> 简洁胜于复杂（优美的代码应当是简洁的，不要有复杂的内部实现） </span>
<span style="color: #008080;"> 7</span> Complex <span style="color: #0000ff;">is</span><span style="color: #000000;"> better than complicated.
</span><span style="color: #008080;"> 8</span> <span style="color: #008000;">#</span><span style="color: #008000;"> 复杂胜于凌乱（如果复杂不可避免，那代码间也不能有难懂的关系，要保持接口简洁）</span>
<span style="color: #008080;"> 9</span> Flat <span style="color: #0000ff;">is</span><span style="color: #000000;"> better than nested.
</span><span style="color: #008080;">10</span> <span style="color: #008000;">#</span><span style="color: #008000;"> 扁平胜于嵌套（优美的代码应当是扁平的，不能有太多的嵌套） </span>
<span style="color: #008080;">11</span> Sparse <span style="color: #0000ff;">is</span><span style="color: #000000;"> better than dense.
</span><span style="color: #008080;">12</span> <span style="color: #008000;">#</span><span style="color: #008000;"> 间隔胜于紧凑（优美的代码有适当的间隔，不要奢望一行代码解决问题） </span>
<span style="color: #008080;">13</span> <span style="color: #000000;">Readability counts.
</span><span style="color: #008080;">14</span> <span style="color: #008000;">#</span><span style="color: #008000;"> 可读性很重要（优美的代码是可读的） </span>
<span style="color: #008080;">15</span> Special cases aren<span style="color: #800000;">'</span><span
                    style="color: #800000;">t special enough to break the rules.</span>
<span style="color: #008080;">16</span> <span style="color: #000000;">Although practicality beats purity.
</span><span style="color: #008080;">17</span> <span style="color: #008000;">#</span><span style="color: #008000;"> 即便假借特例的实用性之名，也不可违背这些规则（这些规则至高无上） </span>
<span style="color: #008080;">18</span> Errors should never <span style="color: #0000ff;">pass</span><span
                    style="color: #000000;"> silently.
</span><span style="color: #008080;">19</span> <span style="color: #000000;">Unless explicitly silenced.
</span><span style="color: #008080;">20</span> <span style="color: #008000;">#</span><span style="color: #008000;"> 不要包容所有错误，除非你确定需要这样做（精准地捕获异常，不写except:pass风格的代码） </span>
<span style="color: #008080;">21</span> <span style="color: #000000;">In the face of ambiguity, refuse the temptation to guess.
</span><span style="color: #008080;">22</span> <span style="color: #008000;">#</span><span style="color: #008000;"> 当存在多种可能，不要尝试去猜测 </span>
<span style="color: #008080;">23</span> There should be one-- <span style="color: #0000ff;">and</span> preferably only one --<span
                    style="color: #000000;">obvious way to do it.
</span><span style="color: #008080;">24</span> <span style="color: #008000;">#</span><span style="color: #008000;"> 而是尽量找一种，最好是唯一一种明显的解决方案（如果不确定，就用穷举法） </span>
<span style="color: #008080;">25</span> Although that way may <span style="color: #0000ff;">not</span> be obvious at first unless you<span
                    style="color: #800000;">'</span><span style="color: #800000;">re Dutch.</span>
<span style="color: #008080;">26</span> <span style="color: #008000;">#</span><span style="color: #008000;"> 虽然这并不容易，因为你不是 Python 之父（这里的Dutch是指Guido）</span>
<span style="color: #008080;">27</span> Now <span style="color: #0000ff;">is</span><span style="color: #000000;"> better than never.
</span><span style="color: #008080;">28</span> Although never <span style="color: #0000ff;">is</span> often better than *right*<span
                    style="color: #000000;"> now.
</span><span style="color: #008080;">29</span> <span style="color: #008000;">#</span><span style="color: #008000;"> 做也许好过不做，但不假思索就动手还不如不做（动手之前要细思量）</span>
<span style="color: #008080;">30</span> If the implementation <span style="color: #0000ff;">is</span> hard to explain, it<span
                    style="color: #800000;">'</span><span style="color: #800000;">s a bad idea.</span>
<span style="color: #008080;">31</span> If the implementation <span style="color: #0000ff;">is</span><span
                    style="color: #000000;"> easy to explain, it may be a good idea.
</span><span style="color: #008080;">32</span> <span style="color: #008000;">#</span><span style="color: #008000;"> 如果你无法向人描述你的方案，那肯定不是一个好方案；反之亦然（方案测评标准） </span>
<span style="color: #008080;">33</span> Namespaces are one honking great idea -- let<span
                    style="color: #800000;">'</span><span style="color: #800000;">s do more of those!</span>
<span style="color: #008080;">34</span> <span style="color: #008000;">#</span><span style="color: #008000;"> 命名空间是一种绝妙的理念，我们应当多加利用（倡导与号召）</span></pre>
        <div class="cnblogs_code_toolbar"><span class="cnblogs_code_copy"><a href="javascript:void(0);"
                                                                             onclick="copyCnblogsCode(this)"
                                                                             title="复制代码"><img
                src="//common.cnblogs.com/images/copycode.gif" alt="复制代码"></a></span></div>
    </div>
    <p>&nbsp;</p>
    <p><span style="font-family: 'courier new', courier; font-size: 13px;">然后，我尝试了里面的一段demo代码：</span></p>
    <div class="cnblogs_code">
<pre><span style="color: #008080;">1</span> <span style="color: #008000;">#</span><span style="color: #008000;"> coding = utf-8</span><span
        style="color: #008080;">2</span> <span style="color: #0000ff;">print</span> (<span
        style="color: #800000;">"""</span>
<span style="color: #008080;">3</span> <span style="color: #800000;">my name is zhangweigong
</span><span style="color: #008080;">4</span> <span style="color: #800000;">my blogs url is:www.cnblogs.com/imyalost
</span><span style="color: #008080;">5</span> <span style="color: #800000;">life is so short,I need python
</span><span style="color: #008080;">6</span> <span style="color: #800000;">"""</span>)</pre>
    </div>
    <p><span style="font-family: 'courier new', courier; font-size: 13px;">运行结果是可以成功运行的，但打印出来的结果前面，专门提及了python的设计哲学，说明，这段代码是不够简洁高效的。。。</span>
    </p>
    <p><span style="font-family: 'courier new', courier; font-size: 13px;">突然明白一个道理：学习一门编程语言，一定要了解这门语言的特性。。。</span></p>
    <p><span style="font-family: 'courier new', courier; font-size: 13px;">其实做一件事学一门技术也一样（不限于编程语言，虽然编程语言也是一门技术、手段），要了解它的特性，才能更好的使用它，发挥它的作用！！！</span>
    </p>
    <p><span style="font-family: 'courier new', courier; font-size: 13px;">引以为戒啊，少年。。。</span></p>
    <p>&nbsp;</p>
</div>