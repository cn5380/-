---




---



[TOC]



# HTML

## 网络传输三大基石

三大基石：URL， HTTP协议， HTML

URL：Internet上的每一个网页都具有一个唯一的名称标识，通常称之为URL（Uniform Resource Locator,统一资源定位器）。它是www的统一资源定位标志，简单地说URL就是web地址，俗称“网址”。

HTTP协议：http协议属于应用层协议，是建立在tcp协议的基础上的，http协议以客户端请求和服务端应答为标准，浏览器通常为客户端，而web服务器称之为服务端；客户端打开任意一个端口向服务端的指定端口发起http请求，首先是发起tcp三次握手，tcp三次握手的目的是建立可靠的数据连接通道，tcp三次握手建立完毕，进行http数据交互，

HTML： HTML称之为超文本标记语言。

![image-20221116203247269](/Users/rain/Library/Application Support/typora-user-images/image-20221116203247269.png)



## 什么是HTML？

```
- HTML 是用来描述网页的一种语言。
- HTML 不是一种编程语言，而是一种标记语言(标记语言是一套标记标签)
- HTML 使用标记标签来描述网页
- HTML 文档包含了HTML 标签及文本内容
- HTML文档也叫做 web 页面
```

【1】HTML 指的是超文本标记语言: HyperText Markup Language

超文本：

```
	普通人VS 超人 （比普通的人厉害）
​	普通的文本 VS 超级文本（比普通的文本厉害）
```

标记：

```
	标记 = 标签
​	标签： <html> <body> <head>	由尖括号包围起来的关键词
  		分类：双标记标签/封闭类型标签。<p> </p>   单标记标签/非封闭类型标签		<br/>
```

语言： HTML是一个描述网页的语言



【2】HTML的作用：

学习HTML就是学习各种各样的标签，然后组成一个页面，这个页面可以被浏览器解析，解析完以后可以在浏览器中讲页面进行展示。



## HTML 的标准结构

【1】先用普通文本新建一个文本，将文本的后缀改为.html结尾。

【2】编辑：标准结构：

```html
<html>

		<head></head>
		<body>
			this is my first html....
		</body>>
		
</html>
```

【3】运行界面：让浏览器解析： 直接用浏览器将文件打开即可。

![image-20221116204846855](/Users/rain/Library/Application Support/typora-user-images/image-20221116204846855.png)

建议：使用谷歌浏览器



## HTML的标签的使用

### Html, head, body

html文档标准结构：

```
<html>
    <head>...</head>
    <body>...</body>
</html>
```

【1】html标签

此元素可告知浏览器其自身是一个 HTML 文档。

