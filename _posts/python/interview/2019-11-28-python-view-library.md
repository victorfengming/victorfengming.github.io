---
title: "Python可视化工具介绍"
subtitle: "帮你找到合适的库"
tags: Python solution interview
---

原文链接:https://www.jianshu.com/p/62027a72a794


<p>Python有很多可视化工具，大体上可以分为基于matplotlib的工具库和基于JS的工具库。<br>
    有如此丰富的选择是幸福的，无论你要画什么图，都能找到相对的库。但与此同时，弄清楚使用哪个工具更合适可能非常具有挑战性。本文对常用的一些可视化工具进行介绍，并说明它们之间的主要区别。</p>
<br>
<div class="image-package">
    <div class="image-container" style="max-width: 700px; max-height: 340px; background-color: transparent;">
        <div class="image-container-fill" style="padding-bottom: 48.46%;"></div>
        <div class="image-view" data-width="3048" data-height="1477"><img
                data-original-src="//upload-images.jianshu.io/upload_images/1434448-5ee38b5bb8c7f4bb.png"
                data-original-width="3048" data-original-height="1477" data-original-format="image/png"
                data-original-filesize="482416" class="" data-image-index="0" style="cursor: zoom-in;"
                src="//upload-images.jianshu.io/upload_images/1434448-5ee38b5bb8c7f4bb.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp">
        </div>
    </div>
    <div class="image-caption">可视化工具一览</div>
</div>
<h4>基于matplotlib的可视化工具</h4>
<p>在介绍基于matplotlib的工具之前， 首先介绍一些matplotlib库。正如《<a
        href="https://links.jianshu.com/go?to=https%3A%2F%2Fpbpython.com%2Fvisualization-tools-1.html"
        target="_blank">Overview of Python Visualization Tools</a>》中所介绍的——“<a
        href="https://links.jianshu.com/go?to=http%3A%2F%2Fmatplotlib.org%2F" target="_blank">Matplotlib</a> is the
    grandfather of python visualization
    packages”——matplotlib是第一个python可视化库，也是使用最广泛的可视化工具之一。它参考MATLAB对低级命令进行了封装，有着非常强大的功能，能绘制绝大多数常用的图，同时支持非常丰富的配置。（参见官网的<a
            href="https://links.jianshu.com/go?to=https%3A%2F%2Fmatplotlib.org%2Fgallery%2Findex.html"
            target="_blank">matplotlib图例</a>）<br>
    但随之而来的是复杂性，往往需要相对较多的代码才能得到想要的效果。加之其默认的绘图风格过于简约复古，想要对其美化更是要花些功夫。</p>
<ul>
    <li>Seaborn<br>
        <a href="https://links.jianshu.com/go?to=http%3A%2F%2Fstanford.edu%2F%7Emwaskom%2Fsoftware%2Fseaborn%2F"
           target="_blank">Seaborn</a>是基于matplotlib的可视化库。它提供了一些更美观的配置选项，同时可以用更简单的代码来创建复杂的图。Seaborn封装了很多统计绘图函数，使得在做数据分析时非常方便。<br>
        <div class="image-package">
            <div class="image-container"
                 style="max-width: 700px; max-height: 395px; background-color: transparent;">
                <div class="image-container-fill" style="padding-bottom: 56.330000000000005%;"></div>
                <div class="image-view" data-width="1358" data-height="765"><img
                        data-original-src="//upload-images.jianshu.io/upload_images/1434448-cc70023b4f2a8ef7.jpg"
                        data-original-width="1358" data-original-height="765" data-original-format="image/jpeg"
                        data-original-filesize="118482" class="" data-image-index="1" style="cursor: zoom-in;"
                        src="//upload-images.jianshu.io/upload_images/1434448-cc70023b4f2a8ef7.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp">
                </div>
            </div>
            <div class="image-caption">seaborn图例</div>
        </div>
    </li>
    <li>Pandas<br>
        Pandas基于matplotlib也提供较为简单的API绘制图形，如pandas.tools.plotting。其使用pandas
        DataFrame进行绘图，这使得可以使用Pandas从分析到绘图无缝衔接。不过想要对图进行进一步的调整，就需要跳入matplotlib进行设置，而无法完全通过pandas进行操作。
    </li>
    <li>ggplot<br>
        与seaborn类似，ggplot也基于matplotlilb，旨在以一种简单的方式改善matplotlib可视化的美化问题。与seaborn的不同之处在于它是
        ggplot2为R语言准备的一个端口，所以它的一些api不是基于python而是基于R语言的。ggoplot利用了<a
                href="https://links.jianshu.com/go?to=https%3A%2F%2Fwww.springer.com%2Fgp%2Fbook%2F9780387245447"
                target="_blank">图形语法</a>的概念，是一种不同的绘图逻辑。
    </li>
</ul>
<p>
    在进行可视化时通常涉及到地理信息的处理。除了常规的折线，柱状图之外，空间分布也是数据可视化中非常重要的一项。Python中一些库则专门处理涉及地理信息图形的工作，比如Basemap，Cartopy等。此外，geopandas扩展了pandas的绘图模块以支持地图和几何操作，并且相比Basemap和Cartopy处理效率相对更高，处理步骤更简单一些。</p>
