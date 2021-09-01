# Jsp

>总结Jsp
>
>1. 什么是Jsp?
>2. 为什么要学习jsp 技术
>3. 如何创建一个jsp 动态页面。
>4. 如何修改jsp 页面的默认编码?
>5. jsp 的本质是什么。
>6. jsp 的三种语法
>  a) jsp 头部的page 指令
>   i. language 属性
>   ii. contentType 属性
>   iii. pageEncoding 属性
>   iv. import 属性
>   v. autoFlush 属性
>   vi. buffer 属性
>   vii. errorPage 属性
>   viii. isErrorPage 属性
>   ix. session 属性
>   x. extends 属性
>   b) jsp 中的三种脚本
>   i. 声明脚本
>7. 我们可以定义全局变量。
>8. 定义static 静态代码块
>9. 定义方法
>10. 定义内部类
>  ii. 表达式脚本
>11. 输出整型
>12. 输出浮点型
>13. 输出字符串
>14. 输出对象
>     iii. 代码脚本
>15. 代码脚本----if 语句
>16. 代码脚本----for 循环语句
>17. 翻译后java 文件中_jspService 方法内的代码都可以写
>     c) jsp 中的三种注释
>     i. html 注释
>     ii. java 注释
>     “玩转”Java 系列
>     iii. jsp 注释
>18. jsp 九大内置对象
>19. jsp 四大域对象
>20. jsp 中的out 输出和response.getWriter 输出的区别
>21. jsp 的常用标签
>       a) jsp 静态包含
>       b) jsp 标签-动态包含
>       c) jsp 标签-转发
>22. 静态包含和动态包含的区别
>23. jsp 练习题--jsp 输出一个表格，里面有20 个学生信息。
>       13、什么是Listener 监听器？
>       13.1、ServletContextListener 监听器

## 1.什么是jsp，它有什么用?

jsp 的全换是java server pages。Java 的服务器页面。

JSP(全称Java Server Pages)是由Sun 公司专门为了解决动态生成HTML 文档的技术。

jsp 的主要作用是代替Servlet 程序回传html 页面的数据。
因为Servlet 程序回传html 页面数据是一件非常繁锁的事情。开发成本和维护成本都极高。

servlet输入html页面的程序代码：

```java
package com.atguigu.servlet;
import java.io.IOException;
import java.io.Writer;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
public class HtmlServlet extends HttpServlet {
private static final long serialVersionUID = 1L;
protected void doGet(HttpServletRequest request,
HttpServletResponse response) throws ServletException, IOException {
// 设置返回的数据内容的数据类型和编码
response.setContentType("text/html; charset=utf-8");
// 获取字符输出流
Writer writer = response.getWriter();
//输出页面内容！
writer.write("<!DOCTYPE html PUBLIC \"-//W3C//DTD HTML 4.01 Transitional//EN\"
\"http://www.w3.org/TR/html4/loose.dtd\">");
writer.write("<html>");
writer.write("<head>");
writer.write("<meta http-equiv=\"Content-Type\" content=\"text/html;
charset=UTF-8\">");
writer.write("<title>Insert title here</title>");
writer.write("</head>");
writer.write("<body>");
writer.write("这是由Servlet 程序输出的html 页面内容！");
writer.write("</body></html>");
}
protected void doPost(HttpServletRequest request,
HttpServletResponse response) throws ServletException, IOException {
}
}
```

在浏览器中输入访问Servlet 的程序地址得到以下结果：

![image-20210901095849654](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901095849654.png)

上面的代码我们不难发现。通过Servlet 输出简单的html 页面信息都非常不方便。
那我们要输出一个复杂页面的时候，就更加的困难，而且不利于页面的维护和调试。
所以sun 公司推出一种叫做jsp 的动态页面技术帮助我们实现对页面的输出繁锁工作。
jsp 页面的访问千万不能像HTML 页面一样。托到浏览器中。只能通过浏览器访问Tomcat 服务器再访问jsp 页面。

Servlet 回传html 页面数据的代码：

