# **java前端三件套**

## **HTML**

### 1.B/S 软件的结构

> J**avaSE C/S  Client Server**
> **B/S  Browser Server**

![image-20210708164746359](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708164746359.png)

### 2.前端的开发流程

![image-20210708164827919](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708164827919.png)

### 3.网页的组成部分

>页面由三部分内容组成！
>分别是内容（结构）、表现、行为。
>内容（结构），是我们在页面中可以看到的数据。我们称之为内容。一般内容我们使用
>html 技术来展示。
>表现，指的是这些内容在页面上的展示形式。比如说。布局，颜色，大小等等。一般使用
>CSS 技术实现
>行为，指的是页面中元素与输入设备交互的响应。一般使用javascript 技术实现。

### 4.HTML简介

> Hyper Text Markup Language （超文本标记语言） 简写：HTML
> HTML 通过标签来标记要显示的网页中的各个部分。网页文件本身是一种文本文件，
> 通过在文本文件中添加标记符，可以告诉浏览器如何显示其中的内容（如：文字如何处理，画
> 面如何安排，图片如何显示等）

### 5.创建HTML文件

1.创建一个web工程(静态web工程)

![image-20210708165135337](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708165135337.png)

![image-20210708165145122](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708165145122.png)

![image-20210708165150242](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708165150242.png)

2.在工程下创建HTML页面

![image-20210708165231847](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708165231847.png)

选择浏览器执行页面

![image-20210708165309274](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708165309274.png)

第一个html事例：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>标题</title>
</head>
<body>
hello
</body>
</html>
```

注：Java 文件是需要先编译，再由java 虚拟机跑起来。但HTML 文件它不需要编译，直接由浏览器进行解析执行。

### 6.HTML文件的书写规范

``` html
<html> 表示整个html 页面的开始
<head> 头信息
<title>标题</title> 标题
</head>
<body> body 是页面的主体内容
页面主体内容
</body>
</html> 表示整个html 页面的结束
Html 的代码注释<!-- 这是html 注释，可以在页面右键查看源代码中看到-->
```

### 7.HTML标签介绍

>1.标签的格式:
><标签名>封装的数据</标签名>
>2.标签名大小写不敏感。
>3.标签拥有自己的属性。
>i. 分为基本属性：bgcolor="red" 可以修改简单的样式效果
>ii. 事件属性： onclick="alert('你好！');" 可以直接设置事件响应后的代码。
>4.标签又分为，单标签和双标签。
>i. 单标签格式： <标签名/> br 换行hr 水平线
>ii. 双标签格式: <标签名> ...封装的数据...</标签名>

![image-20210708165740365](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708165740365.png)

``` html
标签的语法：
<body>
<!-- ①标签不能交叉嵌套-->
正确：<div><span>早安，尚硅谷</span></div>
错误：<div><span>早安，尚硅谷</div></span>
<hr />
<!-- ②标签必须正确关闭-->
<!-- i.有文本内容的标签： -->
正确：<div>早安，尚硅谷</div>
错误：<div>早安，尚硅谷
<hr />
<!-- ii.没有文本内容的标签： -->
正确：<br />
错误：<br>
<hr />
<!-- ③属性必须有值，属性值必须加引号-->
正确：<font color="blue">早安，尚硅谷</font>
错误：<font color=blue>早安，尚硅谷</font>
错误：<font color>早安，尚硅谷</font>
<hr />
<!-- ④注释不能嵌套-->
正确：<!-- 注释内容--> <br/>
错误：<!-- <!-- 这是错误的html 注释--> -->
<hr />
    </body>
注意事项：
1.html 代码不是很严谨。有时候标签不闭合，也不会报错。
```

### 8. 常用的标签介绍

#### 8.1 font字体标签

``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>1.font标签.html</title>
</head>
<body>
	<!-- 字体标签
	 需求1：在网页上显示 我是字体标签 ，并修改字体为 宋体，颜色为红色。

	 font标签是字体标签,它可以用来修改文本的字体,颜色,大小(尺寸)
	 	color属性修改颜色
	 	face属性修改字体
	 	size属性修改文本大小
	 -->
	<font color="red" face="宋体" size="7">我是字体标签</font>
</body>
</html>
```

#### 8.2 特殊字符

>需求1：把<br>换行标签变成文本转换成字符显示在页面上

常用的特殊字符表：

![image-20210708171250221](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708171250221.png)

其他特殊字符表：

![image-20210708171331846](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708171331846.png)

``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>2.特殊字符.html</title>
</head>
<body>
	<!-- 特殊字符
	需求1：把 <br> 换行标签 变成文本 转换成字符显示在页面上

	常用的特殊字符:
		<	===>>>>		&lt;
		>   ===>>>>		&gt;
	  空格	===>>>>		&nbsp;

	 -->
	我是&lt;br&gt;标签<br/>
	国哥好&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;帅啊!
</body>
</html>
```

#### 8.3 标题标签

> 标题标签是h1到h6

需求1：演示标题h1到标题h6

``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>3.标题标签.html</title>
</head>
<body>
	<!-- 标题标签
	 需求1：演示标题1到 标题6的

	 	h1 - h6 都是标题标签
	 	h1 最大
	 	h6 最小
			align 属性是对齐属性
				left		左对齐(默认)
				center		剧中
				right		右对齐
	 -->
	<h1 align="left">标题1</h1>
	<h2 align="center">标题2</h2>
	<h3 align="right">标题3</h3>
	<h4>标题4</h4>
	<h5>标题5</h5>
	<h6>标题6</h6>
	<h7>标题7</h7>
</body>
</html>
```

#### 8.4 超链接（重点）

> 在网页中所有点击之后可以跳转的内容都是超连接

需求1：普通的 超链接。

``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>4.超链接.html</title>
</head>
<body>
	<!-- a标签是 超链接
	 		href属性设置连接的地址
	 		target属性设置哪个目标进行跳转
	 			_self		表示当前页面(默认值)
	 			_blank		表示打开新页面来进行跳转
	 -->
	<a href="http://localhost:8080">百度</a><br/>
	<a href="http://localhost:8080" target="_self">百度_self</a><br/>
	<a href="http://localhost:8080" target="_blank">百度_blank</a><br/>
</body>
</html>
```

#### 8.5 列表标签

> 无序列表 
>
> 有序列表

需求1：使用无序，列表方式，把东北F4，赵四，刘能，小沈阳，宋小宝，展示出来

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <!--需求1：使用无序，列表方式，把东北F4，赵四，刘能，小沈阳，宋小宝，展示出来
        ul 是无序列表
            type属性可以修改列表项前面的符号
        li  是列表项
    -->
    <ul type="none">
        <li>赵四</li>
        <li>刘能</li>
        <li>小沈阳</li>
        <li>宋小宝</li>
    </ul>
</body>
</html>
```

#### 8.6 img标签

> img标签可以在html页面上显示图片

需求1：使用img 标签显示一张美女的照片。并修改宽高，和边框属性

