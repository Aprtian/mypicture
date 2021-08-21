# xml

## 1. xml简介

==**什么是xml？**==
xml 是可扩展的标记性语言。
xml 的作用？
==**xml 的主要作用有：**==
1、用来保存数据，而且这些数据具有自我描述性
2、它还可以做为项目或者模块的配置文件
3、还可以做为网络传输数据的格式（现在JSON 为主）。

## 2. xml语法

1. 文档声明。
2. 元素（标签）
3. xml 属性
4. xml 注释
5. 文本区域（CDATA 区）

### 2.1 文档声明

我们先创建一个简单XML 文件，用来描述图书信息。

1）创建一个xml 文件

![image-20210816155636583](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816155636583.png)

文件名：

![image-20210816155648062](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816155648062.png)

<?xml version="1.0" encoding="UTF-8"?> xml 声明。
<!-- xml 声明version 是版本的意思encoding 是编码-->
而且这个<?xml 要连在一起写，否则会有报错
属性
version 是版本号
encoding 是xml 的文件编码
standalone="yes/no" 表示这个xml 文件是否是独立的xml 文件

2）图书有id 属性表示唯一标识，书名，有作者，价格的信息

```html
<?xml version="1.0" encoding="UTF-8"?>
<!-- xml 声明version 是版本的意思encoding 是编码-->
<books> <!-- 这是xml 注释-->
<book id="SN123123413241"> <!-- book 标签描述一本图书id 属性描述的是图书的编号-->
<name>java 编程思想</name> <!-- name 标签描述的是图书的信息-->
<author>华仔</author> <!-- author 单词是作者的意思，描述图书作者-->
<price>9.9</price> <!-- price 单词是价格，描述的是图书的价格-->
</book>
<book id="SN12341235123"> <!-- book 标签描述一本图书id 属性描述的是图书的编号-->
<name>葵花宝典</name> <!-- name 标签描述的是图书的信息-->
<author>班长</author> <!-- author 单词是作者的意思，描述图书作者-->
<price>5.5</price> <!-- price 单词是价格，描述的是图书的价格-->
</book>
</books>
```

在浏览器中可以查看到文档

![image-20210816155745735](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816155745735.png)

### 2.2 xml注释

html 和XML 注释一样: <!-- html 注释-->

### 2.3 元素（标签）

咱们先回忆一下:
html 标签：
格式：<标签名>封装的数据</标签名>
单标签: <标签名/> <br /> 换行<hr />水平线
双标签<标签名>封装的数据</标签名>
标签名大小写不敏感
标签有属性，有基本属性和事件属性
标签要闭合（不闭合，html 中不报错。但我们要养成良好的书写习惯。闭合）

1）什么是xml 元素

![image-20210816155844639](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816155844639.png)

元素是指从开始标签到结束标签的内容。
例如：<title>java 编程思想</title>
元素我们可以简单的理解为是标签。
Element 翻译元素
2）XML 命名规则
XML 元素必须遵循以下命名规则：
2.1）名称可以含字母、数字以及其他的字符
例如： <book id="SN213412341"> <!-- 描述一本书-->
<author>班导</author> <!-- 描述书的作者信息-->
<name>java 编程思想</name> <!-- 书名-->
<price>9.9</price> <!-- 价格-->
</book>
2.2）名称不能以数字或者标点符号开始

![image-20210816155903675](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816155903675.png)

2.3）名称不能以字符“xml”（或者XML、Xml）开始（它是可以的）

![image-20210816155919031](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816155919031.png)

2.4）名称不能包含空格

![image-20210816155934171](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816155934171.png)

3）xml 中的元素（标签）也分成单标签和双标签：
单标签
格式： <标签名属性=”值” 属性=”值” ...... />
双标签
格式：< 标签名属性=”值” 属性=”值” ......>文本数据或子标签</标签名>

![image-20210816155945456](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816155945456.png)

### 2.4 xml属性

xml 的标签属性和html 的标签属性是非常类似的，属性可以提供元素的额外信息
在标签上可以书写属性：
一个标签上可以书写多个属性。每个属性的值必须使用引号引起来。
的规则和标签的书写规则一致。

![image-20210816160013755](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160013755.png)

1）属性必须使用引号引起来，不引会报错示例代码

![image-20210816160028717](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160028717.png)

### 2.5 语法规则

#### 2.5.1）所有XML 元素都须有关闭标签（也就是闭合）

![image-20210816160137191](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160137191.png)

#### 2.5.2）XML 标签对大小写敏感

![image-20210816160155276](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160155276.png)

#### 2.5.3）XML 必须正确地嵌套

![image-20210816160211987](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160211987.png)

#### 2.5.4）XML 文档必须有根元素

根元素就是顶级元素，
没有父标签的元素，叫顶级元素。
根元素是没有父标签的顶级元素，而且是唯一一个才行。

![image-20210816160244803](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160244803.png)

#### 2.5.5）XML 的属性值须加引号

![image-20210816160305862](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160305862.png)

#### 2.5.6）XML 中的特殊字符

![image-20210816160322896](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160322896.png)

#### 2.5.7）文本区域（CDATA 区） 

CDATA 语法可以告诉xml 解析器，我CDATA 里的文本内容，只是纯文本，不需要xml 语法解析
CDATA 格式：
<![CDATA[ 这里可以把你输入的字符原样显示，不会解析xml ]]>

![image-20210816160356971](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160356971.png)

## 3. xml解析技术介绍

xml 可扩展的标记语言。
不管是html 文件还是xml 文件它们都是标记型文档，都可以使用w3c 组织制定的dom 技术来解析。

![image-20210816160447223](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160447223.png)