<html> 与 </html> 标签限定了文档的开始点和结束点，在它们之间是文档的头部和主体。正如您所了解的那样，文档的头部由 [ 标签](https://www.w3school.com.cn/tags/tag_head.asp)定义，而主体由 [ 标签](https://www.w3school.com.cn/tags/tag_body.asp)定义。

【2】head标签 — 里面放的是页面的配置信息

 <head> 标签用于定义文档的头部，它是所有头部元素的容器。<head> 中的元素可以引用脚本、指示浏览器在哪里找到样式表、提供元信息等等。

文档的头部描述了文档的各种属性和信息，包括文档的标题、在 Web 中的位置以及和其他文档的关系等。绝大多数文档头部包含的数据都不会真正作为内容显示给读者。

```
head包含标签：
meta,title,link,base,script等常用标签。
head包含的标签说明：
title是网页唯一标题标签 -title标签
base是网页默认打开方式声明标签base
link是一个链接标签，包括外部css文件引用、js文件引用、favicon.ico图标引用等作用link介绍
meta包含广泛的内容标签，如网页关键字、网页介绍、作者、网页编码、robots、自动跳转等声明及说明标签。 meta介绍
script是引入外部js文件作用
style直接嵌入网页的js或css文件标签。
标签(Tag):head
```

【3】body标签 — 里面放的就是页面上展示出来的内容

body 元素定义文档的主体。

body 元素包含文档的所有内容（比如文本、超链接、图像、表格和列表等等。）



### head可用标签

代码：

```html
<html>

<!-- 这是一个注释，注释的快捷键是ctrl+shift+/, MAC是command+/-->
<!--  
    head标签中： 放入： 页面的配置信息
    可以加入：
    <title>, <meta>, <link>, <style>, <script>, <base>
-->

<head>
    <!-- 页面标题 -->
    <title> 百度一下，你就知道 </title>
    <!-- 设置页面的编码，防止乱码现象
        利用meta标签，
        character="utf-8" 这是属性，以建值对的形式给出 k=v, a=b
        告诉浏览器用utf-8来解析这个html文档
    -->
    <meta charset="utf-8" /> <!-- 简写-->
    <!-- 繁写形式：（了解）-->
    <!-- <meta http-equiv="content-type" content="text/html;charset=utf-8"> -->
    <!-- <meta http-equiv="refresh" content="3;https://www.baidu.com" /> -->
    <!-- 页面作者 -->
    <meta name="author" content="msb;12451@qq.com" />
    <!-- 设置页面搜索的关键字 -->
    <meta name="keywords" content="马士兵教育;线上培训;架构师课程" />
    <!-- 页面描述 -->
    <meta name="description" content="马士兵教育详情页" />

    <!-- link标签引入外部资源  -->
    <link rel="shortcut icon" href="https://www.baidu.com/favicon.ico" type="image/x-icon" />
</head>

<body>
    <!--  body标签：放入：页面展示的内容
     -->
    this is the main html!
</body>

</html>
```



### body中可用标签

#### 文本标签

```html
**
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>文本标签</title>
</head>

<body>
    <!-- 文本标签 -->
    <!-- 下面的文字就是普通的文本，文本编辑器中的任何效果，都不影响也页面：比如空格，换行 都不影响页面
        页面想要实现效果，必须通过标签来实现 -->
    媒体：为人父母，要不要“持证上网”？
    媒体：为人父母，要不要“持证上网”？
    媒体：为人父母，要不要“持证上网”？
    媒体：为人父母，要不要“持证上网”？
    <!-- 标题标签 
         h1-h6字号逐渐变小，每个标题独占一行，自带换行效果
         h7之后字号都属于无效标签，但是浏览器也不会报错，而是以普通文本的形式进行展现
        -->
    <h1> 媒体：为人父母，要不要“持证上网”？ </h1>
    <h2> 媒体：为人父母，要不要“持证上网”？ </h2>
    <h3> 媒体：为人父母，要不要“持证上网”？ </h3>
    <h4> 媒体：为人父母，要不要“持证上网”？ </h4>
    <h5> 媒体：为人父母，要不要“持证上网”？ </h5>
    <h6> 媒体：为人父母，要不要“持证上网”？ </h6>
    <h7> 媒体：为人父母，要不要“持证上网”？ </h7>
    <h8> 媒体：为人父母，要不要“持证上网”？ </h8>
    <!-- 横线标签
         width: 设置宽度
                300 px:固定宽度
                30%: 页面宽度的百分比，会随着页面宽度的变化而变化
         align: 设置位置 left, center, right 默认不写的话就是center居中效果
         -->
    <hr width="300px" ,align="center" />
    <hr width="30%" ,align="center" />

    <!-- 段落标签：
         段落效果：段落中文字自动换行，段落和段落之间有空行 -->
    <p> &nbsp; &nbsp; &nbsp; &nbsp;
        &nbsp;&nbsp;11月17日下午，国务院联防联控机制举行新闻发布会，主题为“不折不扣，科学精准落实疫情防控优化措施”。文化和旅游部、国家卫生健康委、国家疾控局有关负责同志和中国疾控中心专家出席发布会，并回答媒体提问。
    </p>
    <p> &nbsp; &nbsp; &pound;&pound;&cent;
        &pound;11月17日下午，国务院联防联控机制举行新闻发布会，主题为“不折不扣，科学精准落实疫情防控优化措施”。文化和旅游部、国家卫生健康委、国家疾控局有关负责同志和中国疾控中心专家出席发布会，并回答媒体提问。
    </p>
    <!-- 加粗倾斜下划线 -->
    <b> 急促气垫单反 </b>
    <i> 倾斜</i>
    <u> 下划线 </u>
    <i><u><b> 加粗倾泻下户线</b></u></i>

    <!-- 预编译效果，在页面上显示原样效果 -->
    <pre>
        public static void main(String[] args){
        Sysout.out.println("hello world！");
        }
    </pre>

    <!-- 换行 -->
    国务院联防联控机制举行新闻<br />发布会，主题为“不折不扣，科

    <!-- 一箭穿心 -->
    <br /> <del> 你好 你不好</del>

    <!-- 字体标签 -->
    <font color="coral" size="5" face="楷体"> 国务院联防联控机制举行新闻发布会，主题为“不折不扣，科</font>
</body>

</html>
```



##### 实体字符

注意：实体名称对大小写敏感

![image-20221117192514455](/Users/rain/Library/Application Support/typora-user-images/image-20221117192514455.png)



#### 多媒体标签

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>多媒体标签</title>
</head>

<body>
    <!-- 图片 
        src:引入图片的位置 
            引入本地资源
            引入网络资源
        width:设置宽度
        height：设置高度
        注意：一般高度和宽度只需要设置一个就可以了另一个会按照比例自动生成
        title：鼠标悬浮在图片上的时候的提示语，默认情况(没有设置alt属性) 图片如果加载失败那么提示语也是title
        alt: 图片加载失败的提示语
    -->
    <img src="https://pg-ad-b1.ws.126.net/yixiao/31901/5b727f2c96b35ad953c7bc8a9b905c6f.jpg" width="500px"
        height="300px" />
    <!-- 音频 -->
    <embed src="" />
    <!-- 视频 -->
    <br />
    <embed
        src="https://vd3.bdstatic.com/mda-nkgc9y8hgug7q20w/sc/cae_h264/1668676655524377528/mda-nkgc9y8hgug7q20w.mp4?v_from_s=hkapp-haokan-hbe&auth_key=1668687581-0-0-d8cafed8d74155d22c7c763d3fa24efe&bcevod_channel=searchbox_feed&pd=1&cd=0&pt=3&logid=2981136533&vid=9960172724520758867&abtest=104959_1-105568_2&klogid=2981136533 " />
</body>

</html>
```



#### 超链接标签

超级链接简单来讲，就是指按内容链接。

超级链接在本质上属于一个[网页](https://baike.baidu.com/item/网页/99347?fromModule=lemma_inlink)的一部分，它是一种允许我们同其他网页或站点之间进行连接的[元素](https://baike.baidu.com/item/元素/9563223?fromModule=lemma_inlink)。各个网页[链接](https://baike.baidu.com/item/链接/2665501?fromModule=lemma_inlink)在一起后，才能真正构成一个[网站](https://baike.baidu.com/item/网站/155722?fromModule=lemma_inlink)。所谓的超链接是指从一个网页指向一个目标的连接关系，这个目标可以是另一个网页，也可以是相同网页上的不同位置，还可以是一个图片，一个电子邮件地址，一个文件，甚至是一个应用程序。而在一个网页中用来超链接的对象，可以是一段文本或者是一个图片。当浏览者单击已经链接的文字或图片后，链接目标将显示在[浏览器](https://baike.baidu.com/item/浏览器/213911?fromModule=lemma_inlink)上，并且根据目标的类型来打开或运行。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>超链接标签</title>
</head>

<body>
    <!-- 这是一个超链接标签 
        href:控制跳转的目标位置
        target:_self 在自身页面打开，_blank:新建立一个标签打开
    -->
    <a href="文本标签.html"> 这是一个超链接01</a>
    <a href=""> 这是一个超链接02</a>
    <a href="多媒体标签.html"> 这是一个超链接03</a>
    <a href="https:www.baidu.com" target="_self"> 这是一个超链接04</a> <!-- 跳转到网络资源-->
    <a href="https:www.baidu.com" target="_blank"> 这是一个超链接05</a>

    <a href="https:www.baidu.com" target="_blank"> <img
            src="https://www.baidu.com/img/PCtm_d9c8750bed0b3c7d089fa7d55720d6cf.png">
    </a>
</body>

</html>
```



##### 设置锚点

应用场合：当一个页面太长的时候，就需要设置锚点，然后在同一个页面的不同位置之间的跳转。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <a name="1F"> </a>
    <h1>手机</h1>
    <p>苹果</p>
    <p>苹果</p>
    <p>苹果</p>
    <p>苹果</p>
    <p>苹果</p>
    <p>苹果</p>
    <p>苹果</p>
    <p>苹果</p>
    <p>苹果</p>
    <p>苹果</p>
    <p>苹果</p>
    <p>苹果</p>
    <p>苹果</p>
    <p>苹果</p>
    <p>苹果</p>
    <a name="2F"> </a>
    <h1>化妆品</h1>
    <p>发地位</p>
    <p>发地位</p>
    <p>发地位</p>
    <p>发地位</p>
    <p>发地位</p>
    <p>发地位</p>
    <p>发地位</p>
    <p>发地位</p>
    <a name="3F"> </a>
    <h1>食品</h1>
    <p> 面</p>
    <p> 面</p>
    <p> 面</p>
    <p> 面</p>
    <p> 面</p>
    <p> 面</p>
    <p> 面</p>
    <p> 面</p>
    <a href="">手机</a>
    <a href="">化妆品</a>
    <a href="#3F">食品</a>
</body>

</html>
```



#### 列表标签

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <title>列表标签</title>
</head>

<body>
    <!-- 无序列表 -->
    <!-- type: 可以设置列表前图标的样式 type="square" 
         如果想要更换图标样式，需要借助CSS样式 style="list-style:url(act.jpg);"-->
    <h1>起床以后要做的事</h1>
    <ul type="square">
        <li>睁开眼</li>
        <li>穿衣服</li>
        <li>上厕所</li>
        <li>吃早饭</li>
        <li>打篮球</li>
        <li>练习时长两年半</li>
    </ul>
    <!-- 有序列表 -->
    <!-- type：可以设置列表的序号：1，a, I, i 
         start: 可以设置起始标号 -->
    <h1>JAVA学习顺序</h1>
    <ol type="I" start="4">
        <li>JAVASE</li>
        <li>数据库</li>
        <li>HTML</li>
        <li>CSS</li>
        <li>JAVAEE</li>

    </ol>
</body>
</html>
```



#### 表格标签

应用场合：在页面布局很规整的时候，可能利用的就是表格。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>表格标签</title>
</head>

<body>
    <!--  表格： 4行5列 
        table: 表格
        tr: 行 
        td: 单元格 
        默认情况下表格是没有边框的，通过属性来修饰的 
        border: 设置边框大小 
        cellspacing: 设置单元格和边框之间的空隙 
        align="center": 设置单元格居中
        background 设置背景图片 background="img/123.png"-->

    <table border="1px" cellspacing="0px" width="400px" height="300px" bgcolor="darkseagreen">
        <tr bgcolor="bisque">
            <th>学号</th>
            <th>班级</th>
            <th>姓名</th>
            <th>年龄</th>
        </tr>
        <tr>
            <td align="center">101</td>
            <td>1班</td>
            <td>李丽</td>
            <td>27</td>
        </tr>
        <tr>
            <td>102</td>
            <td>2班</td>
            <td>废物</td>
            <td rowspan="3">19</td>
        </tr>
        <tr>
            <td>104</td>
            <td colspan="2" align="center">3班</td>
            <td>网舞</td>

        </tr>
        <tr>
            <td>105</td>
            <td>2班</td>
            <td>章三</td>

        </tr>
    </table>
</body>
</html>
```

效果：

![image-20221130145505322](/Users/rain/Library/Application Support/typora-user-images/image-20221130145505322.png)

------



## 框架

### 内嵌框架

内嵌[框架](https://so.csdn.net/so/search?q=框架&spm=1001.2101.3001.7020)是用于在网页中嵌入一个网页并让它在网页中显示。

添加内嵌框架的语法: <iframe src=" URL "></iframe>    

URL 指定独立网页的路径.

案例：

展示图书：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>展示图书</title>
</head>

<body>
    <iframe src="书籍导航页面.html " height="700px"></iframe>
    <!-- 内嵌框架 -->
    <iframe name="iframe_my" width="50%" height="700px" src="默认展示网页.html"></iframe>
</body>

</html>
```

书籍展示页面：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>展示图书</title>
</head>

<body>

    <!-- 内嵌框架 -->
    <iframe name="iframe_my" width="500px" height="500px"></iframe>

</body>

</html>
```

左侧导航页面：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>展示图书</title>
</head>

<body>
    <h1>我喜欢的图书展示</h1>
    <!-- 无序列表 -->
    <ul>
        <li>
            <a href="img/三国演义.png" target="iframe_my">三国演义</a>
        </li>
        <li>
            <a href="img/西游记.png" target="iframe_my">西游记</a>
        </li>
        <li>
            <a href="img/红楼梦.png" target="iframe_my">红楼梦</a>
        </li>
        <li>
            <a href="img/水浒传.png" target="iframe_my">水浒传</a>
        </li>
    </ul>

</body>

</html>
```



#### 练习：邮箱

![image-20221201212444616](/Users/rain/Library/Application Support/typora-user-images/image-20221201212444616.png)

![image-20221201212459393](/Users/rain/Library/Application Support/typora-user-images/image-20221201212459393.png)

![image-20221201212518269](/Users/rain/Library/Application Support/typora-user-images/image-20221201212518269.png)

![image-20221201212533117](/Users/rain/Library/Application Support/typora-user-images/image-20221201212533117.png)



#### 框架集合

frameset元素可定义一个框架集，它被用来组织多个窗口（框架），每个框架村有独立的文档，在其最简单的应用中，frameset元素仅仅会规定在框架集中存在多少列或多少行，必须使用cols或者rows属性。

案例：

首页：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

</head>
<!-- 框架集合：和body是并列的概念，不要将框架集合放进body中 -->
<frameset rows="20%,*,30%">
    <!-- 上 -->
    <frame />

    <!-- 中 -->
    <frameset cols="30%,45%,*">
        <frame />
        <frame src="/Users/rain/Desktop/Pragom/HTML&CSS/showBooks/img/水浒传.png" />
        <frame src="index.html" />
    </frameset>

    <!-- 下 -->
    <frameset cols="50%,*">
        <frame />
        <frame />
    </frameset>
</frameset>

</html>
```



## form表单

HTML表单是用户和web站点或应用程序之间交互的主要内容之一。它们允许用户将数据发送到web站点。大多数情况下，数据被发送到web服务器，但是web页面也可以自己拦截它并使用它；

- HTML表单是由一个或多个小部件组成的。这些小部件可以是文本字段(单行或多行)、选择框、按钮、复选框或单选按钮；
- HTML表单和常规HTML文档的主要区别在于，大多数情况下，表单收集的数据被发送到web服务器；

![image-20221202165447302](/Users/rain/Library/Application Support/typora-user-images/image-20221202165447302.png)

案例：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>

<body>
    <!-- 定义from表单 ：from表单会采集包含的有效数据，提交到后端，进行交互-->
    <!-- 
        【1】
        地址栏信息：
        file:///Users/rain/Desktop/Pragom/HTML&CSS/From%E8%A1%A8%E5%8D%95/aa?username=zzhang46&pwd=ddd

        ?之前是提交的资源的目标地址
        ？之后是提交的具体的内容

        ？之前的内容：
        http: 信息交互遵照http协议
        127.0.0.1:代表本机的IP地址
        8020:代表内置服务器的端口号
        From%E8%A1%A8%E5%8D%95：值的是你的项目名字，使用HTML编码
        PS：浏览器的地址是不支持中文的，都会转成编码传送，如果你在地址栏看到中文，只是当前的那个浏览器给你一个有好的显示画面
        PS：可以使用在线解析工具查看：urlencode
        aa:目标资源 --- 去当前项目下找aa


        ？之后的内容：
        username=zzhang46&pwd=ddd
        我们写的文本框，密码框位等必须加入一个属性：name
        然后name属性和具体录入的信息会拼成一个键值对的形式
        多个键值对之间，用&连接

        PS：只有写在表单中的内容才会被提交

        【2】method 属性：默认情况下不屑method属性的时候相当于method="get"
        get方式：提交数据可见，安全，提交数据有限制，效率高
    
        post方式：提交数据不可见，不安全。提交数据长度没有限制，效率低

     -->
    <form action="aa" method="post">
        用户名：<input type="text" name="username" /><br />
        密码： <input type="password" name="pwd" /><br />

        <!-- 提交按钮 -->
        <input type="submit" /><br />

    </form>
    用户名2: <input type="text" name="username2" />
</body>

</html>
```



### 模拟百度搜索

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <title>百度一下，你就知道</title>
    <link rel="shortcut icon" href="http:www.baidu.com/favicon.ico" type="image/x-icon" />

</head>

<body>
    <form action="https://www.baidu.com/s" method="get">
        <!-- 文本框 -->
        <input type="text" name="wd" />
        <!-- 搜索按钮 -->
        <input type="submit" name="百度一下" />
    </form>
</body>

</html>
```



### 表单元素

form中可以放入可放入的标签，就是表单元素。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>

<body>
    <form action="dddd" method="get">
        <!-- 表单元素 -->
        <!-- 文本框 ：
            input标签使用很广泛，通过type属性的不同值，来表现不同的状态。
            type="text",  文本框，里面文字可见
            表单元素必须有一个属性： name , 有了name才可以提交数据，才可以采集数据
            然后提交的时候会以键值对的形式拼在一起。
            value: 就是文本框中的具体内容
            键值对：name=value 形式
            如果value提前写好，那么默认效果就是value中内容
            一般默认提示语：用placeholder属性，不会用value-- value 只是文本框中的值，

            readonly只读：只是不能修改，但是其他操作都可以，可以正常提交
            disabled禁用：完全不用，不能正常提交

            写法：
                readonly="readonly"
                readonly
                readonly="true"
        -->
        <input type="text" name="uname" placeholder="请录入身份证信息" />
        <input type="text" name="uname2" value="123123" readonly="true" />
        <input type="text" name="uname3" value="47y57323" readonly="disabled" />

        <!-- 密码框 -->
        <input type="password" name="pwd" />
        <!-- 单选按钮 
            注意：一组单选按钮，必须通过name属性来控制，让他们在一个分组中，然后在一个分组里选一个，
            正常状态下，提交数据为：gender=on, 后台不能区分你提交的数据
            不同的选项的value值要控制不同，这样后台接收就可以区分了

            默认选中：checked="checked"
        -->
        性别：
        <input type="radio" name="gender" value="1" checked="checked" />男
        <input type="radio" name="gender" value="0" />女

        <!-- 多选按钮 
            必须通过name属性来控制，让它们在一个分组中，然后在一个分组中选择多个，不同的选项的value值要控制为不同
            这样后台接收就可以区分了，多个选项提交的时候，键值对用&符号进行拼接，例如下：
            favlan=1&favlan=3        
        -->

        你喜欢的语言：
        <input type="checkbox" name="favlan" value="1" checked="checked" />java
        <input type="checkbox" name="favlan" value="2" checked="checked" />php
        <input type="checkbox" name="favlan" value="3" checked="checked" />python
        <input type="checkbox" name="favlan" value="4" checked="checked" />c++

        <!-- 文件 -->
        <input type="file" name="" />
        <!-- 隐藏域 -->
        <input type="hidden" name="uname3" value="12e2" />
        <!--普通按钮：普通按钮没有什么效果，就是可以点击，以后学了js，就可以加入事件-->
        <input type="button" value="普通按钮" />
        <!-- 特殊按钮：重置按钮将页面恢复到初始状态 -->
        <input type="reset" />
        <!-- 特殊按钮：图片按钮： -->
        <img src="/Users/rain/Desktop/Pragom/HTML&CSS/showBooks/img/三国演义.png" />
        <input type="image" src="/Users/rain/Desktop/Pragom/HTML&CSS/showBooks/img/水浒传.png" />

        <!-- 特殊按钮：提交按钮：具备提交功能 -->
        <input type="submit" name="提交" />

        <!--下拉列表
            默认选中：selected="selected"
            多选：multiple="multiple"
        -->
        你喜欢的城市：
        <select name="city" multiple="multiple">
            <option value="0">----请选择----</option>
            <option value="1">北京</option>
            <option value="2" selected="selected">上海</option>
            <option value="3">广州</option>
            <option value="4">深圳</option>
        </select>

        <!-- 多行文本框 -->
        自我介绍：
        <textarea style="resize: none;" rows="10" cols="30">请在这里填写信息..</textarea>
        <br />
        <!-- label标签
            一般会在想要获得焦点的标签上加入一个标签上加入一个属性，然后label中的for属性跟id配合使用。 
         -->
        <label for="uname"> 用户名：</label> <input type="text" name="uername" id="uname" />
        </from>
</body>

</html>
```



### HTML5新增type类型

html5新增了很多类型， 我们挑一些常用的进行展示：

网站学习：www.w3school.com.cn/html5/att_input_type.asp

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>


<body>
    <form action="" method="get">
        <!-- email:
            html5的类型可以增加校验    
        -->
        <input type="email" name="email" />
        <!-- url -->
        <input type="url" />
        <!-- color -->
        <input type="color" />
        <!-- number:
            min:  最小值
            max:  最大值
            step: 步长
            value: 默认值： 一定在步长的范围中，否则不能提交
        -->
        <input type="number" min="1" max="10" step="3" value="4" />
        <!-- ranger -->
        <input type="range" min="1" max="10" name="range" step="3" />
        <!-- date -->
        <input type="date" />
        <!-- month -->
        <input type="month" />
        <!-- week -->
        <input type="week" />
        <!-- 提交按钮 -->
        <input type="submit" />

    </form>
</body>

</html>
```



### HTML5新增属性

```html
        <!-- 
            HTML5新增属性：
            multiple: 多选
            placeholder: 默认提示
            autofocus: 自动获取焦点
            required: 必填项
         -->
        <input type="text" autofocus="autofocus" />
        <input type="text" required="required" />
```





------



# CSS



## 引入

【1】为什么要学习CSS？

HTML画页面— 这个页面就是页面上需要的元素罗列起来，但是页面效果很差，不好看，为了让页面好看，为了修饰页面— CSS

CSS作用：修饰HTML页面

用了CSS之后，样式和元素本身做到了分离的效果 — 降低了代码的耦合性



【2】HTML和CSS的关系？

先有HTML，先有页面，修饰页面— CSS

【3】CSS名字：

CSS： cascading style sheets(层叠样式表)



层叠：样式的叠加

样式表：各种各样样式的集合



## CSS的三种书写方式

【1】内联样式：

```html
<body>
    <!-- 书写方式：内联样式（行内样式）
        在标签中加入一个style属性，CSS的样式作为属性值
        多个属性值之间用；进行拼接
    -->
    <h1 style="color: deeppink; font-family: 宋体;">这是一个h1标题</h1>
</body>
```

【2】内部样式

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>

    <!-- 书写样式： 内部样式
        head标签中加入一个style标签，在里面定位到你需要修饰的元素，然后在{} 中加入你要修饰的样式
    -->
    <style type="text/css">
        h1 {
            color: royalblue;
            font-family: 宋体;
        }
    </style>

</head>

<body>
    <h1>这是一个h1标题</h1>
</body>

</html>
```



【3】外部样式：

首先要创建一个CSS文件，CSS文件的后缀.css

```css
h1 {
    color: red;
    font-family: 宋体;
}
```

在创建html页面：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <!-- 引入外部资源 -->
    <link rel="stylesheet" type="text/css" href="/Users/rain/Desktop/Pragom/HTML&CSS/CSS01/mystyle.css" />
</head>

<body>
    <h1>这是一个h1标题</h1>
</body>

</html>
```



【4】实际开发中三种书写方式用的最多的是：

第三种：外部样式：因为这种方式真正做到了：元素页面和样式分离

【5】三种书写方式优先级：

就近原则



## 学习重点

CSS作用：修饰页面上的元素

```
h1{
	color: yellow;
}
```

h1: 定义需要修饰页面上的元素，如何定位：利用选择器

{}中内容: 给元素修饰的具体的样式 



## 选择器

### 基本选择器

【1】什么是基本选择器？

基本选择器是jQuery中最常见的选择器，也是最简单的选择器，它是通过元素id，calss和标签名等来查找DOM元素，常见基本选择器分别有：

- \#id：根据给定的id匹配一个元素（单个元素）
- .class：根据给定的类名匹配元素（元素集合）
- element：根据给定的元素名匹配元素（元素集合）
- *：匹配所有元素（元素集合）
- selector1，selector2..：将每一个选择器匹配到的元素合并后一起返回

【2】代码

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <style type="text/css">
        /* 
            [1]基本选择器：元素选择器
            通过元素的名字进行定位，它会获取页面上所有这个元素，无论在哪
            格式：
            元素名字{
                CSS样式
            }
        */
        h1 {
            color: red;
        }

        /* 
            【2】基本选择器：类选择器
            应用场合：不同类型的标签使用相同的类型
            格式：
            .class的名字{
                css样式
            }
         */
        .mycls {
            color: blueviolet;
        }

        /* 
            【3】基本选择器：id选择器
            应用场合：可以定位唯一的一个元素
            不同的标签确实可以使用相同的id,但是一般我们会进行人为的控制，让ID是可以唯一定位到一个元素。
            格式：
            #id名字{
                CSS样式
            }
        */
        #myid {
            color: darkgreen;
        }
    </style>
</head>

<body>
    <h1>h1标题</h1>
    <h1 class="mycls">类选择器1</h1>
    <h2 class="mycls">类选择器2</h2>
    <h2 id="myid">id选择器1</h2>
    <h2 id="myid">id选择器1</h2>
    <h1 class="mycls" id="myid">表嗲的那份i分</h1>

</body>

</html>
```

【3】优先级

ID选择器>class选择器>元素选择器



### 关系选择器

【1】div和span

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style type="text/css">
        /* 
            我们可以通俗的理解，把div理解为一个“塑料袋”
            div属于块级元素 -- 换行
            span属于行内元素 -- 没有换行效果
            span里面的内容占多大，span包裹的区域就多大
        */
        div {
            color: red;
            border: 1px red solid;
        }

        span {
            border: 1px greenyellow solid;
        }
    </style>
</head>

<body>
    <div>这是一个<br />h1标题</div>
    <div>貌似吧</div>
    <span>菏泽到家啊我</span>
    <span>菏泽到家 打我<br />啊我</span>

    <span>菏泽到家啊我</span>

</body>

</html>
```

div和css结合用于页面的布局。div+CSS用于布局。

【2】关系选择器

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<style type="text/css">
    /* 
    关系选择器：
    后代选择器：只要是这个元素的后代，样式都会发生变化
    div下面的所以h1标签都会改变
    */
    div h1 {
        color: royalblue;
    }

    /* 
    关系选择器：子代选择器
    只改变自标签的样式
    */
    div>h1 {
        color: rgb(255, 153, 0);
    }

    span>h2 {
        color: red;
    }
</style>

<body>
    <div>
        <h1>h1标题</h1>
        <h1>h1标题</h1>
        <h1>h1标题</h1>
        <h1>h1标题</h1>
        <h1>h1标题</h1>
        <span>
            <h2>h2标题</h2>
            <h2>h2标题</h2>
            <h2>h2标题</h2>
            <h1>h2标题</h1>
            <h2>h2标题</h2>
            <h2>h2标题</h2>
        </span>
    </div>

</body>

</html>
```



### 属性选择器

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <!-- 属性选择器 -->
    <style type="text/css">
        input[type="text"][value="rain1"] {
            background-color: blue;
        }

        input[type="password"][value="123123"] {
            background-color: red;
        }
    </style>

</head>

<body>
    <form method="get" action="aaa">
        用户名1：<input type="text" value="rain2" />
        用户名2：<input type="text" value="rain1" />
        密码：<input type="password" value="123123" />
        <input type="submit" value="登录" />
    </form>

</body>

</html>
```



### 伪类选择器

伪类选择器：像某些选择器添加特殊效果

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style type="text/css">
        .mycls:hover {
            color: brown;
        }
    </style>
</head>

<body>
    <h1 class="mycls">我是标题</h1>

</body>

</html>
```

一般伪类选择器都会用在超链接上。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style type="text/css">
        /* 设置静止状态 */
        a:link {
            color: chocolate;
        }

        /* 设置鼠标悬浮状态 */
        a:hover {
            color: bisque;
        }

        /* 设置触发状态 */
        a:active {
            color: blueviolet;
        }

        /* 设置完成状态 */
        a:visited {
            color: crimson;
        }
    </style>
</head>

<body>
    <a href="8.伪类选择器.html"> 超链接</a>
</body>

</html><!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style type="text/css">
        /* 设置静止状态 */
        a:link {
            color: chocolate;
        }

        /* 设置鼠标悬浮状态 */
        a:hover {
            color: bisque;
        }

        /* 设置触发状态 */
        a:active {
            color: blueviolet;
        }

        /* 设置完成状态 */
        a:visited {
            color: crimson;
        }
    </style>
</head>

<body>
    <a href="8.伪类选择器.html"> 超链接</a>
</body>

</html>
```



### 练习：百度导航栏

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="shortcut icon" href="https://www.baidu.com/favicon.ico" type="image/x-icon" />
    <title>百度一下，你就知道</title>

    <style type="text/css">
        ul {
            list-style-type: none;
            /* 将无序列表前面的图标取消*/
        }

        li {
            float: left;
            /*向左浮动*/
            ;
            margin-left: 20px;
            /*设置间隔20px*/
        }

        a {
            text-decoration: none;
            /*去掉下划线*/
            font-size: 13px;
            /*设置字体大小*/
            color: black;
            /*设置字体颜色*/
        }

        a:hover {
            color: #0000FF;
        }

        div {
            /* 定位 */
            position: absolute;
            /* 绝对定位*/
            right: 200px;
        }
    </style>
</head>

<body>
    <div>
        <ul>
            <li>
                <a href="aa">新闻</a>
            </li>
            <li>
                <a href="aa">hao123</a>
            </li>
            <li>
                <a href="aa">地图</a>
            </li>
            <li>
                <a href="aa">贴吧</a>
            </li>
            <li>
                <a href="aa">视频</a>
            </li>
            <li>
                <a href="aa">图片</a>
            </li>
            <li>
                <a href="aa">网盘</a>
            </li>
            <li>
                <a href="aa">更多</a>
            </li>
        </ul>

    </div>

</body>

</html>
```



## 浮动

【1】什么是浮动？

浮动可有三种取值，float:left/right/none，默认为none，浮：漂浮起来脱离文档流，动：朝着指定方向移动

浮动设计的初衷为了解决文字环绕图片问题，浮动后一定不会将文字挡住，这是设计初衷，不能违背的。CSS的float（浮动）使元素脱离文档流，按照指定的方向（左或右发生移动），直到它的外边缘碰到包含框或另一个浮动框的边框为止。说到脱离文档流要说一下什么是文档流，文档流是文档中可显示对象在排列时所占用的位置/空间，而脱离文档流就是页面中不占位置了。

【2】浮动初衷：文字环绕图片

float 属性定义元素在哪个方向浮动。以往这个属性总应用于图像，使文本围绕在图像周围，不过在 CSS 中，任何元素都可以浮动。浮动元素会生成一个块级框，而不论它本身是何种元素。
浮动非替换元素要指定一个明确的宽度；否则，它们会尽可能地窄。
注释：假如在一行之上只有极少的空间可供浮动元素，那么这个元素会跳至下一行，这个过程会持续到某一行拥有足够的空间为止。
我：
（以下以全部设置为float:left;为例）
如果包含框太窄，无法容纳水平排列的几个浮动元素，那么第一个容纳不下的浮动块会带着它后面 的浮动块一起向下移动，直到可以向左移动，则向左移动到边框或另一个浮动框，然后判断是否能容纳第一个浮动块，能则第一个浮动块留在这里，其后面的浮动块继续前面的操作，不能则第一个浮动块和后面的浮动块继续前面的操作。
下面是几个例子：

![image-20221205193427964](/Users/rain/Library/Application Support/typora-user-images/image-20221205193427964.png)

代码：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<style type="text/css">
    img {
        float: left;
    }
</style>

<body>

    <img src="/Users/rain/Desktop/Pragom/HTML&CSS/浮动/img/红楼梦.png" float="left" />
    float 属性定义元素在哪个方向浮动。以往这个属性总应用于图像，使文本围绕在图像周围，不过在 CSS 中，任何元素都可以浮动。浮动元素会生成一个块级框，而不论它本身是何种元素。
    浮动非替换元素要指定一个明确的宽度；否则，它们会尽可能地窄。
    注释：假如在一行之上只有极少的空间可供浮动元素，那么这个元素会跳至下一行，这个过程会持续到某一行拥有足够的空间为止。
    我：
    （以下以全部设置为float:left;为例）
    如果包含框太窄，无法容纳水平排列的几个浮动元素，那么第一个容纳不下的浮动块会带着它后面
    的浮动块一起向下移动，直到可以向左移动，则向左移动到边框或另一个浮动框，然后判断是否能容纳第一个浮动块，能则第一个浮动块留在这里，其后面的浮动块继续前面的操作，不能则第一个浮动块和后面的浮动块继续前面的操作。
    下面是几个例子：
</body>

</html>
```

【3】浮动原理



【4】浮动的语法：

值				描述

Left			元素向左浮动

right           元素向右浮动

None		 默认值，元素不浮动，并会显示在其在文本中出现的位置

【5】代码：

先设置一个大的div, 然后里面放入三个小的div

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <!-- 外层div -->
    <div style="background-color: blanchedalmond;">
        <div id="div01" style="width: 100px; height:100px; background-color:chartreuse; ">11</div>
        <div id="div02" style="width: 200px; height:200px; background-color:red; ">22</div>
        <div id="div03" style="width: 100px; height:100px; background-color:blueviolet;">33</div>
    </div>

</body>

</html>
```

效果：

![image-20221205193643358](/Users/rain/Library/Application Support/typora-user-images/image-20221205193643358.png)

然后给绿色div 加入向左浮动

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <!-- 外层div -->
    <div style="background-color: blanchedalmond;">
        <div id="div01" style="width: 100px; height:100px; background-color:chartreuse;  float: left;">11</div>
        <div id="div02" style="width: 200px; height:200px; background-color:red; ">22</div>
        <div id="div03" style="width: 100px; height:100px; background-color:blueviolet;">33</div>
    </div>

</body>

</html>
```

效果：

![image-20221205193806988](/Users/rain/Library/Application Support/typora-user-images/image-20221205193806988.png)

然后给红色加上浮动

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <!-- 外层div -->
    <div style="background-color: blanchedalmond;">
        <div id="div01" style="width: 100px; height:100px; background-color:chartreuse;  float: left;">11</div>
        <div id="div02" style="width: 200px; height:200px; background-color:red; float: left ">22</div>
        <div id="div03" style="width: 400px; height:300px; background-color:rgb(73, 43, 226);">33</div>
    </div>

</body>

</html>
```

效果：

![image-20221205194013969](/Users/rain/Library/Application Support/typora-user-images/image-20221205194013969.png)

然后给蓝色加入浮动：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <!-- 外层div -->
    <div style="background-color: blanchedalmond;">
        <div id="div01" style="width: 100px; height:100px; background-color:chartreuse;  float: left;">11</div>
        <div id="div02" style="width: 200px; height:200px; background-color:red; float: left ">22</div>
        <div id="div03" style="width: 400px; height:300px; background-color:rgb(73, 43, 226) ; float: left;">33</div>
    </div>

</body>

</html>
```



效果：

![image-20221205194116729](/Users/rain/Library/Application Support/typora-user-images/image-20221205194116729.png)



现在在三个div下面在加入一个div

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <!-- 外层div -->
    <div style="background-color: blanchedalmond;">
        <div id="div01" style="width: 100px; height:100px; background-color:chartreuse;  float: left;">11</div>
        <div id="div02" style="width: 200px; height:200px; background-color:red; float: left ">22</div>
        <div id="div03" style="width: 400px; height:300px; background-color:rgb(73, 43, 226) ; float: left;">33</div>
    </div>
    <div style="width: 500px; height: 500px; background-color: cornflowerblue;">
    </div>

</body>

</html>
```

效果：

![image-20221205194259367](/Users/rain/Library/Application Support/typora-user-images/image-20221205194259367.png)

用浮动要考虑影响，看看是否对其他元素有影响

【6】消除浮动影响：

方式1:

给浮动的父节点加入一个属性

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <!-- 外层div -->
    <div style="background-color: blanchedalmond; overflow: hidden;">
        <div id="div01" style="width: 100px; height:100px; background-color:chartreuse;  float: left;">11</div>
        <div id="div02" style="width: 200px; height:200px; background-color:red; float: left ">22</div>
        <div id="div03" style="width: 400px; height:300px; background-color:rgb(73, 43, 226) ; float: left;">33</div>
    </div>
    <div style="width: 500px; height: 500px; background-color: cornflowerblue;">
    </div>

</body>

</html>
```

方式2: 

给父节点加一个高度，让粉色div 撑起来。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <!-- 外层div -->
    <div style="background-color: blanchedalmond; height: 600px;">
        <div id="div01" style="width: 100px; height:100px; background-color:chartreuse;  float: left;">11</div>
        <div id="div02" style="width: 200px; height:200px; background-color:red; float: left ">22</div>
        <div id="div03" style="width: 400px; height:300px; background-color:rgb(73, 43, 226) ; float: left;">33</div>
    </div>
    <div style="width: 500px; height: 500px; background-color: cornflowerblue;">
    </div>

</body>

</html>
```

方式3:

被影响的元素，加入一个属性,:clear:both ,谁被影响给谁加入

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <!-- 外层div -->
    <div style="background-color: blanchedalmond;">
        <div id="div01" style="width: 100px; height:100px; background-color:chartreuse;  float: left;">11</div>
        <div id="div02" style="width: 200px; height:200px; background-color:red; float: left ">22</div>
        <div id="div03" style="width: 400px; height:300px; background-color:rgb(73, 43, 226) ; float: left;">33</div>
    </div>
    <div style="width: 500px; height: 500px; background-color: cornflowerblue;clear:both">
    </div>

</body>

</html>
```





## 定位

定位：一种高级的布局的方式。你可以将任何的元素，放在页面任意的位置。

position：有五个选值：

static   默认值，没有开启定位

          开启定位的情况以下四种：
    
           relative  相对定位
    
           absolute   绝对定位
    
           fixed     固定定位
    
           sticky    粘滞定位
【1】position 属性指定了元素的定位类型。

**1、static(默认)**

当你没有为一个元素(例如p)指定定位方式时，默认为static，也就是按照文档的流式(flow)定位，将元素放到一个合适的地方。所以在不同的分辨率下，采用流式定位能很好的自适合，取得相对较好的布局效果。

一般来说，我们不需要指明当前元素的定位方式是static——因为这是默认的定位方式。除非你想覆盖从父元素继承来的定位系统。

**2、relative(相对定位)**

在static的基础上，如果我想让一个元素在他本来的位置做一些调整(位移)，我们可以将该元素定位设置为relative，同时指定相对位移(利用top,bottom,left,right)。

有一点需要注意的是，相对定位的元素仍然在文档流中，仍然占据着他本来占据的位置空间——虽然他现在已经不在本来的位置了。

**3、absolute(绝对定位)**

如果你想在一个文档(Document)中将一个元素放至指定位置，你可以使用absolute来定位，将该元素的position设置为absolute，同时使用top,bottom,left,right来定位。

绝对定位会使元素从文档流中被删除，结果就是该元素原本占据的空间被其它元素所填充。

**4、mix relative and absolute(混合相对定位和绝对定位)**

如果对一个父元素设置relative，而对它的一个子元素设置absolute，如：

则子元素的绝对定位的参照物为父元素。

利用混合定位，我们可以用类似下面的css来实现两列(Two Column)定位

**5、fixed(固定定位)**

我们知道absolute定位的参照物是“上一个定位过的父元素(static不算)”，那么如果我想让一个元素定位的参照物总是整个文档(viewport)，怎么办呢？

答案是使用fixed定位，fixed定位的参照物总是当前的文档。利用fixed定位，我们很容易让一个p定位在浏览器文档的左上，右上等方位。比如你想添加一个信息提示的p，并将该p固定在右上方，你可以使用以下css

【2】静态定位：static

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <!-- 静态定位
        如果我们不写position属性的话，相当于默认效果就是静态定位。
        静态效果：就是元素出现在它本该出现的位置。一般使用静态定位可以直接省略
    -->
    <img src="/Users/rain/Desktop/Pragom/HTML&CSS/定位/img/红楼梦.png" style="position: static;">

</body>

</html>
```

【3】相对定位：relative

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <!-- 相对定位：
     相对元素自身所在的位置进行定位。
     可以设置left,right,top,bottom四个属性
     效果：在进行相对定位时，元素原来所在的位置被保留了，被占用了 -- 保留站位其他元素的位置不会发送移动
     一般情况下，left 和 right 不会同时使用，选择一个方向即可，top 和 bottom 不会同时使用，选择一个方向即可。
     优先级：左上>右下
-->
</body>
<div style="background-color: brown;">
    <div style="width: 100px; height: 100px; background-color: bisque;"></div>
    <div style="width: 100px; height: 100px; background-color: yellow; position: relative; bottom: 10px;"></div>
    <div style="width: 100px; height: 100px; background-color: green;"></div>
</div>

</html>
```

相对定位的应用场合：

（1）元素在小范围内移动的时候 

  (2)  结合绝对定位使用

再说一个属性： z-index

设置堆叠顺序，设置元素谁在上，谁在下

注意：z-index的使用：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <!-- 相对定位：
     相对元素自身所在的位置进行定位。
     可以设置left,right,top,bottom四个属性
     效果：在进行相对定位时，元素原来所在的位置被保留了，被占用了 -- 保留站位其他元素的位置不会发送移动
     一般情况下，left 和 right 不会同时使用，选择一个方向即可，top 和 bottom 不会同时使用，选择一个方向即可。
     优先级：左上>右下
-->
</body>
<div style="background-color: brown;">
    <div style="width: 100px; height: 100px; background-color: bisque; position: relative; left:10px; z-index: 15;">
    </div>
    <div
        style="width: 100px; height: 100px; background-color: yellow; position: relative; bottom: 10px; right: 20px; z-index: 90;">
    </div>
    <div style="width: 100px; height: 100px; background-color: green;"></div>
</div>

</html>
```

【4】绝对定位： absolute

源代码：

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<style type="text/css">
    #outer {
        width: 500px;
        height: 500px;
        background-color: pink;
        margin-left: 200px;
    }

    #div01 {
        width: 100px;
        height: 100px;
        background-color: blue;
        /* position: absolute;
        left: 30px;
        top: 50px; */
    }

    #div02 {
        width: 100px;
        height: 100px;
        background-color: rebeccapurple;
        position: sticky;
    }