```jsp
public class PringHtml extends HttpServlet {
@Override
protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException,
IOException {
// 通过响应的回传流回传html 页面数据
resp.setContentType("text/html; charset=UTF-8");
PrintWriter writer = resp.getWriter();
writer.write("<!DOCTYPE html>\r\n");
writer.write(" <html lang=\"en\">\r\n");
writer.write(" <head>\r\n");
writer.write(" <meta charset=\"UTF-8\">\r\n");
writer.write(" <title>Title</title>\r\n");
writer.write(" </head>\r\n");
writer.write(" <body>\r\n");
writer.write(" 这是html 页面数据\r\n");
writer.write(" </body>\r\n");
writer.write("</html>\r\n");
writer.write("\r\n");
}
}
```

jsp 回传一个简单html 页面的代码：

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>

<head>
<title>Title</title>
</head>

<body>
这是html 页面数据
</body>
</html>
```

jsp 的小结：
1、如何创建jsp 的页面?

![image-20210829224435544](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210829224435544.png)

输入文件名敲回车即可！！

![image-20210829224701687](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210829224701687.png)

选中WebContent 目录，右键创建一个jsp 文件

![image-20210901100056461](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901100056461.png)

修改jsp 页面的文件名

![image-20210901100133101](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901100133101.png)

选择生成jsp 文件的模板,我们选择默认的New JSP File(html)

![image-20210901100218926](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901100218926.png)

在body 标签中添加你想要显示的文本内容

![image-20210901100241023](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901100241023.png)

然后在浏览器中输入jsp 页面的访问地址。

jsp 页面的访问地址和html 页面的访问路径一样http://ip:端口号/工程名/文件名
也就是http://127.0.0.1:8080/day08/index.jsp

![image-20210901100312788](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901100312788.png)

**如何修改jsp 文件的默认编码。**

![image-20210901100354350](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901100354350.png)

注意事项：
a)jsp 页面是一个类似于html 的一个页面。jsp 直接存放到WebContent 目录下，和html 一样
访问jsp 的时候，也和访问html 一样
b)jsp 的默认编码集是iso-8859-1 修改jsp 的默认编码为UTF-8

2、jsp 如何访问：
jsp 页面和html 页面一样，都是存放在web 目录下。访问也跟访问html 页面一样。
比如：
在web 目录下有如下的文件：
web 目录
a.html   页面访问地址是->>>>>> http://ip:port/工程路径/a.html
b.jsp      页面访问地址是->>>>>> http://ip:port/工程路径/b.jsp

## 2.jsp 的本质是什么。

jsp 页面本质上是一个Servlet 程序。
当我们第一次访问jsp 页面的时候。Tomcat 服务器会帮我们把jsp 页面翻译成为一个java 源文件。并且对它进行编译成为.class 字节码程序。我们打开java 源文件不难发现其里面的内容是：

![image-20210829224917925](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210829224917925.png)

我们跟踪原代码发现，HttpJspBase 类。它直接地继承了HttpServlet 类。也就是说。jsp 翻译出来的java 类，它间接了继
承了HttpServlet 类。也就是说，翻译出来的是一个Servlet 程序

![image-20210829224946397](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210829224946397.png)

总结：通过翻译的java 源代码我们就可以得到结果：jsp 就是Servlet 程序。
大家也可以去观察翻译出来的Servlet 程序的源代码，不难发现。其底层实现，也是通过输出流。把html 页面数据回传
给客户端。

```java
public void _jspService(final javax.servlet.http.HttpServletRequest request, final
javax.servlet.http.HttpServletResponse response)
throws java.io.IOException, javax.servlet.ServletException {
final java.lang.String _jspx_method = request.getMethod();
if (!"GET".equals(_jspx_method) && !"POST".equals(_jspx_method) && !"HEAD".equals(_jspx_method)
&& !javax.servlet.DispatcherType.ERROR.equals(request.getDispatcherType())) {
response.sendError(HttpServletResponse.SC_METHOD_NOT_ALLOWED, "JSPs only permit GET POST or
HEAD");
return;
}
final javax.servlet.jsp.PageContext pageContext;
javax.servlet.http.HttpSession session = null;
final javax.servlet.ServletContext application;
final javax.servlet.ServletConfig config;
javax.servlet.jsp.JspWriter out = null;
final java.lang.Object page = this;
javax.servlet.jsp.JspWriter _jspx_out = null;
javax.servlet.jsp.PageContext _jspx_page_context = null;
try {
response.setContentType("text/html;charset=UTF-8");
pageContext = _jspxFactory.getPageContext(this, request, response,
null, true, 8192, true);
_jspx_page_context = pageContext;
application = pageContext.getServletContext();
config = pageContext.getServletConfig();
session = pageContext.getSession();
out = pageContext.getOut();
_jspx_out = out;
out.write("\r\n");
out.write("\r\n");
out.write("<html>\r\n");
out.write("<head>\r\n");
out.write(" <title>Title</title>\r\n");
out.write("</head>\r\n");
out.write("<body>\r\n");
out.write(" a.jsp 页面\r\n");
out.write("</body>\r\n");
out.write("</html>\r\n");
} catch (java.lang.Throwable t) {
if (!(t instanceof javax.servlet.jsp.SkipPageException)){
out = _jspx_out;
if (out != null && out.getBufferSize() != 0)
try {
if (response.isCommitted()) {
out.flush();
} else {
out.clearBuffer();
}
} catch (java.io.IOException e) {}
if (_jspx_page_context != null) _jspx_page_context.handlePageException(t);
else throw new ServletException(t);
}
} finally {
_jspxFactory.releasePageContext(_jspx_page_context);
}
}
```

**jsp 的本质，其实是一个Servlet 程序。**

首先我们去找到我们Tomcat 的目录下的work\Catalina\localhost 目录。当我们发布day09 工程。并启动Tomcat
服务器后。我们发现
在work\Catalina\localhost 目录下多出来一个day09 目录。

![image-20210901100627329](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901100627329.png)

一开始day09 目录还是空目录。

![image-20210901100642212](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901100642212.png)

然后，我们在浏览器输入一个jsp 文件的访问路径访问。
比如http://127.0.0.1:8080/day09/index.jsp 访问index.jsp 文件
day09 目录马上会生成org\apache\jsp 目录。
并且在会中有两个文件。

![image-20210901100703911](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901100703911.png)

index_jsp.class 文件很明显是index_jsp.java 源文件编译后的字节码文件。
那么index_jsp.java 是个什么内容呢?
生成的java 文件名，是以原来的文件名加上_jsp 得到。xxxx_jsp.java 文件的名字
我们打开index_jsp.java 文件查看里面的内容：
发现，生成的类继承于HttpJspBase 类。这是一个jsp 文件生成Servlet 程序要继承的基类！！！

![image-20210901100731231](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901100731231.png)

于是，我们关联源代码。去查看一下HttpJspBase 类的内容。从源码的类注释说明中，我们发现。HttpJspBase 这个
类就是所有jsp 文件生成Servlet 程序

需要去继承的基类。并且这个HttpJspBase 类继承于HttpServlet 类。所以jsp 也是一个Servlet 小程序。

![image-20210901100757196](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901100757196.png)

我们分别在工程的WebContent 目录下创建多个jsp 文件。然后依次访问。它们都被翻译为.java 文件并编译成
为.class 字节码文件

![image-20210901100816505](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901100816505.png)

我们打开index_jsp.java 文件查看里面的内容不难发现。jsp 中的html 页面内容都被翻译到Servlet 中的service
方法中直接输出。

![image-20210901100834350](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901100834350.png)

小结：
从生成的文件我们不难发现一个规则。
a.jsp 翻译成java 文件后的全名是a_jsp.java 文件
b.jsp 翻译成java 文件后的全名是b_jsp.java 文件
那么当我们访问一个xxx.jsp 文件后翻译成java 文件的全名是xxx_jsp.java 文件
xxx_jsp.java 文件是一个Servlet 程序。原来jsp 中的html 内容都被翻译到Servlet 类的service 方法中原样输出。

## 3.jsp 的三种语法

### a)jsp 头部的page 指令

jsp 的page 指令可以修改jsp 页面中一些重要的属性，或者行为。

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
```

i. 		language 属性				表示jsp 翻译后是什么语言文件。暂时只支持java。
ii.		 contentType 属性		表示jsp 返回的数据类型是什么。也是源码中response.setContentType()参数值
iii. 		pageEncoding 属性	表示当前jsp 页面文件本身的字符集。
iv.		 import 属性				跟java 源代码中一样。用于导包，导类。
========================两个属性是给out 输出流使用=============================
v. autoFlush 属性				设置当out 输出流缓冲区满了之后，是否自动刷新冲级区。默认值是true。
vi. buffer 属性					设置out 缓冲区的大小。默认是8kb
缓冲区溢出错误：

![image-20210829225250198](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210829225250198.png)

========================两个属性是给out 输出流使用=============================
vii. errorPage 属性				设置当jsp 页面运行时出错，自动跳转去的错误页面路径。
<!--
errorPage 表示错误后自动跳转去的路径<br/>
这个路径一般都是以斜杠打头，它表示请求地址为http://ip:port/工程路径/
映射到代码的Web 目录
-->
viii. 		isErrorPage 属性			设置当前jsp 页面是否是错误信息页面。默认是false。如果是true 可以
获取异常信息。
ix. 			session 属性				设置访问当前jsp 页面，是否会创建HttpSession 对象。默认是true。
x.			 extends 属性				设置jsp 翻译出来的java 类默认继承谁。

### b)jsp 中的常用脚本

**i. 声明脚本(极少使用)**
声明脚本的格式是： <%! 声明java 代码%>
作用：可以给jsp 翻译出来的java 类定义属性和方法甚至是静态代码块。内部类等。

在声明脚本块中，我们可以干4 件事情
1.我们可以定义全局变量。
2.定义static 静态代码块
3.定义方法
4.定义内部类
几乎可以写在类的内部写的代码，都可以通过声明脚本来实现

![image-20210901101108806](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901101108806.png)

练习：
1、声明类属性
2、声明static 静态代码块
3、声明类方法
4、声明内部类
代码示例：

```jsp
<%--1、声明类属性--%>
<%!
private Integer id;
private String name;
private static Map<String,Object> map;
%>
<%--2、声明static 静态代码块--%>
<%!
static {
map = new HashMap<String,Object>();
map.put("key1", "value1");
map.put("key2", "value2");
map.put("key3", "value3");
}
%>
<%--3、声明类方法--%>
<%!
public int abc(){
return 12;
}
%>
<%--4、声明内部类--%>
<%!
public static class A {
private Integer id = 12;
private String abc = "abc";
}
```

%>声明脚本代码翻译对照：

![image-20210829225611221](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210829225611221.png)

**ii. 表达式脚本（常用)**
表达式脚本的格式是：**<%=表达式%>**
表达式脚本的作用是：的jsp 页面上输出数据。
表达式脚本的特点：
1、所有的表达式脚本都会被翻译到_jspService() 方法中
2、表达式脚本都会被翻译成为out.print()输出到页面上
3、由于表达式脚本翻译的内容都在_jspService() 方法中,所以_jspService()方法中的对象都可以直接使用。
4、表达式脚本中的表达式不能以分号结束。
练习：