==document 对象表示的是整个文档（可以是html 文档，也可以是xml 文档）==
**早期JDK 为我们提供了两种xml 解析技术DOM 和Sax 简介（已经过时，但我们需要知道这两种技术）**
dom 解析技术是W3C 组织制定的，而所有的编程语言都对这个解析技术使用了自己语言的特点进行实现。
Java 对dom 技术解析标记也做了实现。
sun 公司在JDK5 版本对dom 解析技术进行升级：SAX（ Simple API for XML ）
SAX 解析，它跟W3C 制定的解析不太一样。它是以类似事件机制通过回调告诉用户当前正在解析的内容。
它是一行一行的读取xml 文件进行解析的。不会创建大量的dom 对象。
所以它在解析xml 的时候，在内存的使用上。和性能上。都优于Dom 解析。
第三方的解析：
jdom 在dom 基础上进行了封装、
**dom4j** 又对jdom 进行了封装。
pull 主要用在Android 手机开发，是在跟sax 非常类似都是事件机制解析xml 文件。
**这个Dom4j 它是第三方的解析技术。我们需要使用第三方给我们提供好的类库才可以解析xml 文件。**

## 4. dom4j解析技术（***重点**）

由于dom4j 它不是sun 公司的技术，而属于第三方公司的技术，我们需要使用dom4j 就需要到dom4j 官网下载dom4j
的jar 包。

### 4.1 Dom4j类库的使用

![image-20210816160717482](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160717482.png)

解压后：

![image-20210816160733155](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160733155.png)

### 4.2 dom4j 目录的介绍：

1）docs 是文档目录

![image-20210816160810487](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160810487.png)

2）如何查Dom4j 的文档

![image-20210816160822690](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160822690.png)

3）Dom4j 快速入门

![image-20210816160833503](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160833503.png)

2）lib 目录

<img src="https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160850306.png" alt="image-20210816160850306"  />

3）src 目录是第三方类库的源码目录：

![image-20210816160901233](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816160901233.png)

### 4.3 dom4j编程步骤：

==第一步： 先加载xml 文件创建Document 对象
第二步：通过Document 对象拿到根元素对象
第三步：通过根元素.elelemts(标签名); 可以返回一个集合，这个集合里放着。所有你指定的标签名的元素对象
第四步：找到你想要修改、删除的子元素，进行相应在的操作
第五步，保存到硬盘上==

### 4.4 获取document对象

创建一个lib 目录，并添加dom4j 的jar 包。并添加到类路径。

![image-20210816161023433](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816161023433.png)

需要解析的books.xml 文件内容

```xml
<?xml version="1.0" encoding="UTF-8"?>
<books>
<book sn="SN12341232">
<name>辟邪剑谱</name>
<price>9.9</price>
<author>班主任</author>
</book>
<book sn="SN12341231">
<name>葵花宝典</name>
<price>99.99</price>
<author>班长</author>
</book>
</books>
```

解析获取Document 对象的代码
第一步，先创建SaxReader 对象。这个对象，用于读取xml 文件，并创建Document

```java
/*
* dom4j 获取Documet 对象
*/
@Test
public void getDocument() throws DocumentException {
// 要创建一个Document 对象，需要我们先创建一个SAXReader 对象
SAXReader reader = new SAXReader();
// 这个对象用于读取xml 文件，然后返回一个Document。
Document document = reader.read("src/books.xml");
// 打印到控制台，看看是否创建成功
System.out.println(document);
}
```

### 4.5 遍历 标签 获取所有标签中的内容（**重点）

需要分四步操作:
第一步，通过创建SAXReader 对象。来读取xml 文件，获取Document 对象
第二步，通过Document 对象。拿到XML 的根元素对象
第三步，通过根元素对象。获取所有的book 标签对象
第四小，遍历每个book 标签对象。然后获取到book 标签对象内的每一个元素，再通过getText() 方法拿到起始标签和结
束标签之间的文本内容

```java
/*
* 读取xml 文件中的内容
*/
@Test
public void readXML() throws DocumentException {
// 需要分四步操作:
// 第一步，通过创建SAXReader 对象。来读取xml 文件，获取Document 对象
// 第二步，通过Document 对象。拿到XML 的根元素对象
// 第三步，通过根元素对象。获取所有的book 标签对象
// 第四小，遍历每个book 标签对象。然后获取到book 标签对象内的每一个元素，再通过getText() 方法拿到
起始标签和结束标签之间的文本内容
// 第一步，通过创建SAXReader 对象。来读取xml 文件，获取Document 对象
SAXReader reader = new SAXReader();
Document document = reader.read("src/books.xml");
// 第二步，通过Document 对象。拿到XML 的根元素对象
Element root = document.getRootElement();
// 打印测试
// Element.asXML() 它将当前元素转换成为String 对象
// System.out.println( root.asXML() );
// 第三步，通过根元素对象。获取所有的book 标签对象
// Element.elements(标签名)它可以拿到当前元素下的指定的子元素的集合
List<Element> books = root.elements("book");
// 第四小，遍历每个book 标签对象。然后获取到book 标签对象内的每一个元素，
for (Element book : books) {
// 测试
// System.out.println(book.asXML());
// 拿到book 下面的name 元素对象
Element nameElement = book.element("name");
// 拿到book 下面的price 元素对象
Element priceElement = book.element("price");
// 拿到book 下面的author 元素对象
Element authorElement = book.element("author");
// 再通过getText() 方法拿到起始标签和结束标签之间的文本内容
System.out.println("书名" + nameElement.getText() + " , 价格:"
+ priceElement.getText() + ", 作者：" + authorElement.getText());
}
}
```

打印内容：

![image-20210816161321141](https://gitee.com/luck365/studypicture/raw/master/img/javaweb/xml/image-20210816161321141.png)