</style>

<body>
    <div id="outer">

        <div id="div01">11 </div>
        <div id="div02">22 </div>

        <div>
</body>

</html>
```



效果：

![image-20221206093550230](/Users/rain/Library/Application Support/typora-user-images/image-20221206093550230.png)



```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<style type="text/css">
    #outer {
        width: 500px;
        height: 500px;
        background-color: pink;
        margin-left: 200px;
    }

    #div01 {
        width: 100px;
        height: 100px;
        background-color: blue;
        position: absolute;
        left: 30px;
        top: 50px;
    }

    #div02 {
        width: 100px;
        height: 100px;
        background-color: rebeccapurple;
        position: sticky;
    }
</style>

<body>
    <div id="outer">

        <div id="div01">11 </div>
        <div id="div02">22 </div>

        <div>
</body>

</html>
```

效果：

![image-20221206093452660](/Users/rain/Library/Application Support/typora-user-images/image-20221206093452660.png)

暂时来说看到的效果：蓝色div相对body产生的位移，相对body进行位置的改变，然后蓝色div发生位移以后，原位置得到了释放，紫色div上去

实际开发中，往往让蓝色div在粉色div中发送位移效果

配合相对定位使用：

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<style type="text/css">
    #outer {
        width: 500px;
        height: 500px;
        background-color: pink;
        margin-left: 200px;
        position: relative;
        /* 设置相对定位 */
    }

    #div01 {
        width: 100px;
        height: 100px;
        background-color: blue;
        position: absolute;
        left: 30px;
        top: 50px;

    }

    #div02 {
        width: 100px;
        height: 100px;
        background-color: rebeccapurple;

    }
</style>

<body>
    <div id="outer">

        <div id="div01">11 </div>
        <div id="div02">22 </div>

        <div>
</body>

</html>
```

