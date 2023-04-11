





[TOC]



# 一.Servlet系列之HTTP协议

## 1.客户端与服务端的交互原理

![image-20221207092318139](/Users/rain/Library/Application Support/typora-user-images/image-20221207092318139.png)



![image-20221207092339549](/Users/rain/Library/Application Support/typora-user-images/image-20221207092339549.png)

客户端的浏览器版本很多，如何实现不同版本的浏览器与服务器的通信？

TCP 连接包括了建立连接、传输数据与断开连接三个阶段，而这一次我们要介绍的 HTTP 协议正是建立在 TCP 连接基础上。

HTTP 协议是一种允许浏览器向服务器获取资源的协议，同时也是我们前端开发 Web 的基础。HTTP 协议通常由浏览器发起请求，用于向服务器获取不同类型的文件，比如前端常用的 HTML 文件，CSS文件。而 HTTP 协议本身也是浏览器使用最广泛的协议。

在我们使用浏览器的时候，通常会碰到下面两种情况：

- 当我们第一次访问某个网站的时候，可能打开的速度特别慢，但是再次访问的时候速度明显变快。
- 当我们登录过一个网站之后，下次再访问这个网站的时候，就已经处于登录状态了。

这一背后的原理都需要了解 HTTP 协议的请求过程。这也正是我们要讲解的内容。

HTTP 请求流程大概氛围两部分：第一部分是浏览器向服务器发起 HTTP 请求，第二部分则是服务器进行响应。我们接下来将从这两部分进行讲解。

### HTTP 与 TCP

前面已经提到了 HTTP 协议建立在 TCP 连接的基础之上，那么我们在讲解 HTTP 请求之前，首先需要再深入了解一下 HTTP 协议与 TCP 之间的关系。

浏览器使用 HTTP 协议作为应用层，同时使用 TCP/IP 协议作为传输层协议，将它发送到网络上。

因此在 HTTP 实际开始工作之前，浏览器需要通过 TCP 协议与服务器建立连接，也就是说 HTTP 的内容本质上是通过 TCP 的传输数据阶段来实现的。

建立 TCP 连接的第一步，就是需要知道目的地址的 IP 地址和端口号。

我们一般不直接使用 IP 地址作为网址进行访问，而是通过部署在 IP 地址上的域名来访问。因此我们首先需要利用的就是我们的域名地址，来获取目的地址。

域名与 IP 地址实际上是一一映射的关系，而构建这套映射关系的系统，就叫做域名系统，简称为 DNS Domain Name System。

因此我们在拿到网址 URL 之后，我们就可以通过 DNS 和域名来获得目的地址的 IP 地址。

至于端口号，如果在访问地址的时候没有直接指明端口号，那 么HTTP 协议默认的端口号就是 80。

于是到现在我们就明白了HTTP请求与TCP连接之间的关系大致如下。

1. HTTP 是应用层协议，需要通过网络层协议 TCP 建立网络连接。
2. TCP 建立网络连接需要获得目的地址的 IP 地址和端口号。
3. 我们通过 DNS 和域名可以获得目的地址的 IP 地址。

#### 浏览器发起请求