1. 输出整型
2. 输出浮点型
3. 输出字符串
4. 输出对象
    示例代码：

```jsp
<%=12 %> <br>
<%=12.12 %> <br>
<%="我是字符串" %> <br>
<%=map%> <br>
<%=request.getParameter("username")%>
```

翻译对照：

![image-20210829225816329](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210829225816329.png)

**iii. 代码脚本**
代码脚本的格式是：
<%
java 语句
%>
代码脚本的作用是：可以在jsp 页面中，编写我们自己需要的功能（写的是java 语句）。
代码脚本的特点是：
1、代码脚本翻译之后都在_jspService 方法中
2、代码脚本由于翻译到_jspService()方法中，所以在_jspService()方法中的现有对象都可以直接使用。
3、还可以由多个代码脚本块组合完成一个完整的java 语句。
4、代码脚本还可以和表达式脚本一起组合使用，在jsp 页面上输出数据
练习：

1. 代码脚本----if 语句
2. 代码脚本----for 循环语句
3. 翻译后java 文件中_jspService 方法内的代码都可以写
    示例代码：

```jsp
1. <%--练习：--%>
   <%--1.代码脚本----if 语句--%>
   <%
   int i = 13 ;
   if (i == 12) {
   %>

<h1>国哥好帅</h1>

<%
} else {
%>

<h1>国哥又骗人了！</h1>

<%
}
%>
<br>
<%--2.代码脚本----for 循环语句--%>

<table border="1" cellspacing="0">
<%
for (int j = 0; j < 10; j++) {
%>
<tr>
<td>第<%=j + 1%>行</td>
</tr>
<%
}
%>
</table>

<%--3.翻译后java 文件中_jspService 方法内的代码都可以写--%>
<%
String username = request.getParameter("username");
System.out.println("用户名的请求参数值是：" + username);
%>
```