效果：

![image-20221206094012722](/Users/rain/Library/Application Support/typora-user-images/image-20221206094012722.png)

总结：

当给一个元素设置了绝对定位的时候，它相对谁变化呢？它会向上一层一层找父级节点是否有定位，如果直到找到了body也没有定位，那么就对body进行变化，如果父级节点有定位，这个定位可以是（绝对定位，相对定位，固定定位）但是一般我们会配合父级为相对定位，当前元素为绝对定位，这个元素就会相对父级位置产生变化，无论是上面的哪一种，都会释放原来的位置，然后其他元素会占用那个位置。开发中，建议使用父级节点 relation,子级节点：绝对定位



【5】固定定位：fixed

应用场合：在页面过长的时候，将某个元素固定在浏览器的某个位置上，当拉动滚动条的时候，这个元素位置不动。

代码：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style type="text/css">
        #mydiv {
            width: 50px;
            height: 66px;
            background-color: blue;
            /* 固定定位 */
            position: fixed;
            right: 0px;
            top: 300px;
        }
    </style>
</head>

<body>
    <div>
        <div id="mydiv"> </div>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
        <p>ddid</p>
    </div>

</body>

</html>
```



## 盒子模型

【1】什么是盒子模型？

**概念：**盒子模型（Box Model）就是把HTML页面中的元素看作是一个矩形的盒子，也就是一个盛装内容的**容器。**

**作用：**CSS 围绕这些盒子产生了一种“盒子模型”概念，通过定义一系列与盒子相关的属性，可以极大地**丰富**和**促进**各个盒子乃至整个[HTML](https://links.jianshu.com/go?to=https%3A%2F%2Fbaike.baidu.com%2Fitem%2FHTML%2F97049)文档的**表现效果和布局结构**。

**组成：**每个盒子都由元素的内容(content)、内边距（padding）、边框（border）和外边距（margin），4个属性组成。

每个属性都包括4个部分：上、右、下、左。属性的4部分可以同时设置，也可以分别设置。

![image-20221206163832515](/Users/rain/Library/Application Support/typora-user-images/image-20221206163832515.png)

一、内容(content)

​     宽度width和高度height属性设置，对盒子内容大小的大小进行控制

二、内边距（padding）

　　padding属性用于设置内边距。 是指边框与内容之间的距离。

　　a）padding-top、padding-right、padding-bottom、padding-left

​        b)  padding: 1px 2px 3px 4px( **顺时针**)

　　注意： 后面跟几个数值表示的意思是不一样的。值的个数表达意思：

​            1个值padding：上下左右边距 比如padding: 3px; 表示上下左右都是3像素

​            2个值padding:  上下边距 左右边距 比如 padding: 3px 5px; 表示 上下3像素 左右 5像素

​            3个值padding：上边距 左右边距 下边距 比如 padding: 3px 5px 10px; 表示 上是3像素                                     左右是5像素 下是10像素

​            4个值padding:  上内边距 右内边距 下内边距 左内边距 比如: padding: 3px 5px 10px                                 15px; 表示 上3px 右是5px 下 10px 左15px

三、盒子边框（border）

　　border 属性来定义盒子的边框，该属性包含3个子属性：border-style(边框样式)，border-color(边框颜色)，border-width(边框宽度)。

　　1、定义宽度

　　　　a） border-top-width、border-bottom-width、border-left-width、border-right-width 

　　　　b） border-width:2px;                      

​                     border-width:1px 2px 3px 4px;               

　　　**注意：**当定义边框宽度时，必须要定义边框的显示样式，由于**默认样式为none**,所以仅设置边框的宽度，由于样式不存在，边框宽度也自动被清除为 0。

　　2、定义颜色

　　　　Demo:border-top-color: green;  border-color: yellow;

　　3、定义样式 border-style:

​                    hidden:隐藏边框(IE 不支持)                 dotted:点线

​                    dashed:虚线             solid:实线            double:双线边框

　　4、复合属性

　　        综合写法：border : border-width || border-style || border-color

　　        **注意：顺序不能错误。**

　　5、圆角边框（CSS3）：

　　    语法：border-radius: 左上角  右上角  右下角  左下角;

　　    Demo：border-radius: 10px;       /*  一个数值表示4个角都是相同的 10px 的弧度 */

​                        border-radius: 50%;         /*  100px   50% 取宽度和高度 一半  */

四、外边距（margin）

　　margin属性用于设置外边距。 设置外边距会在元素之间创建“空白”，定义了元素与其他相邻元素的距离， 这段空白通常不能放置其他内容。

　　margin-top、margin-right、margin-bottom、margin-left

　　margin:1px 2px 3px 4px( **顺时针**)

**常用功能：**

一、盒子水平居中

　　可以让一个盒子实现水平居中，需要满足一下两个条件：

​               块级元素和盒子必须指定宽度（width）

　　        左右的外边距都设置为auto，就可使块级元素水平居中。

二、外边距合并

​    margin的外边距合并（margin collapsing）

​           margin属性有一个特别的行为，就是外边距合并，这个行为只对普通文档流中的块级元素的**垂直外边距有效；**行内框（inline-block）、浮动元素和绝对定位的原素不会发生外边距合并。

​        发生外边距合并的两种基本情况：

​        1、两个或多个垂直毗邻的兄弟元素，上面元素的下边距会与下面元素的上边距发生合并，合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者。

![image-20221206163911273](/Users/rain/Library/Application Support/typora-user-images/image-20221206163911273.png)

 2.父元素和子元素之间，父元素的上外边距和第一个子元素的上外边距、父元素的下外边距和最后一个子元素的下外边距。发生这种情况的前提是父元素和第一个（或最后一个）子元素之间不存在边框和内边距把外边距分隔开，合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者.

![image-20221206163956394](/Users/rain/Library/Application Support/typora-user-images/image-20221206163956394.png)

**三、盒子模型和box-sizing**

​        box-sizing是用来**设置width、height的作用对象**的。

​        三个值:content-box(默认值) 、  border-box 、inherit（继承父类）;

​        **注意：没有margin-box**

​        box-sizing:conten-box，width=元素的内容区    (标准盒子模型)

​        box-sizing:border-box，width=元素内容区+padding+border  (IE盒子模型)

**四、背景剪裁 (Background clip)**

​        当我们给一个元素设置background-color和background-imge时，这个背景会覆盖到元素border的外边界，background-clip属性可以用来**调整背景所覆盖的区域:**

​        border-box:背景延伸到边框外，默认值

​        padding-box：背景延伸到内边距外，但是不会绘制到border。

​        content-box：背景被裁剪至内容区（content box）外沿。

**五、溢流（overflow）**

​        当用绝对的值设置盒子的大小时（比如，固定像素的 width 和 height），内容可能会超出设置的大小，此时内容就会溢流盒子。要控制这时候发生的事情，我们可以使用 overflow 属性。 最常用的：

​        hidden：溢出部分不会显示

​        visible：默认值，子元素会从父元素溢出，在父元素外部显示

​        scroll：生成两个滚动条，通过滚动条来查看完整的内容

​        auto：根据需要生成滚动条

**六、轮廓(Outline)**

​        盒子的 outline 看起来像边界，但是它不是盒模型的一部分。它表现得像边界，但是是画在盒子之上，不会修改盒子的大小（具体来说，ouline 是画在边界框之外，外边距区域之内）。

**七、盒子显示（display）类型**

​        display 三种常见的值为 block、inline、inline-block

​                    block（块盒）：盒子之前以及之后的内容出现在不同的行上

​                    inline （行内盒）：与块盒相反：与周围的文本和其它行内元素出现在同一行，并且其内容会像段落中的文本行一样，随着文本流换行（宽度和高度设置对行内盒无效，在行内盒上的所有内边距、外边距和边界设置会改变周围文本的位置，但是不会影响周围块盒的位置。）；

​                    inline-block（行内块盒）：

​          介于前两者之间：

​                   像行内盒一样，跟随周围的文本流堆放，不会在其前后创建换行；

​                   像块盒一样，使用宽度和高度设置大小，并且维护其块完整性 — 它不会跨段落行换行。

​         **块级元素默认设置为 display: block; ，行内元素默认设置为 display: inline 。**



**display: flex** — 允许你处理一些困扰CSS已久的一些传统布局问题，例如布置一系列弹性等宽容器或者垂直居中内容。

【3】练习

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style type="text/css">
        div {
            width: 100px;
            height: 100px;
            background-color: yellowgreen;
            margin-left: 100px;
            border: 4px red solid;
            padding-left: 5px;
        }
    </style>
</head>

<body>
    <div>8888</div>
</body>

</html>
```