``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>5.img标签.html</title>
</head>
<body>
    <!--需求1：使用img标签显示一张美女的照片。并修改宽高，和边框属性

        img标签是图片标签,用来显示图片
            src属性可以设置图片的路径
            width属性设置图片的宽度
            height属性设置图片的高度
            border属性设置图片边框大小
            alt属性设置当指定路径找不到图片时,用来代替显示的文本内容

        在JavaSE中路径也分为相对路径和绝对路径.
            相对路径:从工程名开始算

            绝对路径:盘符:/目录/文件名

        在web中路径分为相对路径和绝对路径两种
            相对路径:
                .           表示当前文件所在的目录
                ..          表示当前文件所在的上一级目录
                文件名      表示当前文件所在目录的文件,相当于 ./文件名            ./ 可以省略

            绝对路径:
                正确格式是:  http://ip:port/工程名/资源路径

                错误格式是:  盘符:/目录/文件名
    -->
    <img src="1.jpg" width="200" height="260" border="1" alt="美女找不到"/>
    <img src="../../2.jpg" width="200" height="260" />
    <img src="../imgs/3.jpg" width="200" height="260" />
    <img src="../imgs/4.jpg" width="200" height="260" />
    <img src="../imgs/5.jpg" width="200" height="260" />
    <img src="../imgs/6.jpg" width="200" height="260" />
</body>
</html>
```

#### 8.7 表格标签（重点）

![image-20210708172250372](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708172250372.png)

需求1：做一个带表头的，三行，三列的表格，并显示边框
需求2：修改表格的宽度，高度，表格的对齐方式，单元格间距。

``` html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <title>表格标签</title>
</head>
<body>
<!--
	需求1：做一个 带表头的 ，三行，三列的表格，并显示边框
	需求2：修改表格的宽度，高度，表格的对齐方式，单元格间距。

		table 标签是表格标签
			border 设置表格标签
			width 设置表格宽度
			height 设置表格高度
			align 设置表格相对于页面的对齐方式
			cellspacing 设置单元格间距

		tr	 是行标签
		th	是表头标签
		td  是单元格标签
			align 设置单元格文本对齐方式

		b 是加粗标签

	-->

<table align="center" border="1" width="300" height="300" cellspacing="0">
    <tr>
        <th>1.1</th>
        <th>1.2</th>
        <th>1.3</th>
    </tr>
    <tr>
        <td>2.1</td>
        <td>2.2</td>
        <td>2.3</td>
    </tr>
    <tr>
        <td>3.1</td>
        <td>3.2</td>
        <td>3.3</td>
    </tr>
</table>
</body>
</html>
```

#### 8.8 跨行跨列表格（次重点）

![image-20210708172414306](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708172414306.png)

需求1：新建一个五行，五列的表格，第一行，第一列的单元格要跨两列，第二行第一列的单元格跨两行，第四行第四列的单元格跨两行两列。

``` html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
	<head>
		<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
		<title>7.表格的跨行跨列</title>
	</head>
	<body>
<!--	需求1：
			新建一个五行，五列的表格，
			第一行，第一列的单元格要跨两列，
			第二行第一列的单元格跨两行，
			第四行第四列的单元格跨两行两列。

			colspan 属性设置跨列
			rowspan 属性设置跨行
			-->

		<table width="500" height="500" cellspacing="0" border="1">
			<tr>
				<td colspan="2">1.1</td>
				<td>1.3</td>
				<td>1.4</td>
				<td>1.5</td>
			</tr>
			<tr>
				<td rowspan="2">2.1</td>
				<td>2.2</td>
				<td>2.3</td>
				<td>2.4</td>
				<td>2.5</td>
			</tr>
			<tr>
				<td>3.2</td>
				<td>3.3</td>
				<td>3.4</td>
				<td>3.5</td>
			</tr>
			<tr>
				<td>4.1</td>
				<td>4.2</td>
				<td>4.3</td>
				<td colspan="2" rowspan="2">4.4</td>
			</tr>
			<tr>
				<td>5.1</td>
				<td>5.2</td>
				<td>5.3</td>
			</tr>
		</table>
	</body>
</html>
```

#### 8.9 了解iframe框架标签（内嵌窗口）

ifarme 标签它可以在一个html 页面上,打开一个小窗口,去加载一个单独的页面.

``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>8.iframe标签.html</title>
</head>
<body>
	我是一个单独的完整的页面<br/><br/>
    <!--ifarme标签可以在页面上开辟一个小区域显示一个单独的页面
            ifarme和a标签组合使用的步骤:
                1 在iframe标签中使用name属性定义一个名称
                2 在a标签的target属性上设置iframe的name的属性值
    -->
    <iframe src="3.标题标签.html" width="500" height="400" name="abc"></iframe>
    <br/>

    <ul>
        <li><a href="0-标签语法.html" target="abc">0-标签语法.html</a></li>
        <li><a href="1.font标签.html" target="abc">1.font标签.html</a></li>
        <li><a href="2.特殊字符.html" target="abc">2.特殊字符.html</a></li>
    </ul>
</body>
</html>
```

#### 8.10 表单标签（重点）

什么是表单?
表单就是html 页面中,用来收集用户信息的所有元素集合.然后把这些信息发送给服务器.
![image-20210708172721254](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708172721254.png)

需求1:创建一个个人信息注册的表单界面。包含用户名，密码，确认密码。性别（单选），兴趣爱好（多选），国籍（下拉列表）。
隐藏域，自我评价（多行文本域）。重置，提交。

表单的显示:

``` html 
<body>
<!--需求1:创建一个个人信息注册的表单界面。包含用户名，密码，确认密码。性别（单选），兴趣爱好（多选），国籍（下拉列表）。
隐藏域，自我评价（多行文本域）。重置，提交。-->
<!--
form 标签就是表单
input type=text 是文件输入框value 设置默认显示内容
input type=password 是密码输入框value 设置默认显示内容
input type=radio 是单选框name 属性可以对其进行分组checked="checked"表示默认选中
input type=checkbox 是复选框checked="checked"表示默认选中
input type=reset 是重置按钮value 属性修改按钮上的文本
input type=submit 是提交按钮value 属性修改按钮上的文本
input type=button 是按钮value 属性修改按钮上的文本
input type=file 是文件上传域
input type=hidden 是隐藏域当我们要发送某些信息，而这些信息，不需要用户参与，就可以使用隐藏域（提交的
时候同时发送给服务器）
select 标签是下拉列表框
option 标签是下拉列表框中的选项selected="selected"设置默认选中
textarea 表示多行文本输入框（起始标签和结束标签中的内容是默认值）
rows 属性设置可以显示几行的高度
cols 属性设置每行可以显示几个字符宽度
-->
<form>
用户名称：<input type="text" value="默认值"/><br/>
用户密码：<input type="password" value="abc"/><br/>
确认密码：<input type="password" value="abc"/><br/>
性别：<input type="radio" name="sex"/>男<input type="radio" name="sex" checked="checked" />女<br/>
兴趣爱好：<input type="checkbox" checked="checked" />Java<input type="checkbox" />JavaScript<input
type="checkbox" />C++<br/>
国籍：<select>
<option>--请选择国籍--</option>
<option selected="selected">中国</option>
<option>美国</option>
<option>小日本</option>
</select><br/>
自我评价：<textarea rows="10" cols="20">我才是默认值</textarea><br/>
<input type="reset" value="abc" />
<input type="submit"/>
</form>
</body>
```