我们假设在浏览器地址框种输入地址：[yucohny.github.io/index.html](https://www.proyy.com/?golink=aHR0cHM6Ly9saW5rLmp1ZWppbi5jbj90YXJnZXQ9aHR0cHMlM0ElMkYlMkZ5dWNvaG55LmdpdGh1Yi5pbyUyRmluZGV4Lmh0bWw=)。那么接下来我们尝试分析浏览器将完成的动作。

#### 构建请求

首先，浏览器需要构建请求行信息，随后，浏览器再准备发起网络请求：

```
GET /index.html HTTP1.1

<span class="copy-code-btn">复制代码</span>
```

#### 查找缓存

在正式发起网络请求之前，浏览器都会首先在浏览器的缓存当中查询是否有要请求的文件。

> 浏览器缓存本身是一种在本地保存资源的副本，以供下次请求时直接使用的一种技术。

当浏览器发现我们想要请求的资源已经存在于缓存当中时，就会拦截请求，直接返回该资源的副本，同时结束请求。这样做有几个明显的好处：

- 能够缓解服务器端的压力，提升性能。
- 缓存是实现快速资源下载的重要组成部分。

如果在缓存当中没有找到我们想要请求的资源，那么就会进入正式的网络请求过程。

#### 准备 IP 地址和端口

在前面介绍 HTTP 和 TCP 之间关系的时候，我们已经介绍了如何获取IP地址和端口号：

我们通过 DNS 查找到目的地址的 IP 地址；同时查看 HTTP 协议，本身是否指定了端口号，如果没有指定端口号，那么默认则是 80 端口。

#### 等待 TCP 队列

在一切都准备好了之后，我们仍然不能直接建立 TCP 连接，这是因为 chrome 谷歌浏览器存在一个机制：对于同一个域名，我们最多只能同时建立 6 个 TCP 连接，因此如果在同一个域名下有大于 6 个 TCP 连接同时发生，那么后面的请求则会进入排队等待状态，直到有多的空位来连接。

#### 建立 TCP 连接

这一部分就是浏览器，通过TCP协议与服务器已经成功建立连接。

#### 发送 HTTP 请求

在成功建立 TCP 连接之后，浏览器就可以和服务器进行通信。HTTP 中想要发送的数据，就是在这个通讯过程中传输的。

浏览器请求信息至服务器，本质上请求信息包含了三个部分：请求行、请求头与请求体。

对于请求行而言，则包括了请求方法，请求 URL 和 HTTP 协议版本三个部分，也就是我们前面所提到的构建请求。

请求头包括了一些浏览器的基础信息，比如浏览器所使用的操作系统、浏览器内核，以及浏览器端的 Cookie 等信息。

而请求体则是我们真正想要发送的数据的内容。

至此，浏览器就已经成功向服务器发送了请求。

#### 服务器处理请求

接下来复习将会根据浏览器的请求信息来准备响应的内容。

#### 返回请求

一旦服务器处理结束，就可以返回信息至浏览器。我们可以通过 `curl` 命令查看响应信息。

我们在本地命令行输入：

```
curl -i "https://yucohny.github.io/index.html"

<span class="copy-code-btn">复制代码</span>
```

精简后的返回信息如下：

```
HTTP/1.1 200 OK
​
Connection: keep-alive
Content-Length: 405
Server: GitHub.com
Content-Type: text/html; charset=utf-8
permissions-policy: interest-cohort=()
Last-Modified: Sat, 26 Mar 2022 14:46:30 GMT
Access-Control-Allow-Origin: *
Strict-Transport-Security: max-age=31556952
ETag: "623f2746-195"
expires: Sun, 27 Mar 2022 07:32:24 GMT
Cache-Control: max-age=600
x-proxy-cache: MISS
X-GitHub-Request-Id: 7CAA:49EE:2FEA23:336FBC:624010B0
Accept-Ranges: bytes
Date: Sun, 27 Mar 2022 07:22:24 GMT
Via: 1.1 varnish
Age: 0
X-Served-By: cache-icn1450078-ICN
X-Cache: MISS
X-Cache-Hits: 0
X-Timer: S1648365744.209898,VS0,VE183
Vary: Accept-Encoding
X-Fastly-Request-ID: c05cfa310b4d32d60f2c76f6c1d4f38a08916b56
​
<!doctype html>
<html lang="en">
<head></head>
<body>
​
</body>
</html>
<span class="copy-code-btn">复制代码</span>
```

我使用空行将请求信息划分为了三个部分，分别对应了响应行、响应头与响应体。不难看出这三个部分本质上对应了我们请求信息的三个部分。

响应行包括了 HTTP 协议版本与状态码。

> 常用的状态码有许多。其中状态码 200 表示处理成功；状态码 404 表示没有找到对应页面。

响应头则包括了服务器自身的一些信息，比如服务器生成返回数据的时间、返回的数据类型，以及服务器要在客户端保存的 cookie 的信息。

而响应体则包含了 HTML 的实际内容。

#### 断开连接

通常情况下，一旦服务器向客户端返回了响应信息，那么就需要关闭 TCP 连接，但是如果浏览器与服务器都在他们的请求信息或者返回信息中加入了以下信息

```
Connection: Keep-Alive

<span class="copy-code-btn">复制代码</span>
```

那么 TCP 连接在服务器返回信息后，仍然保持打开状态，这样浏览器就可以继续通过同一个 TCP 连接发送请求。保持 TCP 连接打开可以省去下次需要建立连接的时间提升资源下载的速度。

## 2.HTTP协议

```
HTTP：超文本传输协议(Hyper Text Transfer Protocol)
作用：规范了浏览器和服务器的数据交互
特点：
1、简单快速
2、灵活
3、无连接
4、无状态
5、支持B/S和C/S架构
```

注意：HTTP1.1版本之后支持可持续连接

### 2.1HTTP的交互流程

![image-20221207092918945](/Users/rain/Library/Application Support/typora-user-images/image-20221207092918945.png)

建立连接：3次握手

关闭连接：4次挥手



### 2.2HTTP协议请求格式

![image-20221207092949316](/Users/rain/Library/Application Support/typora-user-images/image-20221207092949316.png)

### 2.3HTTP请求方法

![image-20221207093020122](/Users/rain/Library/Application Support/typora-user-images/image-20221207093020122.png)

##### GET和POST请求方式的区别

1. get请求参数是直接显示在地址栏的，而post在地址栏不显示
2. get 方式不安全，post安全
3. get 请求参数是有长度限制的，post没有限制





### 2.4HTTP协议响应格式

![image-20221207093052254](/Users/rain/Library/Application Support/typora-user-images/image-20221207093052254.png)



### 2.5HTTP响应状态码

![image-20221207093112818](/Users/rain/Library/Application Support/typora-user-images/image-20221207093112818.png)

## 3. 常见的响应状态码

```
200 OK //客户端请求成功
400 Bad Request //客户端请求有语法错误，不能被服务器所理解
401 Unauthorized //请求未经授权，这个状态代码必须和WWW-Authenticate 报头域一起使用
403 Forbidden //服务器收到请求，但是拒绝提供服务
404 Not Found //请求资源不存在，eg：输入了错误的 URL
500 Internal Server Error //服务器发生不可预期的错误
503 Server Unavailable //服务器当前不能处理客户端的请求，一段时间后可能恢复正常
```





# 二.Servlet系列之TOMCAT

## 什么是Tomcat？





# 三.Servlet系列之第一个web程序





# 四.Servlet系列之Servlet



## 项目架构模式

- C/S：

   client/server：客户机和服务器架构

-  B/S：

  Browser/Server:浏览器和服务器架构

- C/S和B/S架构比较

|      | 服务器负荷 | 维护升级成本 | 安全要求 | 软件重用 |
| ---- | ---------- | ------------ | -------- | -------- |
| B/S  | 重         | 低           | 低       | 高       |
| C/S  | 轻         | 高           | 高       | 低       |



## Servlet简介

- 是一种Web服务器端编程技术
- 是实现了特殊接口的Java类
- 由支持Servlet的Web服务器调用和启动运行
- 一个Servlet负责对应的一个或一组URL访问请求，并返回相应的响应内容

实现使用：

```
1.创建一个普通Java文件
2.Java文件的类名实现HttpServlet
3.重写service的方法
4.在WEB- INF下的web.xml中添加请求与servlet类的映射关系
web.xml文件设置如下：
    <servlet>
        <servlet-name>MyServlet</servlet-name>
        <servlet-class>com.msb.MyServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>MyServlet</servlet-name>
        <url-pattern>/first</url-pattern>
    </servlet-mapping>
```



## servlet的访问流程

- url: http://localhost:8080/firstweb/first
- 组成：
  - 服务器地址： 端口/虚拟项目名/servlet的别名
  - Uri: 虚拟项目名/servlet别名
- 过程：浏览器发送请求到服务器，服务器根据请求URL地址中URL信息在webapps目录下找到对应的项目文件夹，然后再web.xml中检索对应的servlet，找到后调用并执行servlet



## servlet的生命周期

![image-20221210110014390](/Users/rain/Library/Application Support/typora-user-images/image-20221210110014390.png)



```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">
<!--    配置servlet的别名，同时在servlet-class配置项中添加servlet类的完全限名  包名+类名-->
    <servlet>
        <servlet-name>MyServlet</servlet-name>
        <servlet-class>com.msb.MyServlet</servlet-class>
    </servlet>
<!--    配置servlet跟请求的映射关系-->
    <servlet-mapping>
        <servlet-name>MyServlet</servlet-name>
        <url-pattern>/first</url-pattern>
    </servlet-mapping>


    <servlet>
        <servlet-name>second</servlet-name>
        <servlet-class>com.msb.MyServlet2</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>second</servlet-name>
        <url-pattern>/second</url-pattern>
    </servlet-mapping>

    <servlet>
        <servlet-name>three</servlet-name>
        <servlet-class>com.msb.ServletLife</servlet-class>
        <load-on-startup>1</load-on-startup>
    </servlet>
    <servlet-mapping>
        <servlet-name>three</servlet-name>
        <url-pattern>/three</url-pattern>
    </servlet-mapping>
</web-app>
```



```java
package com.msb; /**
 * @ClassName: ${NAME}
 * @Author: rain
 * @Date: 2022/12/10 - 12 - 10 - 11:02
 * @Description:
 * @Version: 1.0
 */


import javax.servlet.*;
import javax.servlet.http.*;
import javax.servlet.annotation.*;
import java.io.IOException;

@WebServlet(name = "ServletLife", value = "/ServletLife")
public class ServletLife extends HttpServlet {

    /**
     * 完成servlet对象的初始化工作
     * 在servlet接受第一次请求的时候创建对象
     * 生命周期：从第一次接受请求开始到服务器关闭销毁
     * 当在web.xml文件中配置了 <load-on-startup>1</load-on-startup> 后，在开启tomcat之后就会创建servlet对象，数字表示优先级
     * @throws ServletException
     */
    @Override
    public void init() throws ServletException {
        System.out.println("开始初始化");
    }

    @Override
    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        resp.getWriter().write("servlet life");
        System.out.println("this is servlet life");
    }

    @Override
    public void destroy() {
        System.out.println("服务器关闭了");
    }
}
```



## Service、doGet、doPost的区别

- Service方法：不管是get还是post请求方式，如何service方法存在，则优先执行service方法
- doGet方法：在没有service方法的情况下，如果是get请求，调用doGet方法
- doPost方法：在没有service方法的情况下，如果是post请求，调用doPost方法



```java
package com.msb; /**
 * @ClassName: ${NAME}
 * @Author: rain
 * @Date: 2022/12/10 - 12 - 10 - 13:45
 * @Description:
 * @Version: 1.0
 */


import javax.servlet.*;
import javax.servlet.http.*;
import java.io.IOException;

/**
 * Servlet类中可以有service方法
 *      用来接受get或者post请求
 *      如果service和doGet或者doPost同时存在，那么默认会调用service方法
 *      如果同时有server，doGet和doPost方法，在service方法的实现中调用了super(),service()会根据请求的方式跳转doGet或者doPost
 * doGet方法：
 *  用来接受get请求
 * doPost方法：
 *  用来接受post请求
 *
 *  总结：
 *      在编写servlet类的时候，不需要重新实现service方法，只需要重写doGet和doPost方法，用来接受post或者get请求
 */

public class MethodServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("我是get");
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("我是post");
    }

//    @Override
//    protected void service(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
////        System.out.println("我是service");
//    }
}
```



## servet常见错误

- 404：访问资源不存在
  - 请求路径跟web.xml中填写的请求不一致
  - 请求路径的项目虚拟名称填写错误
- 405：
  - 请求的方式跟servlet中支持的方式不一致
- 500：服务器内部错误
  - Web.xml中servlet类的名称错误
  - servlet对应的处理方法中存在代码逻辑错误



# 五.Servlet系列之request



## request常用方法：

- getRequestURL: 获取客户端的完整URL
- getRequestURI:  获取请求行中的资源各部分
- getQueryStrung:  获取请求行的参数部分
- getMethod:  获取请求方式
- getSchema:  获取请求的协议
- getRemoteAddr:  获取客户端的ip地址
- getRemoteHost:   获取客户端的完整主机名
- getRemotePort:    获取客户端的网络端口号
- getHeader:  获取请求头信息
- getParameter: 获取客户端参数信息



```java
package com.msb; /**
 * @ClassName: ${NAME}
 * @Author: rain
 * @Date: 2022/12/10 - 12 - 10 - 16:16
 * @Description:
 * @Version: 1.0
 */


import javax.servlet.*;
import javax.servlet.http.*;
import javax.servlet.annotation.*;
import javax.swing.*;
import java.io.IOException;
import java.util.Enumeration;

/**
 * HttpServletRequest用来存放客户端请求的参数
 *     请求行
 *     请求头
 *     请求体
 */

@WebServlet(name = "RequestServlet", value = "/RequestServlet")
public class RequestServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("get请求");

    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("post请求");
        super.doGet(request,response);
    }

    @Override
    protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
//        System.out.println("Post");
//        System.out.println("Get");
//        super.service(req, resp);
        //      获取请求中的请求方式
        String method = request.getMethod();
        System.out.println(method);
        // 获取请求的完整地址
        StringBuffer url = request.getRequestURL();
        System.out.println(url);
        // 获取请求中的资源路径
        String uri = request.getRequestURI();
        System.out.println(uri);
        // 获取请求中的协议
        String scheme = request.getScheme();
        System.out.println(scheme);

        //获取请求头数据
        // 根据key获取value的值
        String userAgent = request.getHeader("User-Agent");
        System.out.println(userAgent);
        //根据请求头信息中的所以key的枚举对象
        Enumeration<String> headers = request.getHeaderNames();
        while (headers.hasMoreElements()) {
            String key = headers.nextElement();
            String value = request.getHeader(key);
            System.out.println(key + ":" + value);
        }

        //获取用户请求数据
        //无论请求方式是post还是get，获取用户数据的方式不变
        String name = request.getParameter("name");
        String pwd = request.getParameter("pwd");
        String fav = request.getParameter("fav");
        System.out.println(name +":"+ pwd+":"+ fav);

        //获取用户数据中的所有key
        Enumeration<String> parameterNames = request.getParameterNames();
        while (parameterNames.hasMoreElements()) {
            System.out.println(parameterNames.nextElement());
        }

        //获取相同key的多个数据值，例如checkbox
        String[] parametersValues = request.getParameterValues("fav");
        for (String str:parametersValues){
            System.out.println("fav:"+ str);
        }

        //其他常用方法
        //获取远程客户端的地址
        String remoteAddr = request.getRemoteAddr();
        //获取远程客户端的主机名称
        String remoteHost = request.getRemoteHost();
        //获取远程客户端的端口号
        int remotePort = request.getRemotePort();
        System.out.println(remoteAddr + ":"+remoteHost+ ":" + remotePort);

        String localAddr = request.getLocalAddr();
        String localName = request.getLocalName();
        System.out.println(localAddr + ":" + localName);
    }
}
```



## HttpServletResponse

- HttpServletResponse对象是服务器的响应对象，这个对象中封装了向客户端发送数据，发送响应头，发送响应状态码的方法



### response常用方法

- 设置响应头
  - setHeader(String key, String value)	添加响应信息，key重复会覆盖
  - addHeader(Sting key, String value)    添加响应信息，key重复不会覆盖
- 设置响应状态
  - sendError(int num, String msg)	添加响应状态
- 设置响应实体
  - getWriter().write(msg)	响应具体的数据给浏览器

## 课后练习

- 实现用户登录的小项目

- 












### 乱码问题解决：

- 1.使用String重新进行编码
  - String name = new String(name.getBytes("iso-8859-1"),"utf-8")
- 2.get请求乱码
  - req.setCharacterEncoding("utf-8");
  - 在server.xml 中添加 useBodyEncodingForURI=true 的属性
- 3.post请求乱码
  - req.setCharacterEncoding("utf-8");
- 4.response乱码
  - response.setCharacterEncoding(“UTF-8”);
  - response.setContentType(“text/html;charset=utf-8”);





```java
package com.msb;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

/**
 * @ClassName: CharseServlet
 * @Author: rain
 * @Date: 2022/12/30 - 12 - 30 - 15:56
 * @Description:
 * @Version: 1.0
 */

/**
 * 处理乱码问题的方式：
 * 1.get请求
 *   1.获取字符串之后使用new String(name.getBytes("iso-8859-1"),"utf-8")
 *   2.设置request的编码格式，同时在server.xml 中添加 useBodyEncodingForURI=true 的属性
 *   3.在server.xml 中添加 URIEncoding="utf-8" 的属性
 * 2.post请求
 *   1. request.setCharsetEncoding("utf-8")
 * 3.response响应编码
 *   1. resp.setCharacterEncoding("gbk");
 *   2. resp.getWriter().write("欢迎你！");
 */

public class CharseServlet extends HttpServlet {
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("post");
        req.setCharacterEncoding("utf-8");
        String name = req.getParameter("name");
        System.out.println(name);
        resp.setCharacterEncoding("gbk");
        resp.getWriter().write("欢迎你！");
    }

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("get");
        //设置请求的编码格式
//        req.setCharacterEncoding("utf-8");
        String name = req.getParameter("name");
//        System.out.println(new String(name.getBytes("iso-8859-1"),"utf-8"));
        System.out.println(name);
    }
}
```

### serlvet的流程处理



client  

server：![image-20230103093035388](/Users/rain/Library/Application Support/typora-user-images/image-20230103093035388.png)



### servlet请求转发

![image-20230103094231867](/Users/rain/Library/Application Support/typora-user-images/image-20230103094231867.png)

```java
package com.msb.control;

import com.msb.enbity.User;
import com.msb.service.UserService;
import com.msb.service.impl.UserServiceImpl;
import com.sun.net.httpserver.Request;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.PrintWriter;
import java.sql.SQLException;

/**
 * @ClassName: LoginServlet
 * @Author: rain
 * @Date: 2022/12/12 - 12 - 12 - 15:14
 * @Description:
 * @Version: 1.0
 */


public class LoginServlet extends HttpServlet {

    UserService userService = new UserServiceImpl();
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //获取请求数据
        String name = req.getParameter("name");
        String pwd = req.getParameter("pwd");

        //封装对象
        User user = new User(name, pwd);
        //调用service进行逻辑处理
        User u = null;
        try {
            u = userService.checkUser(user);
        } catch (SQLException throwables) {
            throwables.printStackTrace();
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }
        System.out.println(u);

        resp.setCharacterEncoding("utf-8");
        resp.setContentType("text/html;charset=utf-8");
        if (u!=null){
            resp.getWriter().write("登录成功!");
        }else {
//            //设置响应编码
//            resp.setCharacterEncoding("utf-8");
//            resp.setContentType("text/html;charset=utf-8");
//
//
//            //获取响应的输出流对象
//            PrintWriter out = resp.getWriter();
//            out.write("<html>");
//            out.write("<head>");
//            out.write("</head>");
//            out.write("<body>");
//            out.write("<form action='login' method='get'>");
//            out.write("用户名:<input type='text' name='name' value='' /><br/>");
//            out.write("密码:<input type='text' name='pwd' value='' /><br/>");
//            out.write("<input type='submit' value='登录'/>");
//            out.write("</form>");
//            out.write("</body>");
//            out.write("</html>");

            //请求servlet的时候，写相对路径，同时后续不需要逻辑代码的处理
            req.getRequestDispatcher("page").forward(req, resp);
            return;
        }
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        this.doGet(req,resp);
    }
}
```



### servlet request的作用域

- 思考：不同的servlet之间如何实现数据共享？
- 用法：
  - request.setAttribute(Object key, Object value)
  - request.getAttribute(Object key)



### servlet重定向

![image-20230103140705758](/Users/rain/Library/Application Support/typora-user-images/image-20230103140705758.png)

- 1.浏览器发送两次请求
- 2.浏览器的地址发送变化
- 3.请求过程产生两个request对象和两个respond对象
- 4.两个servlet不能共享同一个request和response对象



请求转发和重定向的区别

|          | 请求次数 | 地址栏信息 | 是否共享数据 | 跳转限制 | 发生行为 |
| -------- | :------: | :--------: | :----------: | :------: | :------: |
| 请求转发 |    1     |    不变    |      是      | 本站资源 |  服务端  |
| 重定向   |    2     |    变化    |      否      | 任意URL  |  客户端  |





# Servlet系列之cookie



## 无状态的http协议

- http是一个无状态的协议，当一个客户端向服务端发送请求，在服务器返回响应后，连接就关闭了，在服务器端不保留连接信息。
- 思考：当客户端发送多次请求且需要相同的请求参数的时候，应该如何处理？



## 什么是cookie？

- cookie是一种在客户端保持http状态信息的技术
- cookie是在浏览器访问服务器的某个资源时，由web服务器在响应头传送给浏览器的数据
- 浏览器如果保存了某个cookie，那么以后每次访问服务器的时候，都会在请求头传递给服务端
- 一个cookie只能记录一种信息，是key-value形式
- 一个web站点可以给浏览器发送多个cookie，一个浏览器也可以存储多个站点的cookie



```java
package com.msb; /**
 * @ClassName: ${NAME}
 * @Author: rain
 * @Date: 2023/1/3 - 01 - 03 - 14:19
 * @Description:
 * @Version: 1.0
 */


import javax.servlet.*;
import javax.servlet.http.*;
import javax.servlet.annotation.*;
import java.io.IOException;

/***
 * cookie用来处理客户端发送不同请求的时候如何使用相同的参数信息
 *  cookie的使用：
 *      Cookie cookie = new Cookie("00001","beijing");
 *      response.addCookie(cookie);
 *      设置cookie的参数
 *      cookie.setMarAge(int seconds)
 *      cookie.setPath(String url)
 *      获取cookie对象
 *      Cookie[] cookie = request.getCookies()
 *  特点：
 *      1.cookie是保存在浏览器端的数据名称
 *      2.cookie分类：
 *          临时cookie:默认是存储在内存中的，所以当浏览器关闭的时候，cookie自动失效
 *          持久化cookie：保存在浏览器的某个存储目录，当时间过期之后，才会失效
 */

@WebServlet(name = "com.msb.CookieServlet", value = "/com.msb.CookieServlet")
public class CookieServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        request.setCharacterEncoding("utf-8");
        response.setCharacterEncoding("gbk");

        response.getWriter().write("学习cookie！");

        //创建cookie对象
        Cookie cookie = new Cookie("00001","beijing");
        Cookie cookie1 = new Cookie("00002","shanghai");
        //给cookie对象添加时间有效期
        cookie.setMaxAge(3*24*3600); //单位是秒
        //给cookie设置固定路径值
        cookie1.setPath("/cookie/abc");
        //将cookie对象设置到response对象中
        response.addCookie(cookie);
        response.addCookie(cookie1);

    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```



## Cookie练习

- 实现用户的一般登录





# 6.Servlet系列之session

## 思考：   一个用户的不同请求的处理需要使用相同的数据怎么办？

- 使用session来处理



## 什么是Session？

- 概念：
  - session表示会话，在一段时间内，用户与服务器之间的一系列的交互操作
  - session对象，用户在发送不同请求的时候，在服务端保存不同请求共享数据的存储对象
- 特点：
  - session是依赖cookie技术的服务端的数据存储技术
  - 由服务器进行创建
  - 每个用户独立拥有一个session对象
  - 默认存储时间是30分钟

https://www.cnblogs.com/andy-zhou/p/5360107.html#_caption_1

## Session机制

Session技术则是服务端的解决方案，它是通过服务器来保持状态的。由于Session这个词汇包含的语义很多，因此需要在这里明确一下 Session的含义。首先，我们通常都会把Session翻译成会话，因此我们可以把客户端浏览器与服务器之间一系列交互的动作称为一个 Session。从这个语义出发，我们会提到Session持续的时间，会提到在Session过程中进行了什么操作等等；其次，Session指的是服务器端为客户端所开辟的存储空间，在其中保存的信息就是用于保持状态。从这个语义出发，我们则会提到往Session中存放什么内容，如何根据键值从 Session中获取匹配的内容等。要使用Session，第一步当然是创建Session了。那么Session在何时创建呢？当然还是在服务器端程序运行的过程中创建的，不同语言实现的应用程序有不同创建Session的方法，而在Java中是通过调用HttpServletRequest的getSession方法（使用true作为参数）创建的。在创建了Session的同时，服务器会为该Session生成唯一的Session id，而这个Session id在随后的请求中会被用来重新获得已经创建的Session；在Session被创建之后，就可以调用Session相关的方法往Session中增加内容了，而这些内容只会保存在服务器中，发到客户端的只有Session id；当客户端再次发送请求的时候，会将这个Session id带上，服务器接受到请求之后就会依据Session id找到相应的Session，从而再次使用之。正式这样一个过程，用户的状态也就得以保持了。



## Session的基本原理

![image-20230104133021259](/Users/rain/Library/Application Support/typora-user-images/image-20230104133021259.png)



```java
package com.msb;

/**
 * @ClassName: ${NAME}
 * @Author: rain
 * @Date: 2023/1/4 - 01 - 04 - 14:36
 * @Description:
 * @Version: 1.0
 */


import javax.servlet.*;
import javax.servlet.http.*;
import javax.servlet.annotation.*;
import java.io.IOException;


/**
 * session:
 *      作用：
 *         解决相同用户发送不同请求时的数据共享问题
 *      特点：
 *         1.服务器端存储共享数据的技术
 *         2.session需要依赖cookie技术
 *         3.每个用户对应一个独立的session对象
 *         4.每个session对象的有效期为30分钟
 *         5.每次关闭浏览器的时候，重新请求都会开启一个新的session对象，因为返回的JSESSION保存在浏览器的内存中，是临时cookie，所以
 *         关闭之后自然消失
 *       作用：
 *          HttpSession session = request.getSession();
 *          修改session会话的保持时间
 *          session.setMaxInactiveInterval(6);
 *          设置session强制失效
 *          session.invalidate();
 *
 *
 */

@WebServlet(name = "com.msb.SessionServlet", value = "/com.msb.SessionServlet")
public class SessionServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("接受到请求");
        response.setCharacterEncoding("utf-8");
        request.setCharacterEncoding("utf-8");
        response.setContentType("text/html;charset=utf-8");
        //获取session对象
        HttpSession session = request.getSession();
        //修改session会话的保持时间
//        session.setMaxInactiveInterval(6);
        //getid方法拿到 JSESSIONID
        System.out.println(session.getId());
        //设置session强制失效
//        session.invalidate();
        //向session中设置参数
        session.setAttribute("lisi","123");
        response.getWriter().write("学习session");
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}

```



# 7.Servlet系列之Servlet Context和ServletConfig



思考：

- 思考：不同用户的数据共享怎么办？
- 使用Servlet Context来处理



## 什么是ServletContext？

- 运行在JVM上的每一个web应用程序都要一个与之对应的Servlet上下文（Servlet运行环境）
- Servlet API提供Servlet Context借口用来表示Servlet上下文，Servlet COntext对象可以被web应用程序中的所有servlet访问
- ServletContext对象是web服务器中的一个已知路径的根



## ServletContext原理

servletcontext对象有服务器进行创建，一个项目只有一个对象。不管在项目的任意位置进行获取得到的都是同一个对象，那么不同用户发起的请求获取到的也就是同一个对象了，该对象由用户共同拥有。



## ServletContext API

方法

| 方法                                                | 作用                               |
| --------------------------------------------------- | ---------------------------------- |
| Void setAttribute(String name,Object obj)           | 设置共享属性                       |
| Object getAttribute(String name)                    | 读取共享属性                       |
| Void removeAttribute(String name)                   | 移除共享属性                       |
| ServletContext getContext(String uri)               | 获取指定uri的上下文对象            |
| String getContext(path)                             | 返回web程序的上下文路径            |
| String getInitParameter(String param)               | 获取上下文初始化参数               |
| String getRealPath(String path)                     | 返回资源在服务器上的真实路径       |
| RequestDispatcher getRequestDispatcher(String path) | 返回一个包装了路径信息的dispatcher |



```java
package com.msb;

import javax.servlet.ServletContext;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

/**
 * @ClassName: ServletContextServlet
 * @Author: rain
 * @Date: 2023/1/6 - 01 - 06 - 14:55
 * @Description:
 * @Version: 1.0
 */

/**
 * ServletContext:
 *  作用：
 *      解决不同用户的数据共享问题
 *  特点：
 *      1.有服务器创建
 *      2.所以用户共享同一个ServletContext中的属性
 *      3.所有的servlet都可以访问到同一个ServletContext中的属性
 *      4.每一个web项目对应的是一个Servlet
 *  用法：
 *         //获取ServletContext对象
 *         //1.
 *         ServletContext context = this.getServletContext();
 *         //2.
 *         ServletContext context1 = this.getServletConfig().getServletContext();
 *         //3.
 *         ServletContext context2 = request.getSession().getServletContext();
 *        //设置属性值
 *         context.setAttribute("111","zhangsan");
 *        //获取属性值
 *         ServletContext context = this.getServletContext();
 *         String value = (String) context.getAttribute("111");
 *
 *         1.从web.xml获取公共属性值
 *          <context-param>
 *         <param-name>beijing</param-name>
 *         <param-value>beautiful</param-value>
 *          </context-param>
 *         String value = context.getInitParameter("beijing");
 *         System.out.println(value);
 *
 *         2.获取项目的虚拟目录路径
 *         context.getContextPath()
 *         3.获取某个资源的绝对路径
 *         context.getRealPath(String filename)
 *
 *
 * @author rain
 */

public class ServletContextServlet extends HttpServlet {
    public int cnnt = 1;

    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {

        //获取ServletContext对象
        //1.
        ServletContext context = this.getServletContext();
        //2.
        ServletContext context1 = this.getServletConfig().getServletContext();
        //3.
        ServletContext context2 = request.getSession().getServletContext();

        System.out.println(context==context1);
        System.out.println(context==context2);
        System.out.println(context1==context2);


        //设置属性值
        context.setAttribute("111","zhangsan");

        //从web.xml获取公共属性值
        String value = context.getInitParameter("beijing");
        System.out.println(value);
        String path = context.getContextPath();
        System.out.println(path);
        String path1 = context.getRealPath("beijing");
        System.out.println(path1);

    }

    @Override
    public void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

## 实现案例：网站计数器

```java
package context; /**
 * @ClassName: ${NAME}
 * @Author: rain
 * @Date: 2023/1/29 - 01 - 29 - 16:53
 * @Description:
 * @Version: 1.0
 */


import javax.servlet.*;
import javax.servlet.http.*;
import javax.servlet.annotation.*;
import java.io.IOException;
import java.io.PrintWriter;

@WebServlet(name = "NumServlet", value = "/NumServlet")
public class NumServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //设置编码格式
        request.setCharacterEncoding("utf-8");
        response.setContentType("text/html;charset=utf-8");

        //获取Servletcontext对象
        ServletContext context = this.getServletContext();
        //获取属性值
        Integer num  = (Integer) context.getAttribute("num");
        if (num == null) {
            context.setAttribute("num", 1);
        }else {
            //实现每次加1的功能
            num++;
            //将num设置会servletcontext对象中
            context.setAttribute("num",num);
        }

        //获取输出对象
        PrintWriter out = response.getWriter();
        out.write("<html>");
        out.write("<head>");
        out.write("</head>");
        out.write("<body>");
        out.write("用户访问的次数是"+context.getAttribute("num")+"次");
        out.write("</body>");
        out.write("</html");
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request,response);
    }
}
```



从文本中取得数据，进行累加之后重新覆盖

```java
package context; /**
 * @ClassName: ${NAME}
 * @Author: rain
 * @Date: 2023/1/29 - 01 - 29 - 16:53
 * @Description:
 * @Version: 1.0
 */