翻译之后的对比：

![image-20210829230552192](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210829230552192.png)

### c)jsp 中的三种注释

#### i. html 注释

<!-- 这是html 注释-->
html 注释会被翻译到java 源代码中。在_jspService 方法里，以out.writer 输出到客户端。

#### ii. java 注释

<%
// 单行java 注释
/* 多行java 注释*/
%>
java 注释会被翻译到java 源代码中。

#### iii. jsp 注释

<%-- 这是jsp 注释--%>
jsp 注释可以注掉，jsp 页面中所有代码。

## 4.jsp 九大内置对象

jsp 中的内置对象，是指Tomcat 在翻译jsp 页面成为Servlet 源代码后，内部提供的九大对象，叫内置对象。

![image-20210829230922850](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210829230922850.png)

我们打开翻译后的java 文件。查看_jspService 方法。

![image-20210901101717354](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901101717354.png)

**那么jsp 中九大内置对象分别是：**
request 对象	请求对象，可以获取请求信息
response 对象	响应对象。可以设置响应信息
pageContext 对象	当前页面上下文对象。可以在当前上下文保存属性信息
session 对象	会话对象。可以获取会话信息。
exception 对象	异常对象只有在jsp 页面的page 指令中设置isErrorPage="true" 的时候才会存在
application 对象	ServletContext 对象实例，可以获取整个工程的一些信息。
config 对象	ServletConfig 对象实例，可以获取Servlet 的配置信息
out 对象输出流。
page 对象	表示当前Servlet 对象实例（无用，用它不如使用this 对象）。