表单格式化：

``` html
<form>
<h1 align="center">用户注册</h1>
<table align="center">
<tr>
<td> 用户名称：</td>
<td>
<input type="text" value="默认值"/>
</td>
</tr>
<tr>
<td> 用户密码：</td>
<td><input type="password" value="abc"/></td>
</tr>
<tr>
<td>确认密码：</td>
<td><input type="password" value="abc"/></td>
</tr>
<tr>
<td>性别：</td>
<td>
<input type="radio" name="sex"/>男
<input type="radio" name="sex" checked="checked" />女
</td>
</tr>
<tr>
<td> 兴趣爱好：</td>
<td>
<input type="checkbox" checked="checked" />Java
<input type="checkbox" />JavaScript
<input type="checkbox" />C++
</td>
</tr>
<tr>
<td>国籍：</td>
<td>
<select>
<option>--请选择国籍--</option>
<option selected="selected">中国</option>
<option>美国</option>
<option>小日本</option>
</select>
</td>
</tr>
<tr>
<td>自我评价：</td>
<td><textarea rows="10" cols="20">我才是默认值</textarea></td>
</tr>
<tr>
<td><input type="reset" /></td>
<td align="center"><input type="submit"/></td>
</tr>
</table>
</form>
</body>
```

表单提交细节:

``` html
<body>
<!--
form 标签是表单标签
action 属性设置提交的服务器地址
method 属性设置提交的方式GET(默认值)或POST
表单提交的时候，数据没有发送给服务器的三种情况：
1、表单项没有name 属性值
2、单选、复选（下拉列表中的option 标签）都需要添加value 属性，以便发送给服务器
3、表单项不在提交的form 标签中
GET 请求的特点是：
1、浏览器地址栏中的地址是：action 属性[+?+请求参数]
请求参数的格式是：name=value&name=value
2、不安全
3、它有数据长度的限制
POST 请求的特点是：
1、浏览器地址栏中只有action 属性值
2、相对于GET 请求要安全
3、理论上没有数据长度的限制
-->
<form action="http://localhost:8080" method="post">
<input type="hidden" name="action" value="login" />
<h1 align="center">用户注册</h1>
<table align="center">
<tr>
<td> 用户名称：</td>
<td>
<input type="text" name="username" value="默认值"/>
</td>
</tr>
<tr>
<td> 用户密码：</td>
<td><input type="password" name="password" value="abc"/></td>
</tr>
<tr>
<td>性别：</td>
<td>
<input type="radio" name="sex" value="boy"/>男
<input type="radio" name="sex" checked="checked" value="girl" />女
</td>
</tr>
<tr>
<td> 兴趣爱好：</td>
<td>
<input name="hobby" type="checkbox" checked="checked" value="java"/>Java
<input name="hobby" type="checkbox" value="js"/>JavaScript
<input name="hobby" type="checkbox" value="cpp"/>C++
</td>
</tr>
<tr>
<td>国籍：</td>
<td>
<select name="country">
<option value="none">--请选择国籍--</option>
<option value="cn" selected="selected">中国</option>
<option value="usa">美国</option>
<option value="jp">小日本</option>
</select>
</td>
</tr>
<tr>
<td>自我评价：</td>
<td><textarea name="desc" rows="10" cols="20">我才是默认值</textarea></td>
</tr>
<tr>
<td><input type="reset" /></td>
<td align="center"><input type="submit"/></td>
</tr>
</table>
</form>
</body>
```

#### 8.11 其他标签

需求1：div、span、p 标签的演示

``` html
<body>
<!--需求1：div、span、p 标签的演示
div 标签默认独占一行
span 标签它的长度是封装数据的长度
p 段落标签默认会在段落的上方或下方各空出一行来（如果已有就不再空）
-->
<div>div 标签1</div>
<div>div 标签2</div>
<span>span 标签1</span>
<span>span 标签2</span>
<p>p 段落标签1</p>
<p>p 段落标签2</p>
</body>
HTML 最后的练习2,：创建登录的表单，包含用户名，密码框输入。并结合table 标签排版。让它看上去整齐点
```

## CSS

### 1.CSS技术介绍

> CSS 是「层叠样式表单」。是用于(增强)控制网页样式并允许将样式信息与网页内容分离的一种标记性语言。

### 2. CSS语法规则

![image-20210708173451923](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708173451923.png)

>选择器：浏览器根据“选择器”决定受CSS 样式影响的HTML 元素（标签）。
>属性(property) 是你要改变的样式名，并且每个属性都有一个值。属性和值被冒号分开，并
>由花括号包围，这样就组成了一个完整的样式声明（declaration），例如：p {color: blue}
>多个声明：如果要定义不止一个声明，则需要用分号将每个声明分开。虽然最后一条声明的
>最后可以不加分号(但尽量在每条声明的末尾都加上分号)
>例如：
>p{
>color:red;
>font-size:30px;
>}
>注：一般每行只描述一个属性
>CSS 注释：/*注释内容*/

### 3. CSS和HTML的结合方式

#### 3.1 第一种

> 在标签的style 属性上设置”key:value value;”，修改标签样式。

需求1：分别定义两个div、span 标签，分别修改每个div 标签的样式为：边框1 个像素，实线，红色。

``` html
<div>div 标签1</div>
<div>div 标签2</div>
<span>span 标签1</span>
<span>span 标签2</span>
```



``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
</head>
<body>
<!--需求1：分别定义两个div、span 标签，分别修改每个div 标签的样式为：边框1 个像素，实线，红色。-->
<div style="border: 1px solid red;">div 标签1</div>
<div style="border: 1px solid red;">div 标签2</div>
<span style="border: 1px solid red;">span 标签1</span>
<span style="border: 1px solid red;">span 标签2</span>
</body>
</html>
```

> 问题：这种方式的缺点？
> 1.如果标签多了。样式多了。代码量非常庞大。
> 2.可读性非常差。
> 3.Css 代码没什么复用性可方言。

#### 3.2 第二种

> 在head 标签中，使用style 标签来定义各种自己需要的css 样式。
> 格式如下：
> xxx {
> Key : value value;
> }

需求1：分别定义两个div、span 标签，分别修改每个div 标签的样式为：边框1 个像素，实线，红色。

``` html
<div>div 标签1</div>
<div>div 标签2</div>
<span>span 标签1</span>
<span>span 标签2</span>
```



``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<!--style 标签专门用来定义css 样式代码-->
<style type="text/css">
/* 需求1：分别定义两个div、span 标签，分别修改每个div 标签的样式为：边框1 个像素，实线，红色。*/
div{
border: 1px solid red;
}
span{
border: 1px solid red;
}
</style>
</head>
<body>
<div>div 标签1</div>
<div>div 标签2</div>
<span>span 标签1</span>
<span>span 标签2</span>
</body>
</html>
```

> Css 注释/* 这是css 的代码注释*/
> 问题：这种方式的缺点。
> 1.只能在同一页面内复用代码，不能在多个页面中复用css 代码。
> 2.维护起来不方便，实际的项目中会有成千上万的页面，要到每个页面中去修改。工作量太大了。