import javax.servlet.*;
import javax.servlet.http.*;
import javax.servlet.annotation.*;
import java.io.*;

@WebServlet(name = "NumServlet", value = "/NumServlet")
public class NumServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //设置编码格式
        request.setCharacterEncoding("utf-8");
        response.setContentType("text/html;charset=utf-8");

        String fileName = "/Users/rain/Desktop/Pragom/JAVAEE/servletcontext/web/file/nums.txt";
        String count = readFileContent(fileName);
        Integer cnt = Integer.parseInt(count);

        //获取ServletContext对象
        ServletContext context = this.getServletContext();

        context.setAttribute("num",cnt);

        //获取属性值
        Integer num  = (Integer) context.getAttribute("num");
//        if (num == null) {
//            context.setAttribute("num", 1);
//        }else {
//            //实现每次加1的功能
//            num++;
//            //将num设置会servletContext对象中
//            context.setAttribute("num",num);
//        }
        //实现加1的功能
        num++;
        context.setAttribute("num",num);
        writeUsingOutputStream(String.valueOf(num));

        //获取输出对象
        PrintWriter out = response.getWriter();
        out.write("<html>");
        out.write("<head>");
        out.write("</head>");
        out.write("<body>");
        out.write("用户访问的次数是"+context.getAttribute("num")+"次");
        out.write("</body>");
        out.write("</html");
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request,response);
    }

    /**
     * 读取文本中的数据，进行获取复制给ServletContext
     * @param fileName
     * @return
     */
    public static String readFileContent(String fileName) {
        File file = new File(fileName);
        BufferedReader reader = null;
        StringBuffer sbf = new StringBuffer();
        try {
            reader = new BufferedReader(new FileReader(file));
            String tempStr;
            while ((tempStr = reader.readLine()) != null) {
                sbf.append(tempStr);
            }
            reader.close();
            return sbf.toString();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (reader != null) {
                try {
                    reader.close();
                } catch (IOException e1) {
                    e1.printStackTrace();
                }
            }
        }
        return sbf.toString();
    }

    /**
     * 将计数重新给文本数据，以便累计加1 
     * @param data
     */
    private static void writeUsingOutputStream(String data) {
        OutputStream os = null;
        try {
            os = new FileOutputStream(new File("/Users/rain/Desktop/Pragom/JAVAEE/servletcontext/web/file/nums.txt"));
            os.write(data.getBytes(), 0, data.length());
        } catch (IOException e) {
            e.printStackTrace();
        }finally{
            try {
                os.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```



## ServlerConfig

思考：使用ServletContext对象可以获取web.xml中的全局配置文件，在web.xml中，每个servlet也可以进行单独的配置，那么该怎么获取配置信息呢？

- 使用ServletConfig对象



```java
package com.msb; /**
 * @ClassName: ${NAME}
 * @Author: rain
 * @Date: 2023/1/30 - 01 - 30 - 14:58
 * @Description:
 * @Version: 1.0
 */


import javax.servlet.*;
import javax.servlet.http.*;
import javax.servlet.annotation.*;
import java.io.IOException;
import java.util.Enumeration;

/**
 * ServletConfig
 *  作用：
 *      方便每一个servlet获取自己单独的属性配置
 *  特点：
 *      1.每一个servlet单独拥有一个servletConfig对象
 *  使用：
 *              //获取对象
 *         ServletConfig config = this.getServletConfig();
 *         String value = config.getInitParameter("china");
 *         System.out.println(value);
 *
 *         //获取所以的key
 *         Enumeration<String> initParameters = config.getInitParameterNames();
 *         while (initParameters.hasMoreElements()) {
 *             String name = initParameters.nextElement();
 *             String value2 = config.getInitParameter(name);
 *             System.out.println(name + "---" + value2);
 *         }
 *
 */

@WebServlet(name = "ServletConfigServlet", value = "/ServletConfigServlet")
public class ServletConfigServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //获取对象
        ServletConfig config = this.getServletConfig();
        String value = config.getInitParameter("china");
        System.out.println(value);

        //获取所以的key
        Enumeration<String> initParameters = config.getInitParameterNames();
        while (initParameters.hasMoreElements()) {
            String name = initParameters.nextElement();
            String value2 = config.getInitParameter(name);
            System.out.println(name + "---" + value2);
        }
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```



# 8.Servlet系列之JSP简单介绍



## 为什么需要JSP？

- Servlet：
  - 优点：逻辑处理方便 
  - 缺点： 页面表现麻烦
- JSP：
  - 优点：页面表现方便
  - 缺点：逻辑处理麻烦
- 注意：一般在weB项目中，采用JSP+Servlet+JavaBean 的技术（SSM）



## JSP本质

- JSP是一种动态网页技术
  - 动态生成网页数据，而不是有动态效果的网页！
  - 常见的几种动态网页技术：
    - JSP （JAVA Server Page）
    - ASP （Active Server Page）
    - PHP （Hypertext Preprocessor） 超级文本预处理语言
- 本质：JSP就是Servlet，JSP也是java类，通过JSP引擎将JSP转译成Servlet
- JSP=java+html



# 9.Servlet系列之JSP用法

编译器指令

- Page
  - <%@ page contentType="text/html;charset=UTF-8" language="java" %>
    <%@ page session="false" %>
    <%@ page errorPage="error.jsp" %>
- inclue
  - <%@ include file = “相对位置” %>
- taglib
  - <%@ tagline uri = “http://java.sun.com/jstl/core” prefix=“c”%>

## Jsp 的 page指令



```jsp
<%--
  Created by IntelliJ IDEA.
  User: rain
  Date: 2023/2/1
  Time: 10:36
  To change this template use File | Settings | File Templates.
--%>
<%--
    html注释
        也会被转译成Java文件，会发送给浏览器，但是浏览器不会被执行
    Java注释
        也会被转译，但是不会发送给浏览器
    jsp注释
        不会被转译
--%>

<%--
    page：
    用来设置转译成servlet文件时的参数
        contextType：表示浏览器解析响应信息的时候使用的编码和解析格式
        language：表示jsp要转译成的文件类型
        import： 导入需要的jar 包，多个包使用逗号分割
        pageEncoding: 设置页面的响应格式
        session: 用来控制servlet中是否有session对象
        errorPage： 当页面发送逻辑错误的时候，跳转的页面
        extends: 需要要转译的serlvet类要继承的父类（包含+类名）
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ page session="false" %>
<%@ page errorPage="error.jsp" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<%--我是html注释--%>
page jsp
<% int i = 100/0; %>
</body>
</html>

```

## jsp页面如何嵌入java代码

```jsp
<%@ page import="java.util.Random" %><%--
  Created by IntelliJ IDEA.
  User: rain
  Date: 2023/2/1
  Time: 10:36
  To change this template use File | Settings | File Templates.
--%>
<%--
    html注释
        也会被转译成Java文件，会发送给浏览器，但是浏览器不会被执行
    Java注释
        也会被转译，但是不会发送给浏览器
    jsp注释
        不会被转译
--%>

<%--
    page：
    用来设置转译成servlet文件时的参数
        contextType：表示浏览器解析响应信息的时候使用的编码和解析格式
        language：表示jsp要转译成的文件类型
        import： 导入需要的jar 包，多个包使用逗号分割
        pageEncoding: 设置页面的响应格式
        session: 用来控制servlet中是否有session对象
        errorPage： 当页面发送逻辑错误的时候，跳转的页面
        extends: 需要要转译的serlvet类要继承的父类（包含+类名）

        局部代码块：
            可以将Java代码跟页面展示的标签写到一个jsp页面中，Java代码转译成的servlet文件中，Java代码跟输出是保存在service方法中的
            缺点：
                代码可读性比较差，开发比较麻烦
                一般不使用
        全局代码块：
            定义公共的方法时候需要使用全局代码块使用<%!%>,生成的代码在servlet类中
            调用的时候需要使用局部代码块
        脚本调用方式：
            使用<%=直接调用变量或方法（必须有返回值）%>
            注意：不能在变量或方法的后面添加：

        页面导入的方式：
            静态导入：
                <%@include file="staticImport.jsp"%> file中填写的是jsp文件的相对路径
                不会将静态导入的页面生成一个新的servlet文件，而是两个文件合并
                优点：运行效率高
                缺点：两个页面会耦合到一起，不利于维护，两个页面中不能存在相同名称的变量名
            动态导入：
                <jsp:include page="dy.jsp"></jsp:include>
                两个页面不会进行合并，分别生成自己的servlet文件，但是页面在最终展示的时候是合并到一起的
                优点：没有耦合，可以存在同名的变量

            请求转发：
                在jsp中也可以实现servlet的请求转发功能
                <jsp:forward page="forward.jsp"></jsp:forward>  page中填写的是转发的页面的相对路径
                注意：在标签中间不可以添加任何字符  除了<jsp:param name="beijing" value="shanghai"/>
                在转发的页面中想要获取到属性值通过request.getParameter(String key)

--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ page session="false" %>
<%@ page errorPage="error.jsp" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<%--我是html注释--%>
page jsp
<% //int i = 100/0;%>

<%!
    String str = "jsp222";
public void test(){
    System.out.println(
            "我是全局代码块"
    );
}

public String hehe(){
    return "hehe";
}
%>

<%
    int i = new Random().nextInt(10);
    if(i>5) {
%>
<b> 今天天气很好 </b>
<%=str%>
<%}else {
%>
<b>今天天气不好</b>
<%}%>
<%--<%test();}%>--%>

<%@include file="staticImport.jsp"%>
<jsp:include page="dy.jsp"></jsp:include>

<jsp:forward page="forward.jsp">
    <jsp:param name="beijing" value="shanghai"/>
    <jsp:param name="henan" value="zhengzhou"/>
</jsp:forward  >

</body>
</html>
```



inclue

- 静态导入：
  - <%@ include file = “logo.jsp” %>
  - 是在servlet引擎转译时，就把此文件内容包含了进去（两个文件的源代码整合到一起，全部放到jspService方法中），所以只生成了一个servlet，所以两个页面不能有同名的变量
  - 运行效率高一点点，耦合性比较高，不够灵活
- 动态导入
  - <jsp:include page=“logo.jsp”> </jsp:include>
  - 是在servlet引擎转译后，请求的此页面，所以共生成了两个servlet，所以可以有同名变量
  - 生成两个servlet。相当于两个类之间的调用，耦合性比较低，非常灵活

## 动作语法- forward请求转发

<jsp:forward>用于请求转发 标签以后的代码，将不会被执行

- <jsp:forward page="forward.jsp">
      <jsp:param name="beijing" value="shanghai"/>
      <jsp:param name="henan" value="zhengzhou"/>
  </jsp:forward  >



## JSP九大内置对象



```jsp
<%@ page import="java.util.Random" %><%--
  Created by IntelliJ IDEA.
  User: rain
  Date: 2023/2/1
  Time: 10:36
  To change this template use File | Settings | File Templates.
--%>
<%--
    html注释
        也会被转译成Java文件，会发送给浏览器，但是浏览器不会被执行
    Java注释
        也会被转译，但是不会发送给浏览器
    jsp注释
        不会被转译
--%>

<%--
    page：
    用来设置转译成servlet文件时的参数
        contextType：表示浏览器解析响应信息的时候使用的编码和解析格式
        language：表示jsp要转译成的文件类型
        import： 导入需要的jar 包，多个包使用逗号分割
        pageEncoding: 设置页面的响应格式
        session: 用来控制servlet中是否有session对象
        errorPage： 当页面发送逻辑错误的时候，跳转的页面
        extends: 需要要转译的serlvet类要继承的父类（包含+类名）

        局部代码块：
            可以将Java代码跟页面展示的标签写到一个jsp页面中，Java代码转译成的servlet文件中，Java代码跟输出是保存在service方法中的
            缺点：
                代码可读性比较差，开发比较麻烦
                一般不使用
        全局代码块：
            定义公共的方法时候需要使用全局代码块使用<%!%>,生成的代码在servlet类中
            调用的时候需要使用局部代码块
        脚本调用方式：
            使用<%=直接调用变量或方法（必须有返回值）%>
            注意：不能在变量或方法的后面添加：

        页面导入的方式：
            静态导入：
                <%@include file="staticImport.jsp"%> file中填写的是jsp文件的相对路径
                不会将静态导入的页面生成一个新的servlet文件，而是两个文件合并
                优点：运行效率高
                缺点：两个页面会耦合到一起，不利于维护，两个页面中不能存在相同名称的变量名
            动态导入：
                <jsp:include page="dy.jsp"></jsp:include>
                两个页面不会进行合并，分别生成自己的servlet文件，但是页面在最终展示的时候是合并到一起的
                优点：没有耦合，可以存在同名的变量

            请求转发：
                在jsp中也可以实现servlet的请求转发功能
                <jsp:forward page="forward.jsp"></jsp:forward>  page中填写的是转发的页面的相对路径
                注意：在标签中间不可以添加任何字符  除了<jsp:param name="beijing" value="shanghai"/>
                在转发的页面中想要获取到属性值通过request.getParameter(String key)
            jspji九大内置对象：
                jsp页面在转译成其对应的servlet文件的时候，会自动声明一些对象，在jsp页面中可以直接使用
                注意：内置对象是jsp页面中使用的，可以在局部代码中使用，也可以在脚本段语句中使用，但是不能在全局代码中使用

                九大对象：
                pageContext： 表示页面的上下文的对象封存了其他的内置对象，封存了当前页面的运行信息
                            注意：每一个页面都要一个对应的pagecontext对象
                            伴随着当前页面的结束而结束
                request：封装当前请求的数据，由tomcat创建，一次请求对应一个request对象
                session：用来封装同一个用户的不同请求的共享数据，一次会话对应一个session对象
                response：响应对象，用来响应请求数据，将处理结果返回给浏览器，可以进行重定向
                page：代表当前jsp对象，跟java中的this指针类似、
                exception：异常对象，存储当前运行的异常信息，必须在page指令中
                config:相当于servletconfig对象，用来获取web.xml配置信息，完成servlet的初始化操作
                out: 响应对象，jsp内部使用，带有缓冲区的响应对象，效率要高于response
           四大作用域：
                pageContext：表示当前页面，解决当前页面内的数据共享问题，获取其他内置对象
                request：一次请求，一次请求的servlet的数据共享，通过请求转发的方式，将数据流转到下一个servlet
                session：一次会话，一个用户发送的不同请求直接的数据共享，可以将数据从一个请求流转到其他请求
                application：项目内，不同用户的数据共享问题，将数据从一个用户流转到其他用户
           路径问题：
                想要获取项目中的资源，可以使用相对路径，也可以使用绝对路径
                相对路径：相对于当前页面的路径
                    问题：1.资源的问题不可以随便更改
                         2.必须需要使用../的方式进行文件夹的跳出，如果目录结构比较深，操作起来比较麻烦
                绝对路径：
                    在请求路径的前面加/.表示当前服务器的根路径，使用的时候要添加/虚拟项目名称/资源目录


--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ page session="true" %>
<%@ page errorPage="error.jsp" isErrorPage="true" %>
<%
    String path = request.getServletPath();
        System.out.println(path);
String basePath = request.getScheme()+"://"+request.getServletPath() + ":"+request.getServerPort()+path+"/";
    System.out.println(basePath);

%>
<html>
<head>
    <title>Title</title>
</head>
<body>
<%--我是html注释--%>
page jsp
<% //int i = 100/0;%>

<%!
    String str = "jsp222";
public void test(){
    System.out.println(
            "我是全局代码块"
    );
}

public String hehe(){
    return "hehe";
}
%>

<%
    int i = new Random().nextInt(10);
    if(i>5) {
%>
<b> 今天天气很好 </b>
<%=str%>
<%}else {
%>
<b>今天天气不好</b>
<%}%>
<%--<%test();}%>--%>

<%--<%@include file="staticImport.jsp"%>--%>
<%--<jsp:include page="dy.jsp"></jsp:include>--%>

<%--<jsp:forward page="forward.jsp">--%>
<%--    <jsp:param name="beijing" value="shanghai"/>--%>
<%--    <jsp:param name="henan" value="zhengzhou"/>--%>
<%--</jsp:forward  >--%>

<a href="a/a.jsp">aaaa</a>
<a href="b/b.jsp">bbbbb</a>


</body>
</html>
```



# 10.servlet系列之EL和JSTL

## EL表达式

- 概念：
  - Expression Language，一种写法非常简单的表达式，语法简单易懂，便于使用。
- 作用：
  - 让jsp书写起来更加的方便，简化在jsp中获取作用域或者请求数据的写法
- 语法结构：
  - ${expression}
  - 提供.和[]两种运算符来获取数据

## EL表达式用法

- 使用EL表达式获取请求数据
  - 获取用户请求数据
  - 获取请求头数据
  - 获取cookie数据
- 使用EL表达式获取作用域数据
  - 获取作用域数据
  - 作用域查找顺序
  - 获取指定作用域中的数据
- 使用EL表达式进行运算
  - 算术运算
  - 关系运算
  - 逻辑运算

案例：

```jsp
<%--使用EL表达式获取数据--%>
name:${param.name}
pwd:${param.pwd}
aa:${param.a}
town:${user.address.town}
武安:${list[1].address.town}
mapvalue:${map.china}
mapUser:${map2.a1.address.town}
```

程序：

Java：

```java
package com.mashibing;

import com.mashibing.enbity.Address;
import com.mashibing.enbity.User;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.ArrayList;
import java.util.HashMap;

/**
 * @ClassName: ELServlet
 * @Author: rain
 * @Date: 2023/2/13 - 02 - 13 - 10:15
 * @Description:
 * @Version: 1.0
 */


/**
 * EL表达式
 *      概念：
 *          Expression Language,一种表达式语言，语法简单
 *      作用：
 *          方便jsp页面获取作用域中的属性
 *      语法规则：
 *          ${expression}, 可以使用，或者[]来获取属性值或者指定索引位置的对象
 *          获取值的时候，可以使用作用域中的key,然后使用，来饮用属性，使用[]来获取指定索引位置的对象
 *      作用域：
 *          pageContext--->request--->session-->application
 *      获取作用域数据的顺序：
 *          从小的作用域开始查询，如果找到则返回对应的值，不接着向大范围寻找数据
 *          当四种作用域中存在相同属性的时候，可以通过pageScore,requestScope,sessionScope,applicationScope获取指定作用域的数据
 *      EL表达式可以进行算术运算和关系运算
 *          直接在表达式中写入算法操作即可，如果是关系运算，返回true或者false
 *          注意：在EL表达式中的+表示加法操作而不是字符串连接符
 *      EL表达式可以进行逻辑运算：
 *          ${true&&false}<br>
 *          ${true||false}<br>
 *      EL表达式获取heard信息
 *          ${header}:获取所有请求头信息
 *          ${header[key}:获取指定key的数组
 *          ${headerValues[key}:获取key对应的一组数据，返回类型是数组
 *          ${headerValues[key}[0]:获取key对应数组的某一个值
 *      EL表达式获取cookie信息：
 *          ${cookie}<br>：获取cookie中的所有数据
 *          ${cookie.JSESSIONID}<br>：获取cookie中指定key数据的name
 *          ${cookie.JSESSIONID.name}<br>:获取cookie指定key数据的name
 *          ${cookie.JSESSIONID.value}<br>获取cookie指定key数据的value
 *
 *
 */

public class ELServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //设置请求响应的编码格式
        request.setCharacterEncoding("utf-8");
        response.setContentType("text/html;charset=utf-8");

        //从请求中获取数据
        String name = request.getParameter("name");
        String pwd = request.getParameter("pwd");
        System.out.println(name);
        System.out.println(pwd);
        //给request对象单独设置属性
        request.setAttribute("a","a");
        //给request添加对象
        User user = new User(1,"张三",new Address("北京市","北京市","门头沟"));
        User user2 = new User(2,"张三",new Address("河北省","邯郸","武安"));

        ArrayList<User> list = new ArrayList<User>();
        list.add(user);
        list.add(user2);

        request.setAttribute("user",user);

        //给request对象设置集合
        request.setAttribute("list",list);

        //给request对象设置map对象
        HashMap<String,String> map = new HashMap<String, String>();
        map.put("china","beijing");
        map.put("hebei","handan");

        request.setAttribute("map",map);

        HashMap<String,User> map2 = new HashMap<>();
        map2.put("a1",user);
        map2.put("a2",user2);

        request.setAttribute("map2",map2);

        //通过请求转发的方式跳转到某一个jsp页面
        request.getRequestDispatcher("el.jsp").forward(request, response);
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

JSP：

```jsp
<%@ page import="com.mashibing.enbity.User" %>
<%--<%@ page import="java.util.ArrayList" %>--%>
<%--<%@ page import="java.util.HashMap" %>--%>

<%  %>
<%--
  Created by IntelliJ IDEA.
  User: rain
  Date: 2023/2/13
  Time: 10:24
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>ellll</title>
</head>
<body>
<%--使用传统方式获取作用域中的值--%>
<%--name:<%=request.getParameter("name") %>--%>
<%--pwd:<%=request.getParameter("pwd")%>--%>
<%--aa:<%=request.getAttribute("a") %>--%>
<%--town:<%=((User)request.getAttribute("user")).getAddress().getTown()%>--%>
<%--武安:<%=((User)((ArrayList)request.getAttribute("list")).get(1)).getAddress().getTown()%>--%>
<%--map:<%=((HashMap)request.getAttribute("map")).get("china")%>--%>
<%--map2:<%=((User)((HashMap)request.getAttribute("map2")).get("a1")).getAddress().getTown()%>--%>

<%--
使用传统方式获取request对象中的值有一下缺点
1.必须要导入包
2.进行类型的强制转换
3.层次结构比较复杂


解决办法使用EL表达式
--%>
<br/>
<%--使用EL表达式获取数据--%>
name:${param.name}
pwd:${param.pwd}
aa:${param.a}
town:${user.address.town}
武安:${list[1].address.town}
mapvalue:${map.china}
mapUser:${map2.a1.address.town}

<%--使用el表达式获取对象的顺序--%>
<%
    pageContext.setAttribute("key", "hello pageContext");
    request.setAttribute("key","hello request");
    session.setAttribute("key","hello session");
    application.setAttribute("key", "hello application");
%>
<br/>
key:${key}

<br/>
pageContext:${pageScope.key}
<br/>
request:${requestScope.key}
<br/>
session:${sessionScope.key}
<br/>
application:${applicationScope.key}<br/>

<%--使用EL表达式进行基本运算--%>
${1+2}<br/>
${1-2}<br/>
${1*2}<br/>
${1/2}<br/>
${1%2}<br/>
${1>2}<br/>
${1>2?"男":"女"}
<%--${1+"abc"}--%>
<br/>

<%--获取请求头数据--%>
${header}<br/>
${header["host"]}<br/>
${headerValues["accept-language"][0]}<br/>

<%--获取cookie数据--%>
${cookie}<br>
${cookie.JSESSIONID}<br>
${cookie.JSESSIONID.name}<br>
${cookie.JSESSIONID.value}<br>

<%--逻辑运算符--%>
${true&&false}<br>
${true||false}<br>
</body>
</html>
```



## JSTL标签库

JSTL（Java Server Pages Standerd Tag Library，JSP标准标签库）包含用于编写和开发JSP页面的一组标准标签，它可以为用户提供一个无脚本环境。在此环境中，用户可以使用标签编写代码，而无须使用Java脚本。在JSP2.0中已将JSTL作为标准支持。使用JSTL可以取代在传统JSP程序中嵌入Java代码的做法，大大提高了程序的可维护性

### 1、JSTL标签库简介

虽然JSTL叫做标准标签库，实际上它是由5个功能不同的标签库组成。这5个标签库分别是核心标签库、格式标签库、SQL标签库、XML标签库和函数标签库等。在使用这些标签之前必须在JSP页面的顶部使用<%@ taglib%>指令定义引用的标签库和访问前缀。

![image-20230214201213679](/Users/rain/Library/Application Support/typora-user-images/image-20230214201213679.png)

#### 1.1 核心标签库

核心标签库主要用于完成JSP页面的常用功能，包括JSTL的表达式标签、URL标签、流程控制标签和循环标签共4种标签。其中，表达式标签包括：<c:out>、<c:set>、<c:remove>和<c:catch>；URL标签包括：<c:import>、<c:redirect>、<c:url>和<c:param>；流程控制标签包括：<c:if>、<c:choose>、<c:when>和<c:otherwise>；循环标签包括：<c:forEach>和<c:forTokens>。

 使用核心标签库的taglib指令格式如下：

```
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>
```

核心标签库的基本作用：

![image-20230214201458396](/Users/rain/Library/Application Support/typora-user-images/image-20230214201458396.png)

#### 1.2 格式标签库

格式标签库提供了一个简单的国际化标记，也被称为 I18N 标签库，用于处理和解决国际化相关的问题。另外，格式化标签库中还包含格式化数字和日期显示格式的标签。

使用格式标签库的taglib指令格式如下：

```
<%@ taglib prefix="fmt" uri="http://java.com/jsp/jstl/fmt"%>
```

格式标签库的基本作用：

![image-20230214201601699](/Users/rain/Library/Application Support/typora-user-images/image-20230214201601699.png)

#### 1.3 SQL标签库

SQL标签库提供了基本的访问关系型数据的能力。使用SQL标签，可以简化对数据库的访问。如结合核心标签库，可以方便地获取结果集，并迭代输出结果集中的数据。

使用SQL标签库的taglib指令格式如下：

```
<%@ taglib prefix="sql" uri="http://java.sun.com/jsp/jstl/sql"%>
```

SQL标签库的基本作用：

#### ![image-20230214201724500](/Users/rain/Library/Application Support/typora-user-images/image-20230214201724500.png)

#### 1.4 XML标签库

XML标签库可以处理和生成XML的标记，使用这些标记可以很方便地开发基于XML的Web应用。

使用XML标签库的taglib指令格式如下：

```
<%@ taglib prefix="x" uri="http://java.sun.com/jsp/jstl/xml"%>
```

在使用xml标签前，你必须将 XML 和 XPath 的相关包拷贝至你的<Tomcat 安装目录>\lib下：

XercesImpl.jar 下载地址： http://www.apache.org/dist/xerces/j/

xalan.jar下载地址： http://xml.apache.org/xalan-j/index.html

XML标签库的基本作用：

![image-20230214201756202](/Users/rain/Library/Application Support/typora-user-images/image-20230214201756202.png)

#### 1.5 函数标签库

函数标签库提供了一系列字符串操作函数，用于完成分解字符串、连接字符串、返回子串、确定字符串是否包含特定的子串等功能。

使用函数标签库的taglib指令格式如下：

```
<%@ taglib prefix="fn" uri="http://java.sun.com/jsp/jstl/functions"%>
```

函数标签库的基本作用：

![image-20230214201847917](/Users/rain/Library/Application Support/typora-user-images/image-20230214201847917.png)