【4】用代码感受盒子模型：

```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style type="text/css">
        /* 将所有元素的样式：外边距，边框，内边距全部设置为0  */
        * {
            margin: 0px;
            border: 0px;
            padding: 0px;
        }

        #outer {
            background-color: blueviolet;
            width: 500px;
            height: 500px;
            margin-left: 100px;
            margin-top: 100px;
            padding-left: 60px;
            padding-top: 50px;
            position: relative;
        }

        #mydiv {
            background-color: brown;
            width: 100px;
            height: 100px;
            padding-left: 60px;
            padding-top: 50px;
        }
    </style>
</head>

<body>
    <div id="outer">
        <div id="mydiv"> id</div>

    </div>

</body>

</html>
```

效果：

![image-20221206170528124](/Users/rain/Library/Application Support/typora-user-images/image-20221206170528124.png)

## 练习



```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style type="text/css">
        #mydiv01 {
            width: 60px;
            height: 55px;
            background: url(/Users/rain/Desktop/Pragom/HTML&CSS/盒子模型/img/喇叭.png) no-repeat -3px 1px;
            /* 不平衡 */
            background-color: #EFEFEF;
            /*注意：要先写背景图，在写背景色*/
            /* 设置div中文字体效果 */
            font-size: 17px;
            font-family: 微软雅黑;
            color: #666666;
            padding-top: 60px;
            text-align: center;
            /* 设置固定定位 */
            position: fixed;
            right: 0px;
            top: 200px;
        }

        #mydiv02 {
            width: 60px;
            height: 55px;
            background: url(/Users/rain/Desktop/Pragom/HTML&CSS/盒子模型/img/二维码.png) no-repeat 1px 1px;
            /* 不平衡 */
            background-color: #EFEFEF;
            /*注意：要先写背景图，在写背景色*/
            /* 设置div中文字体效果 */
            font-size: 17px;
            font-family: 微软雅黑;
            color: #666666;
            padding-top: 60px;
            text-align: center;
            /* 设置固定定位 */
            position: fixed;
            right: 0px;
            top: 320px;
        }

        #mydiv03 {
            width: 60px;
            height: 55px;
            background: url(/Users/rain/Desktop/Pragom/HTML&CSS/盒子模型/img/电话.png) no-repeat 3px 4px;
            /* 不平衡 */
            background-color: #EFEFEF;
            /*注意：要先写背景图，在写背景色*/
            /* 设置div中文字体效果 */
            font-size: 17px;
            font-family: 微软雅黑;
            color: #666666;
            padding-top: 60px;
            text-align: center;
            /* 设置固定定位 */
            position: fixed;
            right: 0px;
            top: 440px;
        }

        #mydiv04 {
            width: 60px;
            height: 55px;
            background: url(/Users/rain/Desktop/Pragom/HTML&CSS/盒子模型/img/叉.png) no-repeat 4px 10px;
            /* 不平衡 */
            background-color: #EFEFEF;
            /*注意：要先写背景图，在写背景色*/
            /* 设置div中文字体效果 */
            font-size: 17px;
            font-family: 微软雅黑;
            color: #666666;
            padding-top: 60px;
            text-align: center;
            /* 设置固定定位 */
            position: fixed;
            right: 0px;
            top: 560px;
        }
    </style>
</head>

<body>
    <div id="mydiv01">最新<br />发布</div>
    <div id="mydiv02">联系<br />客服</div>
    <div id="mydiv03">APP<br />下载</div>
    <div id="mydiv04">关闭</div>
    <p>342434</p>
    <p>342434</p>
    <p>342434</p>
    <p>342434</p>
    <p>342434</p>
    <p>342434</p>

    <p>342434</p>
    <p>342434</p>
    <p>342434</p>
    <p>342434</p>
    <p>342434</p>

    <p>342434</p>
    <p>342434</p>
    <p>342434</p>
    <p>342434</p>

    <p>342434</p>
    <p>342434</p>
    <p>342434</p>

    <p>342434</p>
    <p>342434</p>

    <p>342434</p>
    <p>342434</p>
    <p>342434</p>

    <p>342434</p>
    <p>342434</p>
    <p>342434</p>
    <p>342434</p>

    <p>342434</p>
    <p>342434</p>
    <p>342434</p>
    <p>342434</p>

    <p>342434</p>
    <p>342434</p>
    <p>342434</p>

    <p>342434</p>
    <p>342434</p>
    <p>342434</p>


</body>

</html>
```

效果：

![image-20221206184548214](/Users/rain/Library/Application Support/typora-user-images/image-20221206184548214.png)