#### 3.3 第三种

> 把css 样式写成一个单独的css 文件，再通过link 标签引入即可复用。
> 使用html 的<link rel="stylesheet" type="text/css" href="./styles.css" /> 标签导入css 样
> 式文件。

1.css文件内容：

``` html
div{
border: 1px solid yellow;
}
span{
border: 1px solid red;
}
```

html文件代码：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<!--link 标签专门用来引入css 样式代码-->
<link rel="stylesheet" type="text/css" href="1.css"/>
</head>
<body>
<div>div 标签1</div>
<div>div 标签2</div>
<span>span 标签1</span>
<span>span 标签2</span>
</body>
</html>
```

### 4.css 选择器

#### 4.1 标签名选择器

> 标签名选择器的格式是：
> 标签名{
> 属性：值;
> }
> 标签名选择器，可以决定哪些标签被动的使用这个样式。

``` html
<div>div 标签1</div>
<div>div 标签2</div>
<span>span 标签1</span>
<span>span 标签2</span>
```

需求1：在所有div 标签上修改字体颜色为蓝色，字体大小30 个像素。边框为1 像素黄色实线。
并且修改所有span 标签的字体颜色为黄色，字体大小20 个像素。边框为5 像素蓝色虚线。

示例代码：

``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>CSS 选择器</title>
<style type="text/css">
div{
border: 1px solid yellow;
color: blue;
font-size: 30px;
}
span{
border: 5px dashed blue;
color: yellow;
font-size: 20px;
}
</style>
</head>
<body>
<!--
需求1：在所有div 标签上修改字体颜色为蓝色，字体大小30 个像素。边框为1 像素黄色实线。
并且修改所有span 标签的字体颜色为黄色，字体大小20 个像素。边框为5 像素蓝色虚线。
-->
<div>div 标签1</div>
<div>div 标签2</div>
<span>span 标签1</span>
<span>span 标签2</span>
</body>
</html>
```

#### 4.2 id 选择器

> id 选择器的格式是：
> #id 属性值{
> 属性：值;
> }
> id 选择器，可以让我们通过id 属性选择性的去使用这个样式。

需求1：分别定义两个div 标签，
第一个div 标签定义id 为id001 ，然后根据id 属性定义css 样式修改字体颜色为蓝色，
字体大小30 个像素。边框为1 像素黄色实线。
第二个div 标签定义id 为id002 ，然后根据id 属性定义css 样式修改的字体颜色为红色，字体大小20 个像
素。边框为5 像素蓝色点线。

``` html
<div id="id001">div 标签1</div>
<div id="id002">div 标签2</div>
```

示例代码：

``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>ID 选择器</title>
<style type="text/css">
#id001{
color: blue;
font-size: 30px;
border: 1px yellow solid;
}
#id002{
color: red;
font-size: 20px;
border: 5px blue dotted ;
}
</style>
</head>
<body>
<!--
需求1：分别定义两个div 标签，
第一个div 标签定义id 为id001 ，然后根据id 属性定义css 样式修改字体颜色为蓝色，
字体大小30 个像素。边框为1 像素黄色实线。
第二个div 标签定义id 为id002 ，然后根据id 属性定义css 样式修改的字体颜色为红色，字体大小20 个像素。
边框为5 像素蓝色点线。
-->
<div id="id002">div 标签1</div>
<div id="id001">div 标签2</div>
</body>
</html>
```

#### 4.3 class 选择器

> class 类型选择器的格式是：
> .class 属性值{
> 属性：值;
> }
> class 类型选择器，可以通过class 属性有效的选择性地去使用这个样式。

需求1：修改class 属性值为class01 的span 或div 标签，字体颜色为蓝色，字体大小30 个像素。边框为1 像素黄色实线。
需求2：修改class 属性值为class02 的div 标签，字体颜色为灰色，字体大小26 个像素。边框为1 像素红色实线。

``` html
<div class="class01">div 标签class01</div>
<div class="class02">div 标签</div>
<span class="class01">span 标签class01</span>
<span>span 标签2</span>
```



``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>class 类型选择器</title>
<style type="text/css">
.class01{
color: blue;
font-size: 30px;
border: 1px solid yellow;
}
.class02{
color: grey;
font-size: 26px;
border: 1px solid red;
}
</style>
</head>
<body>
<!--
需求1：修改class 属性值为class01 的span 或div 标签，字体颜色为蓝色，字体大小30 个像素。边框为1 像素黄色实线。
需求2：修改class 属性值为class02 的div 标签，字体颜色为灰色，字体大小26 个像素。边框为1 像素红色实线。
-->
<div class="class02">div 标签class01</div>
<div class="class02">div 标签</div>
<span class="class02">span 标签class01</span>
<span>span 标签2</span>
</body>
</html>
```

#### 4.4 组合选择器

> 组合选择器的格式是：
> 选择器1，选择器2，选择器n{
> 属性：值;
> }
> 组合选择器可以让多个选择器共用同一个css 样式代码。

``` html
<div class="class01">div 标签class01</div> <br />
<span id="id01">span 标签</span> <br />
<div>div 标签</div> <br />
<div>div 标签id01</div> <br />
```

需求1：修改class="class01" 的div 标签和id="id01" 所有的span 标签，字体颜色为蓝色，字体大小20 个像素。
边框为1 像素黄色实线。
示例代码：

``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>class 类型选择器</title>
<style type="text/css">
.class01 , #id01{
color: blue;
font-size: 20px;
border: 1px yellow solid;
}
</style>
</head>
<body>
<!--
需求1：修改class="class01" 的div 标签和id="id01" 所有的span 标签，
字体颜色为蓝色，字体大小20 个像素。边框为1 像素黄色实线。
-->
<div id="id01">div 标签class01</div> <br />
<span >span 标签</span> <br />
<div>div 标签</div> <br />
<div>div 标签id01</div> <br />
</body>
</html>
```

### 5. 常用样式

``` html
1、字体颜色
color：red；
颜色可以写颜色名如：black, blue, red, green 等
颜色也可以写rgb 值和十六进制表示值：如rgb(255,0,0)，#00F6DE，如果写十六进制值必
须加#
2、宽度
width:19px;
宽度可以写像素值：19px；
也可以写百分比值：20%；
3、高度
height:20px;
高度可以写像素值：19px；
也可以写百分比值：20%；
4、背景颜色
background-color:#0F2D4C
4、字体样式：
color：#FF0000；字体颜色红色
font-size：20px; 字体大小
5、红色1 像素实线边框
border：1px solid red;
7、DIV 居中
margin-left: auto;
margin-right: auto;
8、文本居中：
text-align: center;
9、超连接去下划线
text-decoration: none;
10、表格细线
table {
border: 1px solid black; /*设置边框*/
border-collapse: collapse; /*将边框合并*/
}
td,th {
border: 1px solid black; /*设置边框*/
}
11、列表去除修饰
ul {
list-style: none;
}
```

示例代码：

``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>06-css 常用样式.html</title>
<style type="text/css">
div{
color: red;
border: 1px yellow solid;
width: 300px;
height: 300px;
background-color: green;
font-size: 30px;
margin-left: auto;
margin-right: auto;
text-align: center;
}
table{
border: 1px red solid;
border-collapse: collapse;
}
td{
border: 1px red solid;
}
a{
text-decoration: none;
}
ul{
list-style: none;
}
</style>
</head>
<body>
<ul>
<li>11111111111</li>
<li>11111111111</li>
<li>11111111111</li>
<li>11111111111</li>
<li>11111111111</li>
</ul>
<table>
<tr>
<td>1.1</td>
<td>1.2</td>
</tr>
</table>
<a href="http://www.baidu.com">百度</a>
<div>我是div 标签</div>
</body>
</html>
```