九大内置对象，都是我们可以在【代码脚本】中或【表达式脚本】中直接使用的对
象。

## 5.jsp 四大域对象

四个域对象分别是：
pageContext 			(PageContextImpl 类) 			当前jsp 页面范围内有效
request 					(HttpServletRequest 类)、			一次请求内有效
session			 		(HttpSession 类)、			一个会话范围内有效（打开浏览器访问服务器，直到关闭浏览器）
application				 (ServletContext 类)			 整个web 工程范围内都有效（只要web 工程不停止，数据都在）
域对象是可以像Map 一样存取数据的对象。四个域对象功能一样。不同的是它们对数据的存取范围。
虽然四个域对象都可以存取数据。在使用上它们是有优先顺序的。
四个域在使用的时候，优先顺序分别是，他们从小到大的范围的顺序。
pageContext ---->>> request ---->>> session ---->>> application
scope.jsp 页面

```jsp
<body>

<h1>scope.jsp 页面</h1>

<%
// 往四个域中都分别保存了数据
pageContext.setAttribute("key", "pageContext");
request.setAttribute("key", "request");
session.setAttribute("key", "session");
application.setAttribute("key", "application");
%>
pageContext 域是否有值：<%=pageContext.getAttribute("key")%> <br>
request 域是否有值：<%=request.getAttribute("key")%> <br>
session 域是否有值：<%=session.getAttribute("key")%> <br>
application 域是否有值：<%=application.getAttribute("key")%> <br>
<%
request.getRequestDispatcher("/scope2.jsp").forward(request,response);
%>
</body>
```

scope2.jsp 页面