<h4>基于JS的可视化工具</h4>
<p>基于matplotlib的可视化工具存在一个很明显的缺点，是其绘图处理速度低，尤其是在实时交互和图形快速更新等方面<br>
    对于图基于JS开发的可视化库相对于matpltolib来说，<strong>交互可视化</strong>正是它的优势。</p>
<ul>
    <li>Bokeh和HoloViews<br>
        Bokeh和HoloViews是开源的交互式可视化库。它们都是属于PyViz生态（可参见<a
                href="https://links.jianshu.com/go?to=https%3A%2F%2Fzhuanlan.zhihu.com%2Fp%2F58797814"
                target="_blank">PyViz生态</a>）。<br>
        HoloViews用于即时可视化数据的声明对象，从方便的高级规范构建Bokeh图<br>
        Bokeh致力于在现代Web浏览器中生成可视化效果。它旨在进行交互式Web可视化。
    </li>
    <li>plotly<br>
        <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fplot.ly%2F" target="_blank">plotly</a>区别于其他工具，是企业级分析和可视化的在线工具。其基于开源的可视化框架Dash，并提供了很多语言(比如MATLAB，Python，R等)的接口，并与pandas无缝集成。
    </li>
    <li>Cufflinks<br>
        Cufflinks将Plotly直接绑定到pandas数据帧。结合了Pandas的灵活性，比Plotly更有效，语法甚至比plotly简单。使用plotly的Python库，您可以使用DataFrame的系列和索引来描述图形，但是使用Cufflinks可以直接绘制它。
    </li>
    <li>GeoViews<br>
        <a href="https://links.jianshu.com/go?to=http%3A%2F%2Fgeoviews.org%2Findex.html"
           target="_blank">GeoViews</a>同样是PyViz的产品，专门用于可视化的地理数据，可以与HoloViews对象混合和匹配。<br>
        <div class="image-package">
            <div class="image-container"
                 style="max-width: 700px; max-height: 440px; background-color: transparent;">
                <div class="image-container-fill" style="padding-bottom: 62.74999999999999%;"></div>
                <div class="image-view" data-width="1243" data-height="780"><img
                        data-original-src="//upload-images.jianshu.io/upload_images/1434448-435b1e9217cfbbde.jpg"
                        data-original-width="1243" data-original-height="780" data-original-format="image/jpeg"
                        data-original-filesize="125059" class="" data-image-index="2" style="cursor: zoom-in;"
                        src="//upload-images.jianshu.io/upload_images/1434448-435b1e9217cfbbde.jpg?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp">
                </div>
            </div>
            <div class="image-caption">GeoViews样例</div>
        </div>
    </li>
    <li>Folium<br>
        Folium是另一个用于绘制空间数据的“神库”，建立在Python生态系统的数据优势和Leaflet.js库的映射优势之上。你可以在python中操作数据，然后通过folium在Leaflet地图中将其可视化。
    </li>
    <li>Altair<br>
        <a href="https://links.jianshu.com/go?to=https%3A%2F%2Faltair-viz.github.io%2F%23"
           target="_blank">Altair</a>类似Seaborn用于<strong>统计可视化</strong>。是一种声明性统计可视化库，是JavaScript的高级可视化库Vega-Lite的包装器。Altair的API也是基于图形语法的，数据围绕Pandas
        Dataframe构建。
    </li>
</ul>
<p><br></p>
<h4>总结</h4>
<p>根据具体的需要选择更合适的工具，对常见的一些工具库，可以作如下总结。</p>
<ul>
    <li>对于没有交互需求的图，可以使用基于matplotlib的工具<br>
        对于<strong>简单的图表绘制</strong>任务，直接使用Pandas是非常方便的。但在对图进行定制化操作是需要使用matplotlib来实现。<br>
        对于较为复杂的可视化修以及统计分析需求，Seaborn 有更简便的实现，同时有很好的美化功能。但仍需要 matplotlib 的知识来调整。ggplot也是不错的选择。<br>
        对地理空间的可视化需求，则考虑Basemap/Cartopy/geopandas。
    </li>
    <li>对于交互可视化，则基于JS的工具有很好的性能<br>
        如果需要建立可视化服务器，bokeh 将是一个强大的工具。并用GeoViews来解决地理可视化的需求。<br>
        Plotly可以创建最具互动性的图表。可以离线保存，并创建非常丰富的基于web的可视化图表。<br>
        对有分析需求的任务可以考虑使用Altair。
    </li>
</ul>
<p><br><br>
    参考：<br>
    <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fpbpython.com%2Fvisualization-tools-1.html"
       target="_blank">Overview of Python Visualization Tools</a><br>
    <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fcloud.tencent.com%2Fdeveloper%2Farticle%2F1471394"
       target="_blank">Python可视化工具概览</a><br>
    <a href="https://links.jianshu.com/go?to=http%3A%2F%2Fseaborn.pydata.org%2Ftutorial.html"
       target="_blank">seaborn官网</a><br>
    <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmatplotlib.org%2F" target="_blank">matplotlib官网</a><br>
    <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fplot.ly%2F" target="_blank">plotly官网</a></p>