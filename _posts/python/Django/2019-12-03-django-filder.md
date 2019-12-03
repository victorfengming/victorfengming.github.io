---
title: "Django模板（过滤器）"
subtitle: "django内建的过滤器"
tags: Python solution web django
---



* content
{:toc}


本文转自:https://www.cnblogs.com/qingtianyu2015/p/6064073.html


<div id="cnblogs_post_body" class="blogpost-body ">
    <p>-------------------django内建的过滤器-------------------<br>1、add <br> 使用形式为：{{ value | add: "2"}}<br>
        意义：将value的值增加2</p>
    <p><br>2、addslashes<br> 使用形式为：{{ value | addslashes }}<br> 意义：在value中的引号前增加反斜线</p>
    <p><br>3、capfirst<br> 使用形式为：{{ value | capfirst }}<br> 意义：value的第一个字符转化成大写形式</p>
    <p><br>4、cut<br> 使用形式为：{{ value | cut:arg}}， 例如，如果value是“String with spaces” arg是" "那么输出是"Stringwithspaces"<br>
        意义：从给定value中删除所有arg的值</p>
    <p><br>5、date<br> 使用形式为：：<br> (a) {{ value | date:"D d M Y"
        }}，例如，如果value是一个datetime对象(datetime.datetime.now())那么输出将是字符串"Wed 09 Jan 2008"<br> (b) {{ value | date
        }}，这种形式没有格式化字符串，这时候，格式化字符串会自动采用DATE_FORMAT所设置的形式。<br> 意义：将日期格式数据按照给定的格式输出</p>
    <p><br>6、default<br> 使用形式：{{ value | default: "nothing" }}，例如，如果value是“”，那么输出将是nothing<br>
        意义：如果value的意义是False，那么输出使用缺省值</p>
    <p><br>7、default_if_none<br> 使用形式：{{ value | default_if_none:"nothing" }}，例如，如果value是None，那么输出将是nothing<br>
        意义：如果value是None，那么输出将使用缺省值<br></p>
    <p>8、dictsort<br> 意义：如果value的值是一个字典，那么返回值是按照关键字排序的结果<br> 使用形式：{{ value | dictsort:"name"}}，例如，<br> 如果value是：<br>
        [<br> {'name': 'zed', 'age': 19},<br> {'name': 'amy', 'age': 22},<br> {'name': 'joe', 'age': 31}, ]<br>
        那么，输出是：<br> [<br> {'name': 'amy', 'age': 22},<br> {'name': 'joe', 'age': 31},<br> {'name': 'zed', 'age':
        19}, ]</p>
    <p><br>9、dictsortreversed<br> 意义：如果value的值是一个字典，那么返回值是按照关键字排序的结果的反序<br> 使用形式：与上述(8)完全相同。</p>
    <p><br>10、divisibleby<br> 使用形式：{{ value | divisibleby:arg}}，如果value是21，arg是3，那么输出将是True<br>
        意义：如果value能够被arg整除，那么返回值将是True</p>
    <p><br>11、escape<br> 使用形式：{{ value | escape}}<br> 意义：替换value中的某些字符，以适应HTML格式，包括：<br> &lt; is converted to
        &amp;lt;<br>
        &gt; is converted to &amp;gt;<br> ' (single quote) is converted to &amp;#39;<br> " (double quote) is
        converted to &amp;quot;<br> &amp; is converted to &amp;amp;<br> <br>
        注：escape仅仅在输出的时候才起作用，所以escape不能够用在链式过滤器的中间，<br>他应该总是最后一个过滤器，如果想在链式过滤器的中间使用，那么可以使用force_escape</p>
    <p>12、escapejs<br> 使用形式：{{ value | escapejs }}<br> 意义：替换value中的某些字符，以适应JAVASCRIPT和JSON格式。</p>
    <p><br>13、filesizeformat<br> 使用形式：{{ value | filesizeformat }}<br> 意义：格式化value，使其成为易读的文件大小，例如：13KB，4.1MB等。</p>
    <p><br>14、first<br> 使用形式：{{ value | first }}<br> 意义：返回列表中的第一个Item，例如，如果value是列表['a','b','c']，那么输出将是'a'。<br></p>
    <p>15、floatformat<br> 使用形式：{{ value | floatformat}}或者{{value|floatformat:arg}}，
        arg可以是正数也可以是负数。没有参数的floatformat相当于floatformat:-1</p>
    <p> 1、如果不带arg，那么引擎会四舍五入，同时最多只保留一位小数。<br> 34.23234{{ value|floatformat }}34.234.00000{{ value|floatformat
        }}3434.26000{{ value|floatformat }}34.3<br> <br> 2、如果arg是正数，那么引擎会四舍五入，同时保留arg位的小数。<br> 34.23234{{
        value|floatformat:3 }}34.23234.00000{{ value|floatformat:3 }}34.00034.26000{{ value|floatformat:3 }}34.260
    </p>
    <p> 3、如果arg是负数，那么引擎会四舍五入，如果有小数部分，那么保留arg位小数；否则，则没有任何小数部分。<br> 34.23234{{ value|floatformat:"-3"
        }}34.23234.00000{{ value|floatformat:"-3" }}3434.26000{{ value|floatformat:"-3" }}34.26(16)get_digit<br>
        <br> 使用形式：{{ value | get_digit:"arg"}}，例如，如果value是123456789，arg是2，那么输出是8<br>
        意义：给定一个数字，返回，请求的数字，记住：1代表最右边的数字，如果value不是合法输入，那么会返回所有原有值。</p>
    <p><br>16、iriencode<br> 使用形式：{{value | iriencode}}<br>
        意义：如果value中有非ASCII字符，那么将其进行抓化成URL中适合的编码，如果value已经进行过URLENCODE，<br> 改操作就不会再起作用。</p>
    <p><br>17、join<br> 使用形式：{{ value | join:"arg"}}，如果value是['a','b','c']，arg是'//'那么输出是a//b//c<br>
        意义：使用指定的字符串连接一个list，作用如同python的str.join(list)</p>
    <p><br>18、last<br> 使用形式：{{ value | last }}<br> 意义：返回列表中的最后一个Item</p>
    <p><br>19、length<br> 使用形式：{{ value | length }}<br> 意义：返回value的长度。</p>
    <p><br>20、length_is<br> 使用形式：{{ value | length_is:"arg"}}<br>
        意义：返回True，如果value的长度等于arg的时候，例如：如果value是['a','b','c']，arg是3，那么返回True</p>
    <p><br>21、linebreaks<br> 使用形式：{{value|linebreaks}}<br> 意义：value中的"\n"将被&lt;br/&gt;替代，并且整个value使用&lt;/p&gt;包围起来，从而适和HTML的格式
    </p>
    <p><br>22、linebreaksbr<br> 使用形式：{{value |linebreaksbr}}<br> 意义：value中的"\n"将被&lt;br/&gt;替代</p>
    <p><br>23、linenumbers<br> 使用形式：{{value | linenumbers}}<br> 意义：显示的文本，带有行数。</p>
    <p><br>24、ljust<br> 使用形式：{{value | ljust}}<br> 意义：在一个给定宽度的字段中，左对齐显示value</p>
    <p><br>25、center<br> 使用形式：{{value | center}}<br> 意义：在一个给定宽度的字段中，中心对齐显示value </p>
    <p><br>26、rjust<br> 使用形式：{{value | rjust}}<br> 意义：在一个给定宽度的字段中，右对齐显示value</p>
    <p><br>27、lower<br> 使用形式：{{value | lower}}<br> 意义：将一个字符串转换成小写形式</p>
    <p><br>28、make_list<br> 使用形式：{{value | make_list}}<br> 意义：将value转换成一个list，对于字符串，转换成字符list；对于整数，转换成整数list<br>
        例如value是Joel，那么输出将是[u'J',u'o',u'e',u'l']；value是123，那么输出将是[1,2,3]</p>
    <p><br>29、pluralize<br> 使用形式：{{value | pluralize}}，或者{{value | pluralize:"es"}}，或者{{value |
        pluralize:"y,ies"}}<br> 意义：如果value不是1，则返回一个复数后缀，缺省的后缀是's'</p>
    <p><br>30、random<br> 使用形式：{{value | random}}<br> 意义：从给定的list中返回一个任意的Item</p>
    <p><br>31、removetags<br> 使用形式：{{value | removetags:"tag1 tag2 tag3..."}}<br>
        意义：删除value中tag1,tag2....的标签。例如，如果value是&lt;b&gt;Joel&lt;/b&gt; &lt;button&gt;is&lt;/button&gt; a &lt;span&gt;slug&lt;/span&gt;<br>
        tags是"b span"，那么输出将是：Joel &lt;button&gt;is&lt;/button&gt; a slug</p>
    <p><br>32、safe<br> 使用形式：{{value | safe}}<br> 意义：当系统设置autoescaping打开的时候，该过滤器使得输出不进行escape转换</p>
    <p><br>33、safeseq<br> 与上述safe基本相同，但有一点不同的就是：safe是针对字符串，而safeseq是针对多个字符串组成的sequence</p>
    <p><br>34、slice<br> 使用形式：{{some_list | slice:":2"}}<br> 意义：与python语法中的slice相同，:2表示第一的第二个元素</p>
    <p><br>35、slugify<br> 使用形式：{{value | slugify}}<br> 意义：将value转换成小写形式，同事删除所有分单词字符，并将空格变成横线<br> 例如：如果value是Joel is
        a slug，那么输出将是joel-is-a-slug</p>
    <p><br>36、stringformat<br> 这个不经常用，先不说</p>
    <p><br>37、striptags<br> 使用形式：{{value | striptags}}<br> 意义：删除value中的所有HTML标签</p>
    <p><br>38、time<br> 使用形式：{{value | time:"H:i"}}或者{{value | time}}<br>
        意义：格式化时间输出，如果time后面没有格式化参数，那么输出按照TIME_FORMAT中设置的进行。</p>
    <p><br>39、title<br> 转换一个字符串成为title格式。</p>
    <p><br>40、truncatewords<br> 使用形式：{{value | truncatewords:2}}<br> 意义：将value切成truncatewords指定的单词数目<br>
        例如，如果value是Joel is a slug 那么输出将是：Joel is ...</p>
    <p><br>41、truncatewords_html<br> 使用形式同(39)<br> 意义：truncation点之前如果某个标签打开了，但是没有关闭，那么在truncation点会立即关闭。<br>
        因为这个操作的效率比truncatewords低，所有只有在value是html格式时，才考虑使用。</p>
    <p><br>42、upper<br> 转换一个字符串为大写形式</p>
    <p><br>43、urlencode<br> 将一个字符串进行URLEncode</p>
    <p><br>44、urlize<br> 意义：将一个字符串中的URL转化成可点击的形式。<br> 使用形式：{{ value | urlize }}<br> 例如，如果value是Check out
        www.djangoproject.com，那么输出将是：<br> Check out &lt;a href="http://www.djangoproject.com"&gt;www.djangoproject.com&lt;/a&gt;
    </p>
    <p><br>45、urlizetrunc<br> 使用形式：{{ value | urlizetrunc:15}}<br>
        意义：与(43)相同，但是有一点不同就是现实的链接字符会被truncate成特定的长度，后面以...现实。</p>
    <p><br>46、wordcount<br> 返回字符串中单词的数目</p>
    <p><br>47、wordwrap<br> 使用形式：{{value | wordwrap:5}}<br> 意义：按照指定的长度包装字符串<br> 例如，如果value是Joel is a
        slug，那么输出将会是：<br> Joel<br> is a<br> slug</p>
    <p><br>48、timesince<br> 使用形式：{{value | timesince:arg}}<br> 意义：返回参数arg到value的天数和小时数<br> 例如，如果 blog_date 是一个日期实例表示
        2006-06-01 午夜， 而 comment_date 是一个日期实例表示 2006-06-01 早上8点，<br> 那么 {{ comment_date|timesince:blog_date }} 将返回
        "8 hours".</p>
    <p><br>49、timeuntil<br> 使用形式：{{value | timeuntil}}<br> 意义：与(47)基本相同，一个不同点就是，返回的是value距离当前日期的天数和小时数。</p>
    <p>&nbsp;</p>