```jsp
<body>

<h1>scope2.jsp 页面</h1>

pageContext 域是否有值：<%=pageContext.getAttribute("key")%> <br>
request 域是否有值：<%=request.getAttribute("key")%> <br>
session 域是否有值：<%=session.getAttribute("key")%> <br>
application 域是否有值：<%=application.getAttribute("key")%> <br>
</body>
```

四个作用域的测试代码：
新建两个jsp 页面。分别取名叫：context1.jsp，context2.jsp

1）context1.jsp 的页面代码如下：

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
"http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>
这是context1 页面<br/>
<%
//设置page 域的数据
pageContext.setAttribute("key", "pageContext-value");
//设置request 域的数据
request.setAttribute("key", "request-value");
//设置session 域的数据
session.setAttribute("key", "session-value");
//设置application 域的数据
application.setAttribute("key", "application-value");
%>
<%-- 测试当前页面作用域--%>
<%=pageContext.getAttribute("key") %><br/>
<%=request.getAttribute("key") %><br/>
<%=session.getAttribute("key") %><br/>
<%=application.getAttribute("key") %><br/>
<%
// 测试request 作用域
// request.getRequestDispatcher("/context2.jsp").forward(request, response);
%>
</body>
</html>
```

2）context2.jsp 的页面代码如下：

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
"http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>
这是context2 页面<br/>
<%=pageContext.getAttribute("key") %><br/>
<%=request.getAttribute("key") %><br/>
<%=session.getAttribute("key") %><br/>
<%=application.getAttribute("key") %><br/>
</body>
</html>
```

测试pageContext 作用域步骤：
直接访问context1.jsp 文件
测试request 作用域步骤：
1.在context1.jsp 文件中添加转发到context2.jsp（有数据）
2.直接访问context2.jsp 文件（没有数据）
测试session 作用域步骤：
1.访问完context1.jsp 文件
2.关闭浏览器。但是要保持服务器一直开着
3.打开浏览器，直接访问context2.jsp 文件
测试application 作用域步骤：
1.访问完context1.jsp 文件，然后关闭浏览器
2.停止服务器。再启动服务器。
3.打开浏览器访问context2.jsp 文件

## 6.jsp 中的out 输出和response.getWriter 输出的区别

response 中表示响应，我们经常用于设置返回给客户端的内容（输出）out 也是给用户做输出使用的。

![image-20210829231237856](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210829231237856.png)

由于jsp 翻译之后，底层源代码都是使用out 来进行输出，所以一般情况下。我们在jsp 页面中统一使用out 来进行输出。避
免打乱页面输出内容的顺序。
out.write()			 输出字符串没有问题
out.print() 			输出任意数据都没有问题（都转换成为字符串后调用的write 输出）
**深入源码，浅出结论：在jsp 页面中，可以统一使用out.print()来进行输出**