## JavaScript

### 1. JavaScript介绍

> **Javascript 语言诞生主要是完成页面的数据验证**。因此它运行在客户端，需要运行浏览器来解析执行**JavaScript** 代码。
> JS 是Netscape 网景公司的产品，最早取名为LiveScript;为了吸引更多java 程序员。更名为JavaScript。
> JS 是弱类型，Java 是强类型。
> 特点：
>
> 1. 交互性（它可以做的就是信息的动态交互）
> 2. 安全性（不允许直接访问本地硬盘）
> 3. 跨平台性（只要是可以解释JS 的浏览器都可以执行，和平台无关）

### 2. JavaScript和HTML代码的结合方式

#### 2.1 第一种方式

只需要在head 标签中，或者在body 标签中， 使用script 标签来书写JavaScript 代码

示例代码：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
// alert 是JavaScript 语言提供的一个警告框函数。
// 它可以接收任意类型的参数，这个参数就是警告框的提示信息
alert("hello javaScript!");
</script>
</head>
<body>
</body>
</html>
```

#### 2.2 第二种方式

使用script 标签引入单独的JavaScript 代码文件

文件目录：

![image-20210708180153502](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708180153502.png)

html 代码内容：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<!--
现在需要使用script 引入外部的js 文件来执行
src 属性专门用来引入js 文件路径（可以是相对路径，也可以是绝对路径）
script 标签可以用来定义js 代码，也可以用来引入js 文件
但是，两个功能二选一使用。不能同时使用两个功能
-->
<script type="text/javascript" src="1.js"></script>
<script type="text/javascript">
alert("国哥现在可以帅了");
</script>
</head>
<body>
</body>
</html>
```

### 4. 变量

> JavaScript 的变量类型：
> 数值类型： number
> 字符串类型： string
> 对象类型： object
> 布尔类型： boolean
> 函数类型： function
> JavaScript 里特殊的值：
> undefined 未定义，所有js 变量未赋于初始值的时候，默认值都是undefined.
> null 空值
> NaN 全称是：Not a Number。非数字。非数值。
> **JS 中的定义变量格式：**
> **var 变量名;**
> **var 变量名= 值;**

示例代码：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
var i;
// alert(i); // undefined
i = 12;
// typeof()是JavaScript 语言提供的一个函数。
// alert( typeof(i) ); // number
i = "abc";
// 它可以取变量的数据类型返回
// alert( typeof(i) ); // String
var a = 12;
var b = "abc";
alert( a * b ); // NaN 是非数字，非数值。
</script>
</head>
<body>
</body>
</html>
```

### 5. 关系（比较）运算

> 等于： == 等于是简单的做字面值的比较
> 全等于： === 除了做字面值的比较之外，还会比较两个变量的数据类型

示例代码：

``` html 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
var a = "12";
var b = 12;
alert( a == b ); // true
alert( a === b ); // false
</script>
</head>
<body>
</body>
</html>
```

### 6. 逻辑运算

> 且运算： &&
> 或运算： ||
> 取反运算： !
> 在JavaScript 语言中，所有的变量，都可以做为一个boolean 类型的变量去使用。
> 0 、null、undefined、””(空串) 都认为是false；
> /*
> && 且运算。
> 有两种情况：
> 第一种：当表达式全为真的时候。返回最后一个表达式的值。
> 第二种：当表达式中，有一个为假的时候。返回第一个为假的表达式的值
> || 或运算
> 第一种情况：当表达式全为假时，返回最后一个表达式的值
> 第二种情况：只要有一个表达式为真。就会把回第一个为真的表达式的值
> 并且&& 与运算和||或运算有短路。
> 短路就是说，当这个&&或||运算有结果了之后。后面的表达式不再执行
> */

``` html 
var a = "abc";
var b = true;
var d = false;
var c = null;
```

示例代码：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
/* 在JavaScript 语言中，所有的变量，都可以做为一个boolean 类型的变量去使用。
0 、null、undefined、””(空串) 都认为是false；*/
// var a = 0;
// if (a) {
// alert("零为真");
// } else {
// alert("零为假");
// }
// var b = null;
// if (b) {
// alert("null 为真");
// } else {
// alert("null 为假");
// }
// var c = undefined;
// if (c) {
// alert("undefined 为真");
// } else {
// alert("undefined 为假");
// }
// var d = "";
// if (d) {
// alert("空串为真");
// } else {
// alert("空串为假");
// }
/* && 且运算。
有两种情况：
第一种：当表达式全为真的时候。返回最后一个表达式的值。
第二种：当表达式中，有一个为假的时候。返回第一个为假的表达式的值*/
var a = "abc";//真
var b = true;
var c = null;//假
var d = false;
    
// alert( a && b );//true
// alert( b && a );//true
// alert( a && d ); // false
// alert( a && c ); // null
/* || 或运算
第一种情况：当表达式全为假时，返回最后一个表达式的值
第二种情况：只要有一个表达式为真。就会把回第一个为真的表达式的值*/
// alert( d || c ); // null
// alert( c|| d ); //false
// alert( a || c ); //abc
// alert( b || c ); //true
</script>
</head>
<body>
</body>
</html>
```

### 7. 数组（重点）

#### 7.1 数组定义方式

> JS 中数组的定义：
> 格式：
> var 数组名= []; // 空数组
> var 数组名= [1 , ’abc’ , true]; // 定义数组同时赋值元素

示例代码：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
var arr = [true,1]; // 定义一个空数组
// alert( arr.length ); // 0
arr[0] = 12;
// alert( arr[0] );//12
// alert( arr.length ); // 0
// javaScript 语言中的数组，只要我们通过数组下标赋值，那么最大的下标值，就会自动的给数组做扩容操作。
arr[2] = "abc";
alert(arr.length); //3
// alert(arr[1]);// undefined
// 数组的遍历
for (var i = 0; i < arr.length; i++){
alert(arr[i]);
}
</script>
</head>
<body>
</body>
</html>
```

### 8. 函数（重点）

#### 8.1 函数的两种定义方式

> **第一种，可以使用function 关键字来定义函数。**
> **使用的格式如下:**
> **function 函数名(形参列表){**
> **函数体**
> **}**
> **在JavaScript 语言中，如何定义带有返回值的函数？**
> **只需要在函数体内直接使用return 语句返回值即可！**

示例代码：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
// 定义一个无参函数
function fun(){
alert("无参函数fun()被调用了");
}
// 函数调用===才会执行
// fun();
function fun2(a ,b) {
alert("有参函数fun2()被调用了a=>" + a + ",b=>"+b);
}
// fun2(12,"abc");
// 定义带有返回值的函数
function sum(num1,num2) {
var result = num1 + num2;
return result;
}
alert( sum(100,50) );
</script>
</head>
<body>
</body>
</html>
```