</div>
<div id="MySignature"></div>
<div class="clear"></div>
<div id="blog_post_info_block">
    <div id="BlogPostCategory">
        分类:
        <a href="https://www.cnblogs.com/qingtianyu2015/category/917641.html" target="_blank">Django</a></div>


    <div id="blog_post_info">
        <div id="green_channel">
            <a href="javascript:void(0);" id="green_channel_digg"
               onclick="DiggIt(6064073,cb_blogId,1);green_channel_success(this,'谢谢推荐！');">好文要顶</a>
            <a id="green_channel_follow" onclick="follow('707020fa-9257-e411-b908-9dcfd8948a71');"
               href="javascript:void(0);">关注我</a>
            <a id="green_channel_favorite" onclick="AddToWz(cb_entryId);return false;"
               href="javascript:void(0);">收藏该文</a>
            <a id="green_channel_weibo" href="javascript:void(0);" title="分享至新浪微博" onclick="ShareToTsina()"><img
                    src="https://common.cnblogs.com/images/icon_weibo_24.png" alt=""></a>
            <a id="green_channel_wechat" href="javascript:void(0);" title="分享至微信" onclick="shareOnWechat()"><img
                    src="https://common.cnblogs.com/images/wechat.png" alt=""></a>
        </div>
        <div id="author_profile">
            <div id="author_profile_info" class="author_profile_info">
                <a href="https://home.cnblogs.com/u/qingtianyu2015/" target="_blank"><img
                        src="https://pic.cnblogs.com/face/683233/20160905233823.png" class="author_avatar"
                        alt=""></a>
                <div id="author_profile_detail" class="author_profile_info">
                    <a href="https://home.cnblogs.com/u/qingtianyu2015/">cloud_wh</a><br>
                    <a href="https://home.cnblogs.com/u/qingtianyu2015/followees/">关注 - 10</a><br>
                    <a href="https://home.cnblogs.com/u/qingtianyu2015/followers/">粉丝 - 23</a>
                </div>
            </div>
            <div class="clear"></div>
            <div id="author_profile_honor"></div>
            <div id="author_profile_follow">
                <a href="javascript:void(0);"
                   onclick="follow('707020fa-9257-e411-b908-9dcfd8948a71');return false;">+加关注</a>
            </div>
        </div>
        <div id="div_digg">
            <div class="diggit" onclick="votePost(6064073,'Digg')">
                <span class="diggnum" id="digg_count">0</span>
            </div>
            <div class="buryit" onclick="votePost(6064073,'Bury')">
                <span class="burynum" id="bury_count">0</span>
            </div>
            <div class="clear"></div>
            <div class="diggword" id="digg_tips">
            </div>
        </div>

        <script type="text/javascript">
            currentDiggType = 0;
        </script>
    </div>
    <div class="clear"></div>
    <div id="post_next_prev">

        <a href="https://www.cnblogs.com/qingtianyu2015/p/6064067.html" class="p_n_p_prefix">« </a> 上一篇： <a
            href="https://www.cnblogs.com/qingtianyu2015/p/6064067.html"
            title="发布于 2016-11-15 00:12">django框架(Model)</a>
        <br>
        <a href="https://www.cnblogs.com/qingtianyu2015/p/6064076.html" class="p_n_p_prefix">» </a> 下一篇： <a
            href="https://www.cnblogs.com/qingtianyu2015/p/6064076.html"
            title="发布于 2016-11-15 00:15">django富文本编辑器</a>

    </div>
</div>