1） jsp 中out 和response 的writer 的区别演示

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
"http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>
<%
// out 输出
out.write("这是out 的第一次输出<br/>");
// out flush 之后。会把输出的内容写入writer 的缓冲区中
out.flush();
// 最后一次的输出，由于没有手动flush，会在整个页面输出到客户端的时候，自动写入到writer
缓冲区
out.write("这是out 的第二次输出<br/>");
// writer 的输出
response.getWriter().write("这是writer 的第一次输出<br/>");
response.getWriter().write("这是writer 的第二次输出<br/>");
%>
</body>
</html>
```

在浏览器里输入http://127.0.0.1:8080/day09/output.jsp 运行查看的结果：

![image-20210901102343201](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901102343201.png)

2） 图解out 流和writer 流的两个缓冲区如何工作

![image-20210901102407665](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901102407665.png)

## 7.jsp 的常用标签

### a)jsp 静态包含

示例说明：
<%--
<%@ include file=""%> 就是静态包含
file 属性指定你要包含的jsp 页面的路径
地址中第一个斜杠/ 表示为http://ip:port/工程路径/ 映射到代码的web 目录
静态包含的特点：
1、静态包含不会翻译被包含的jsp 页面。
2、静态包含其实是把被包含的jsp 页面的代码拷贝到包含的位置执行输出。
--%>
<%@ include file="/include/footer.jsp"%>

### b)jsp 动态包含

示例说明：
<%--
<jsp:include page=""></jsp:include> 这是动态包含
page 属性是指定你要包含的jsp 页面的路径
动态包含也可以像静态包含一样。把被包含的内容执行输出到包含位置
动态包含的特点：
1、动态包含会把包含的jsp 页面也翻译成为java 代码
2、动态包含底层代码使用如下代码去调用被包含的jsp 页面执行输出。
JspRuntimeLibrary.include(request, response, "/include/footer.jsp", out, false);
3、动态包含，还可以传递参数
--%>

```jsp
<jsp:include page="/include/footer.jsp">
<jsp:param name="username" value="bbj"/>
<jsp:param name="password" value="root"/>
</jsp:include>
```

动态包含的底层原理：

![image-20210829231503650](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210829231503650.png)

### c)jsp 标签-转发 

示例说明：

<%--
<jsp:forward page=""></jsp:forward> 是请求转发标签，它的功能就是请求转发
page 属性设置请求转发的路径
--%>
<jsp:forward page="/scope2.jsp"></jsp:forward>

<jsp:forward 转发功能相当于
request.getRequestDispatcher("/xxxx.jsp").forward(request, response); 的功能。

![image-20210901103045478](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901103045478.png)

在这里需要补充说明一点：我们在工作中，几乎都是使用静态包含。理由很简单。因为jsp 页面虽然可以写java 代
码，做其他的功能操作。但是由于jsp 在开发过程中被定位为专门用来展示页面的技术。也就是说。jsp 页面中，基
本上只有html，css，js。还有一些简单的EL，表达式脚本等输出语句。所以我们都使用静态包含。

## 8、jsp 的练习题

### 练习一：在jsp 页面中输出九九乘法口诀表

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>

<head>
<title>Title</title>
<style type="text/css">
table{
width: 650px;
}
</style>
</head>

<body>
<%-- 练习一：在jsp 页面中输出九九乘法口诀表--%>

<h1 align="center">九九乘法口诀表</h1>
<table align="center">
<%-- 外层循环遍历行--%>
<% for (int i = 1; i <= 9; i++) { %>
<tr>
<%-- 内层循环遍历单元格--%>
<% for (int j = 1; j <= i ; j++) { %>
<td><%=j + "x" + i + "=" + (i*j)%></td>
<% } %>
</tr>
<% } %>
</table>

</body>
</html>
```

![九九乘法口诀表](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/%E4%B9%9D%E4%B9%9D%E4%B9%98%E6%B3%95%E5%8F%A3%E8%AF%80%E8%A1%A8.png)

练习二：jsp 输出一个表格，里面有10 个学生信息。

![image-20210829231622007](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210829231622007.png)

Student 类：

```java
public class Student {
private Integer id;
private String name;
private Integer age;
private String phone;
```

SearchStudentServlet 程序：

```java
public class SearchStudentServlet extends HttpServlet {
@Override
protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException,
IOException {
// 获取请求的参数
// 发sql 语句查询学生的信息
// 使用for 循环生成查询到的数据做模拟
List<Student> studentList = new ArrayList<Student>();
for (int i = 0; i < 10; i++) {
int t = i + 1;
studentList.add(new Student(t,"name"+t, 18+t,"phone"+t));
}
// 保存查询到的结果（学生信息）到request 域中
req.setAttribute("stuList", studentList);
// 请求转发到showStudent.jsp 页面
req.getRequestDispatcher("/test/showStudent.jsp").forward(req,resp);
}
}
```

showStudent.jsp 页面

```jsp
<%@ page import="java.util.List" %>
<%@ page import="com.atguigu.pojo.Student" %>
<%@ page import="java.util.ArrayList" %>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>

<head>
<title>Title</title>
<style>
table{
border: 1px blue solid;
width: 600px;
border-collapse: collapse;
}
td,th{
border: 1px blue solid;
}
</style>
</head>

<body>
<%--练习二：jsp 输出一个表格，里面有10 个学生信息。--%>
<%
List<Student> studentList = (List<Student>) request.getAttribute("stuList");
%>

<table>
<tr>
<td>编号</td>
<td>姓名</td>
<td>年龄</td>
<td>电话</td>
<td>操作</td>
</tr>
<% for (Student student : studentList) { %>
<tr>
<td><%=student.getId()%></td>
<td><%=student.getName()%></td>
<td><%=student.getAge()%></td>
<td><%=student.getPhone()%></td>
<td>删除、修改</td>
</tr>
<% } %>
</table>

</body>
</html>
```