函数的第二种定义方式： 

>**使用格式如下：**
>**var 函数名= function(形参列表) { 函数体}**

示例代码：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
var fun = function () {
alert("无参函数");
}
// fun();
var fun2 = function (a,b) {
alert("有参函数a=" + a + ",b=" + b);
}
// fun2(1,2);
var fun3 = function (num1,num2) {
return num1 + num2;
}
alert( fun3(100,200) );
</script>
</head>
<body>
</body>
</html>
```

注：在Java 中函数允许重载。但是在JS 中函数的重载会直接覆盖掉上一次的定义

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
function fun() {
alert("无参函数fun()");
}
function fun(a,b) {
alert("有参函数fun(a,b)");
}
fun();
</script>
</head>
<body>
</body>
</html>
```

#### 8.2 函数的arguments 隐形参数（只在function 函数内）

> 就是在**function** 函数中不需要定义，但却可以直接用来获取所有参数的变量。我们管它叫**隐形参数**。
> 隐形参数特别像java 基础的可变长参数一样。
> **public void fun( Object ... args );**
> 可变长参数其他是一个数组。
> 那么js 中的隐形参数也跟java 的可变长参数一样。操作类似数组。

示例代码：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
function fun(a) {
alert( arguments.length );//可看参数个数
alert( arguments[0] );
alert( arguments[1] );
alert( arguments[2] );
alert("a = " + a);
for (var i = 0; i < arguments.length; i++){
alert( arguments[i] );
}
alert("无参函数fun()");
}
// fun(1,"ad",true);
// 需求：要求编写一个函数。用于计算所有参数相加的和并返回
function sum(num1,num2) {
var result = 0;
for (var i = 0; i < arguments.length; i++) {
if (typeof(arguments[i]) == "number") {
result += arguments[i];
}
}
return result;
}
alert( sum(1,2,3,4,"abc",5,6,7,8,9) );
</script>
</head>
<body>
</body>
</html>
```

### 9. JS中的自定义对象（扩展内容）

> **Object 形式的自定义对象**
> **对象的定义：**
> **var 变量名= new Object(); // 对象实例（空对象）**
> **变量名.属性名= 值; // 定义一个属性**
> **变量名.函数名= function(){} // 定义一个函数**
> **对象的访问：**
> **变量名.属性/ 函数名();**

示例代码：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
// 对象的定义：
// var 变量名= new Object(); // 对象实例（空对象）
// 变量名.属性名= 值; // 定义一个属性
// 变量名.函数名= function(){} // 定义一个函数
var obj = new Object();
obj.name = "华仔";
obj.age = 18;
obj.fun = function () {
alert("姓名：" + this.name + " , 年龄：" + this.age);
}
// 对象的访问：
// 变量名.属性/ 函数名();
// alert( obj.age );
obj.fun();
</script>
</head>
<body>
</body>
</html>
```

> {}花括号形式的自定义对象
> 对象的定义：
> var 变量名= { // 空对象
> 属性名：值, // 定义一个属性
> 属性名：值, // 定义一个属性
> 函数名：function(){} // 定义一个函数
> };
> 对象的访问：
> 变量名.属性/ 函数名();

示例代码：

````html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
// 对象的定义：
// var 变量名= { // 空对象
// 属性名：值, // 定义一个属性
// 属性名：值, // 定义一个属性
// 函数名：function(){} // 定义一个函数
// };
var obj = {
name:"国哥",
age:18,
fun : function () {
alert("姓名：" + this.name + " , 年龄：" + this.age);
}
};
// 对象的访问：
// 变量名.属性/ 函数名();
alert(obj.name);
obj.fun();
</script>
</head>
<body>
</body>
</html>
````

### 10. JS中的事件

> 什么是事件？事件是电脑输入设备与页面进行交互的响应。我们称之为事件。
> 常用的事件：
> onload 加载完成事件： 页面加载完成之后，常用于做页面js 代码初始化操作
> onclick 单击事件： 常用于按钮的点击响应操作。
> onblur 失去焦点事件： 常用用于输入框失去焦点后验证其输入内容是否合法。
> onchange 内容发生改变事件： 常用于下拉列表和输入框内容发生改变后操作
> onsubmit 表单提交事件： 常用于表单提交前，验证所有表单项是否合法。
> 事件的注册又分为静态注册和动态注册两种：
> **什么是事件的注册（绑定）？**
> **其实就是告诉浏览器，当事件响应后要执行哪些操作代码，叫事件注册或事件绑定。**
> **静态注册事件：通过html 标签的事件属性直接赋于事件响应后的代码，这种方式我们叫静态注册。**
> **动态注册事件：是指先通过js 代码得到标签的dom 对象，然后再通过dom 对象.事件名= function(){} 这种形式赋于事件**
> **响应后的代码，叫动态注册。**
> 动态注册基本步骤：
> 1、获取标签对象
> 2、标签对象.事件名= fucntion(){}

onload 加载完成事件

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
// onload 事件的方法
function onloadFun() {
alert('静态注册onload 事件，所有代码');
}
// onload 事件动态注册。是固定写法
window.onload = function () {
alert("动态注册的onload 事件");
}
</script>
</head>
<!--静态注册onload 事件
onload 事件是浏览器解析完页面之后就会自动触发的事件
<body onload="onloadFun();">
-->
<body>
</body>
</html>
```

onclick 单击事件

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
function onclickFun() {
alert("静态注册onclick 事件");
}
// 动态注册onclick 事件
window.onload = function () {
// 1 获取标签对象
/*
* document 是JavaScript 语言提供的一个对象（文档）<br/>
* get 获取
* Element 元素（就是标签）
* By 通过。。由。。经。。。
* Id id 属性
*
* getElementById 通过id 属性获取标签对象
**/
var btnObj = document.getElementById("btn01");
// alert( btnObj );
// 2 通过标签对象.事件名= function(){}
btnObj.onclick = function () {
alert("动态注册的onclick 事件");
}
}
</script>
</head>
<body>
<!--静态注册onClick 事件-->
<button onclick="onclickFun();">按钮1</button>
<button id="btn01">按钮2</button>
</body>
</html>
```