## 9、什么是Listener 监听器？

什么是监听器？监听器就是实时监视一些事物状态的程序，我们称为监听器。
就好像朝阳群众？朝阳区只要有哪个明星有什么不好的事，他们都会知道，然后举报。
那么朝阳群众就是监听器，明星就是被监视的事物，举报就是响应的内容。
又或者说是，电动车的报警器。当报警器锁上的时候。我们去碰电动车，电动车就会报警。
报警器，就是监听器，电动车就是被监视的对象。报警就是响应的内容

1、Listener 监听器它是JavaWeb 的三大组件之一。JavaWeb 的三大组件分别是：Servlet 程序、Filter 过滤器、Listener 监
听器。
2、Listener 它是JavaEE 的规范，就是接口
3、监听器的作用是，监听某种事物的变化。然后通过回调函数，反馈给客户（程序）去做一些相应的处理。

#### ServletContextListener 监听器

ServletContextListener 它可以监听ServletContext 对象的创建和销毁。
ServletContext 对象在web 工程启动的时候创建，在web 工程停止的时候销毁。
监听到创建和销毁之后都会分别调用ServletContextListener 监听器的方法反馈。
两个方法分别是：

```java
public interface ServletContextListener extends EventListener {
/**

* 在ServletContext 对象创建之后马上调用，做初始化
  */
  public void contextInitialized(ServletContextEvent sce);
  /**
* 在ServletContext 对象销毁之后调用
  */
  public void contextDestroyed(ServletContextEvent sce);
  }
```

如何使用ServletContextListener 监听器监听ServletContext 对象。
使用步骤如下：
1、编写一个类去实现ServletContextListener
2、实现其两个回调方法
3、到web.xml 中去配置监听器
监听器实现类：

```java
public class MyServletContextListenerImpl implements ServletContextListener {
@Override
public void contextInitialized(ServletContextEvent sce) {
System.out.println("ServletContext 对象被创建了");
}
@Override
public void contextDestroyed(ServletContextEvent sce) {
System.out.println("ServletContext 对象被销毁了");
}
}
```

web.xml 中的配置：

```xml
<!--配置监听器-->
<listener>
<listener-class>com.atguigu.listener.MyServletContextListenerImpl</listener-class>
</listener>
```

javax.servlet.ServletContextListener ServletContext 监听器
监听器的使用步骤。
第一步：我们需要定义一个类。然后去继承生命周期的监听器接口。
第二步：然后在Web.xml 文件中配置。
ServletContextListener 监听器，一定要在web.xml 文件中配置之后才会生效
<listener>
<listener-class>全类名</listener-class>
</listener>
生命周期监听器两个方法：
public void contextInitialized(ServletContextEvent sce) 是ServletContext 对象的
创建回调
public void contextDestroyed(ServletContextEvent sce) 是ServletContext 对象的销
毁回调

1）创建一个ServletContextListenerImpl 类实现ServletContextListener 接口。

```java
import javax.servlet.ServletContextEvent;
import javax.servlet.ServletContextListener;
“玩转”Java 系列
public class ServletContextListenerImpl implements ServletContextListener {
@Override
public void contextInitialized(ServletContextEvent sce) {
System.out.println("ServletContext 对象被创建了");
}
@Override
public void contextDestroyed(ServletContextEvent sce) {
System.out.println("ServletContext 对象被销毁了");
}
}
```

2）在web.xml 文件中的配置如下：

```xml
<listener>
<listener-class>com.atguigu.listener.RequestListener</listener-class>
</listener>
```

3）这个时候，启动web 工程和正常停止web 工程，后台都会如下打印：

![image-20210901102832368](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/Jsp/image-20210901102832368.png)