onblur 失去焦点事件

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
// 静态注册失去焦点事件
function onblurFun() {
// console 是控制台对象，是由JavaScript 语言提供，专门用来向浏览器的控制器打印输出， 用于测试使用
// log() 是打印的方法
console.log("静态注册失去焦点事件");
}
// 动态注册onblur 事件
window.onload = function () {
//1 获取标签对象
var passwordObj = document.getElementById("password");
// alert(passwordObj);
//2 通过标签对象.事件名= function(){};
passwordObj.onblur = function () {
console.log("动态注册失去焦点事件");
}
}
</script>
</head>
<body>
用户名:<input type="text" onblur="onblurFun();"><br/>
密码:<input id="password" type="text" ><br/>
</body>
</html>
```

onchange 内容发生改变事件

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
function onchangeFun() {
alert("女神已经改变了");
}
window.onload = function () {
//1 获取标签对象
var selObj = document.getElementById("sel01");
// alert( selObj );
//2 通过标签对象.事件名= function(){}
selObj.onchange = function () {
alert("男神已经改变了");
}
}
</script>
</head>
<body>
请选择你心中的女神：
<!--静态注册onchange 事件-->
<select onchange="onchangeFun();">
<option>--女神--</option>
<option>芳芳</option>
<option>佳佳</option>
<option>娘娘</option>
</select>
请选择你心中的男神：
<select id="sel01">
<option>--男神--</option>
<option>国哥</option>
<option>华仔</option>
<option>富城</option>
</select>
</body>
</html>
```

onsubmit 表单提交事件

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript" >
// 静态注册表单提交事务
function onsubmitFun(){
// 要验证所有表单项是否合法，如果，有一个不合法就阻止表单提交
alert("静态注册表单提交事件----发现不合法");
return flase;
}
window.onload = function () {
//1 获取标签对象
var formObj = document.getElementById("form01");
//2 通过标签对象.事件名= function(){}
formObj.onsubmit = function () {
// 要验证所有表单项是否合法，如果，有一个不合法就阻止表单提交
alert("动态注册表单提交事件----发现不合法");
return false;
}
}
</script>
</head>
<body>
<!--return false 可以阻止表单提交-->
<form action="http://localhost:8080" method="get" onsubmit="return onsubmitFun();">
<input type="submit" value="静态注册"/>
</form>
<form action="http://localhost:8080" id="form01">
<input type="submit" value="动态注册"/>
</form>
</body>
</html>
```

### 11.DOM 模型

> DOM 全称是Document Object Model 文档对象模型
> 大白话，就是把文档中的标签，属性，文本，转换成为对象来管理。
> 那么它们是如何实现把标签，属性，文本转换成为对象来管理呢。这就是我们马上要学习的重点。

#### 11.1 Document对象（重点）

![image-20210708182831829](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708182831829.png)

> Document 对象的理解：
> 第一点：Document 它管理了所有的HTML 文档内容。
> 第二点：document 它是一种树结构的文档。有层级关系。
> 第三点：它让我们把所有的标签都对象化
> 第四点：我们可以通过document 访问所有的标签对象。
> 什么是对象化？？
> 我们基础班已经学过面向对象。请问什么是对象化？
> 举例：
> 有一个人有年龄：18 岁，性别：女，名字：张某某
> 我们要把这个人的信息对象化怎么办！
> Class Person {
> private int age;
> private String sex;
> private String name;
> }
>
> 那么html 标签要对象化怎么办？
>
> ``` html
> <body>
> <div id="div01">div01</div>
> </body>
> 模拟
> ```
>
> 模拟对象化，相当于：
> class Dom{
> private String id; // id 属性
> private String tagName; //表示标签名
> private Dom parentNode; //父亲
> private List<Dom> children; // 孩子结点
> private String innerHTML; // 起始标签和结束标签中间的内容
> }

#### 11.2 Document 对象中的方法介绍(重点)

> document.getElementById(elementId)
> 通过标签的id 属性查找标签dom 对象，elementId 是标签的id 属性值
> document.getElementsByName(elementName)
> 通过标签的name 属性查找标签dom 对象，elementName 标签的name 属性值
> document.getElementsByTagName(tagname)
> 通过标签名查找标签dom 对象。tagname 是标签名
> document.createElement( tagName)
> 方法，通过给定的标签名，创建一个标签对象。tagName 是要创建的标签名
> 注：
> document 对象的三个查询方法，如果有id 属性，优先使用getElementById 方法来进行查询
> 如果没有id 属性，则优先使用getElementsByName 方法来进行查询
> 如果id 属性和name 属性都没有最后再按标签名查getElementsByTagName
> 以上三个方法，一定要在页面加载完成之后执行，才能查询到标签对象。

getElementById方法示例代码：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript" >
/*
* 需求：当用户点击了较验按钮，要获取输出框中的内容。然后验证其是否合法。<br/>
* 验证的规则是：必须由字母，数字。下划线组成。并且长度是5 到12 位。
* */
function onclickFun() {
// 1 当我们要操作一个标签的时候，一定要先获取这个标签对象。
var usernameObj = document.getElementById("username");
// [object HTMLInputElement] 它就是dom 对象
var usernameText = usernameObj.value;
// 如何验证字符串，符合某个规则，需要使用正则表达式技术
var patt = /^\w{5,12}$/;
/*
* test()方法用于测试某个字符串，是不是匹配我的规则，
* 匹配就返回true。不匹配就返回false.
* */
var usernameSpanObj = document.getElementById("usernameSpan");
// innerHTML 表示起始标签和结束标签中的内容
// innerHTML 这个属性可读，可写
usernameSpanObj.innerHTML = "国哥真可爱！";
if (patt.test(usernameText)) {
// alert("用户名合法！");
// usernameSpanObj.innerHTML = "用户名合法！";
usernameSpanObj.innerHTML = "<img src=\"right.png\" width=\"18\" height=\"18\">";
} else {
// alert("用户名不合法！");
// usernameSpanObj.innerHTML = "用户名不合法！";
usernameSpanObj.innerHTML = "<img src=\"wrong.png\" width=\"18\" height=\"18\">";
}
}
</script>
</head>
<body>
用户名：<input type="text" id="username" value="wzg"/>
<span id="usernameSpan" style="color:red;">
</span>
<button onclick="onclickFun()">较验</button>
</body>
</html>
```

getElementsByName 方法示例代码：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Title</title>
<script type="text/javascript">
// 全选
function checkAll() {
// 让所有复选框都选中
// document.getElementsByName();是根据指定的name 属性查询返回多个标签对象集合
// 这个集合的操作跟数组一样
// 集合中每个元素都是dom 对象
// 这个集合中的元素顺序是他们在html 页面中从上到下的顺序
var hobbies = document.getElementsByName("hobby");
// checked 表示复选框的选中状态。如果选中是true，不选中是false
// checked 这个属性可读，可写
for (var i = 0; i < hobbies.length; i++){
hobbies[i].checked = true;
}
}
//全不选
function checkNo() {
var hobbies = document.getElementsByName("hobby");
// checked 表示复选框的选中状态。如果选中是true，不选中是false
// checked 这个属性可读，可写
for (var i = 0; i < hobbies.length; i++){
hobbies[i].checked = false;
}
}
// 反选
function checkReverse() {
var hobbies = document.getElementsByName("hobby");
for (var i = 0; i < hobbies.length; i++) {
hobbies[i].checked = !hobbies[i].checked;
// if (hobbies[i].checked) {
// hobbies[i].checked = false;
// }else {
// hobbies[i].checked = true;
// }
}
}
</script>
</head>
<body>
兴趣爱好：
<input type="checkbox" name="hobby" value="cpp" checked="checked">C++
<input type="checkbox" name="hobby" value="java">Java
<input type="checkbox" name="hobby" value="js">JavaScript
<br/>
<button onclick="checkAll()">全选</button>
<button onclick="checkNo()">全不选</button>
<button onclick="checkReverse()">反选</button>
</body>
</html>
```

getElementsByTagName 方法示例代码：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        window.onload = function(){
            // alert( document.getElementById("btn01") );
        }


        // 全选
        function checkAll() {
            alert( document.getElementById("btn01") );
            // document.getElementsByTagName("input");
            // 是按照指定标签名来进行查询并返回集合
            // 这个集合的操作跟数组 一样
            // 集合中都是dom对象
            // 集合中元素顺序 是他们在html页面中从上到下的顺序。
            var inputs = document.getElementsByTagName("input");

            for (var i = 0; i < inputs.length; i++){
                inputs[i].checked = true;
            }
        }
    </script>
</head>
<body>

    <!--as -->
    兴趣爱好：
    <input type="checkbox" value="cpp" checked="checked">C++
    <input type="checkbox" value="java">Java
    <input type="checkbox" value="js">JavaScript
    <br/>
    <button id="btn01" onclick="checkAll()">全选</button>

</body>
</html>
```

createElement 方法示例代码：

``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        window.onload = function () {
            // 现在需要我们使用js代码来创建html标签，并显示在页面上
            // 标签的内容就是：<div>国哥，我爱你</div>
            var divObj = document.createElement("div"); // 在内存中 <div></div>

            var textNodeObj = document.createTextNode("国哥，我爱你"); // 有一个文本节点对象 #国哥，我爱你

            divObj.appendChild(textNodeObj); // <div>国哥，我爱你</div>

            // divObj.innerHTML = "国哥，我爱你"; // <div>国哥，我爱你</div>,但，还只是在内存中
            // 添加子元素
            document.body.appendChild(divObj);
        }
    </script>
</head>
<body>

</body>
</html>
```

#### 11.3 节点的常用属性和方法

> 节点就是标签对象
> 方法：
> 通过具体的元素节点调用
> getElementsByTagName()
> 方法，获取当前节点的指定标签名孩子节点
> appendChild( oChildNode )
> 方法，可以添加一个子节点，ChildNode 是要添加的孩子节点
> 属性：
> childNodes
> 属性，获取当前节点的所有子节点
> firstChild
> 属性，获取当前节点的第一个子节点
> lastChild
> 属性，获取当前节点的最后一个子节点
> parentNode
> 属性，获取当前节点的父节点
> nextSibling
> 属性，获取当前节点的下一个节点
> previousSibling
> 属性，获取当前节点的上一个节点
> className
> 用于获取或设置标签的class 属性值
> innerHTML
> 属性，表示获取/设置起始标签和结束标签中的内容
> innerText
> 属性，表示获取/设置起始标签和结束标签中的文本

练习：DOM查询练习

``` html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>dom 查询</title>
<link rel="stylesheet" type="text/css" href="style/css.css" />
<script type="text/javascript">
window.onload = function(){
//1.查找#bj 节点
document.getElementById("btn01").onclick = function () {
var bjObj = document.getElementById("bj");
alert(bjObj.innerHTML);
}
//2.查找所有li 节点
var btn02Ele = document.getElementById("btn02");
btn02Ele.onclick = function(){
var lis = document.getElementsByTagName("li");
alert(lis.length)
};
//3.查找name=gender 的所有节点
var btn03Ele = document.getElementById("btn03");
btn03Ele.onclick = function(){
var genders = document.getElementsByName("gender");
alert(genders.length)
};
//4.查找#city 下所有li 节点
var btn04Ele = document.getElementById("btn04");
btn04Ele.onclick = function(){
//1 获取id 为city 的节点
//2 通过city 节点.getElementsByTagName 按标签名查子节点
var lis = document.getElementById("city").getElementsByTagName("li");
alert(lis.length)
};
//5.返回#city 的所有子节点
var btn05Ele = document.getElementById("btn05");
btn05Ele.onclick = function(){
//1 获取id 为city 的节点
//2 通过city 获取所有子节点
alert(document.getElementById("city").childNodes.length);
};
//6.返回#phone 的第一个子节点
var btn06Ele = document.getElementById("btn06");
btn06Ele.onclick = function(){
// 查询id 为phone 的节点
alert( document.getElementById("phone").firstChild.innerHTML );
};
//7.返回#bj 的父节点
var btn07Ele = document.getElementById("btn07");
btn07Ele.onclick = function(){
//1 查询id 为bj 的节点
var bjObj = document.getElementById("bj");
//2 bj 节点获取父节点
alert( bjObj.parentNode.innerHTML );
};
//8.返回#android 的前一个兄弟节点
var btn08Ele = document.getElementById("btn08");
btn08Ele.onclick = function(){
// 获取id 为android 的节点
// 通过android 节点获取前面兄弟节点
alert( document.getElementById("android").previousSibling.innerHTML );
};
//9.读取#username 的value 属性值
var btn09Ele = document.getElementById("btn09");
btn09Ele.onclick = function(){
alert(document.getElementById("username").value);
};
//10.设置#username 的value 属性值
var btn10Ele = document.getElementById("btn10");
btn10Ele.onclick = function(){
document.getElementById("username").value = "国哥你真牛逼";
};
//11.返回#bj 的文本值
var btn11Ele = document.getElementById("btn11");
btn11Ele.onclick = function(){
alert(document.getElementById("city").innerHTML);
// alert(document.getElementById("city").innerText);
};
};
</script>
</head>
<body>
<div id="total">
<div class="inner">
<p>
你喜欢哪个城市?
</p>
<ul id="city">
<li id="bj">北京</li>
<li>上海</li>
<li>东京</li>
<li>首尔</li>
</ul>
<br>
<br>
<p>
你喜欢哪款单机游戏?
</p>
<ul id="game">
<li id="rl">红警</li>
<li>实况</li>
<li>极品飞车</li>
<li>魔兽</li>
</ul>
<br />
<br />
<p>
你手机的操作系统是?
</p>
<ul id="phone"><li>IOS</li><li id="android">Android</li><li>Windows Phone</li></ul>
</div>
<div class="inner">
gender:
<input type="radio" name="gender" value="male"/>
Male
<input type="radio" name="gender" value="female"/>
Female
<br>
<br>
name:
<input type="text" name="name" id="username" value="abcde"/>
</div>
</div>
<div id="btnList">
<div><button id="btn01">查找#bj 节点</button></div>
<div><button id="btn02">查找所有li 节点</button></div>
<div><button id="btn03">查找name=gender 的所有节点</button></div>
<div><button id="btn04">查找#city 下所有li 节点</button></div>
<div><button id="btn05">返回#city 的所有子节点</button></div>
<div><button id="btn06">返回#phone 的第一个子节点</button></div>
<div><button id="btn07">返回#bj 的父节点</button></div>
<div><button id="btn08">返回#android 的前一个兄弟节点</button></div>
<div><button id="btn09">返回#username 的value 属性值</button></div>
<div><button id="btn10">设置#username 的value 属性值</button></div>
<div><button id="btn11">返回#bj 的文本值</button></div>
</div>
</body>
</html>
```

![image-20210708183737980](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/img/image-20210708183737980.png)

