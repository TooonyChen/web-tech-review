# SE121: Web Technology - Review


## Chapter 1: Web Essentials - Clients Servers and Communication

**Typical browser-server interaction**
- User enters Web address in browser
- Browser uses DNS to locate IP address
- Browser opens TCP connection to server
- Browser sends HTTP request over connection
- Server sends HTTP response to browser over connection
- Browser displays body of response in the client area of the browser window

**Web Browsers**

Primary tasks:
- Convert web addresses (URL’s) to HTTP requests
- Communicate with web servers via HTTP
- Render (appropriately display) documents returned by a server

Standard features:
- Save web page to disk
- Find string in page
- Fill forms automatically (passwords, CC numbers, …)
- Set preferences (language, character set, cache and HTTP parameters)
- Modify display style (e.g., increase font sizes)
- Display raw HTML and HTTP header info (e.g., Last-Modified)
- Choose browser themes (skins)
- View history of web addresses visited
- Bookmark favorite pages for easy return

Additional functionality:
- Execution of scripts (e.g., drop-down menus)
- Event handling (e.g., mouse clicks)
- GUI for controls (e.g., buttons)
- Secure communication with servers
- Display of non-HTML documents (e.g., PDF) via plug-ins

**Web Servers**

Basic functionality:
- Receive HTTP request via TCP
- Map Host header to specific virtual host (one of many host names sharing an IP address)
- Map Request-URI to specific resource associated with the virtual host
- File: Return file in HTTP response
- Program: Run program and return output in HTTP response
- Map type of resource to appropriate MIME type and use it to set Content-Type header in HTTP response
- Log information about the request and response



**知识点1：telnet命令行的用法**
- 定义：Telnet是一种网络协议，允许用户在本地计算机上使用命令行接口远程登录到远程主机，并执行命令。
- 用法：telnet [hostname or IP address] [port]。通过telnet命令，用户可以连接到远程服务器并发送各种命令。
- 例子：telnet www.example.com 80。这将连接到端口80（HTTP端口）上的www.example.com，并允许用户手动发送HTTP请求。

**知识点2：localhost的含义**
- 定义：localhost是一个标准主机名，通常用于识别本地计算机或本地主机。它指向本地主机IP地址，通常是127.0.0.1。
- 用法：在网络通信中，localhost可以用作目标主机名，表示通信将在本地主机上进行。
- 例子：当在浏览器中输入http://localhost时，浏览器将尝试连接到本地计算机上运行的Web服务器。

**知识点3：HTTP请求/响应消息的构成**
- 定义：HTTP请求和响应消息是客户端和服务器之间交换的数据，用于请求和传送Web页面和资源。
- 用法：HTTP请求通常由请求行、请求头、空行（用于分隔请求头和请求体）、请求体组成。而HTTP响应通常由状态行、响应头、空行、响应体组成。
- 例子：HTTP请求消息示例：
```
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.99 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
```
HTTP响应消息示例：
```
HTTP/1.1 200 OK
Date: Sun, 08 May 2024 12:00:00 GMT
Server: Apache/2.4.38 (Unix)
Last-Modified: Tue, 01 Jan 2024 00:00:00 GMT
Content-Type: text/html
Content-Length: 127

<!DOCTYPE html>
<html>
<head>
    <title>Example Page</title>
</head>
<body>
    <h1>Hello, World!</h1>
</body>
</html>
```

**知识点4：Web浏览器/服务器的主要责任和功能以及其之间的交互**
- 定义：Web浏览器负责向用户显示Web页面，解释并呈现HTML、CSS和JavaScript。Web服务器则负责存储和传送Web内容，处理来自客户端的请求，并向客户端发送响应。
- 用法：Web浏览器通过发送HTTP请求到Web服务器请求页面和资源，然后接收并呈现Web服务器返回的HTML、CSS、JavaScript等内容。
- 例子：当用户在浏览器中输入URL并按下回车键时，浏览器将发送HTTP请求到相应的Web服务器，服务器将处理请求并返回相应的Web页面或资源，浏览器接收并显示该页面。


## Chapter 2: Markup Languages - XHTML 1.0.ppt

1. 块级元素
   块级元素在浏览器中显示时会独占一行,常用于文档结构和布局。

- `<p>`表示一个段落
- `<h1>`到`<h6>`表示不同级别的标题,`<h1>`是最高级
- `<pre>`表示预格式化文本,保留其中的空格和换行
- `<hr>`表示水平分隔线
- `<div>`是通用的块级容器,常用于分组和布局

示例:

```html
<h1>欢迎访问我的主页</h1>
<p>这是一个段落。段落之间会自动换行。</p>
<pre>
  这是预格式化文本  
  它保留了空格和换行
</pre>
<hr />
<div>
  <p>div元素中的一个段落</p>
  <p>div元素中的另一个段落</p>  
</div>
```

2. 内联元素
   内联元素通常出现在块级元素内部,不会打断文本流。

- `<span>`是通用的内联容器,常用于对文本应用样式
- `<a>`表示超链接,用href属性指定链接目标
- `<img>`表示图像,用src属性指定图像URL
- `<strong>`表示重要性强调的文本
  示例:

```html
<p>一个包含<span style="color:red;">红色文本</span>的段落。</p>
<p>访问<a href="http://www.example.com">示例网站</a></p>
<p>一张图片:<img src="logo.png" alt="网站logo" /></p> 
<p>这是<strong>重要的</strong>信息。</p>
```

3. 列表元素
   列表元素用于创建项目列表,可以是有序、无序或定义列表。

- `<ul>`表示无序列表,`<li>`表示列表项
- `<ol>`表示有序列表,`<li>`表示列表项
- `<dl>`表示定义列表,`<dt>`表示被定义的项,`<dd>`表示其定义

示例:

```html
<ul>
  <li>无序列表项1</li>
  <li>无序列表项2</li>
</ul>
<ol>
  <li>有序列表项1</li>
  <li>有序列表项2</li>
</ol>
<dl>
  <dt>术语1</dt>
  <dd>术语1的定义</dd>
  <dt>术语2</dt>
  <dd>术语2的定义</dd>
</dl>
```

4. 表格元素
   表格元素用于在网页中显示表格数据。

- `<table>`表示一个表格
- `<tr>`表示表格行
- `<td>`表示数据单元格
- `<th>`表示表头单元格

示例:

```html
<table border="1">
<tr>
  <th>表头1</th>
  <th>表头2</th>
</tr>
<tr>
  <td>数据1</td>
  <td>数据2</td>
</tr>
</table>
```

5. 表单元素
   表单用于收集用户输入并提交到服务器。

- `<form>`表示一个表单,action属性指定提交URL
- `<input>`表示各种形式的输入域,如文本框、单选框、复选框等,type属性指定类型
- `<textarea>`表示多行文本输入域
- `<select>`和`<option>`表示下拉选择框

示例:

```html
<form action="/login" method="post">
  <p>用户名: <input type="text" name="username" /></p>
  <p>密码: <input type="password" name="password" /></p>
  <p>性别: 
    <input type="radio" name="gender" value="male" /> 男
    <input type="radio" name="gender" value="female" /> 女
  </p>
  <p>爱好:
    <input type="checkbox" name="interests" value="sports" /> 体育 
    <input type="checkbox" name="interests" value="music" /> 音乐
  </p>
  <p>个人简介:</p>
  <textarea name="bio" rows="5" cols="40"></textarea>
  <p>籍贯:
    <select name="hometown">
      <option value="beijing">北京</option>
      <option value="shanghai">上海</option>
    </select>
  </p>
  <p><input type="submit" value="登录" /></p>
</form>
```

 

## Chapter 3: Style Sheets - CSS

**知识点1: 单一元素类型选择器**

- 定义: 使用单一HTML元素标签作为选择器,如p { font-size:smaller; letter-spacing:1em }
- 用法: 选择页面上所有该类型的HTML元素,并对它们应用相同的样式
- 例子:

```css
p { font-size:smaller; letter-spacing:1em }
```

这条规则将应用于页面上所有的`<p>`段落元素

**知识点2: 多元素类型选择器**

- 定义: 使用多个HTML元素标签作为选择器,用逗号分隔,如h1,h2,h3,h4,h5,h6 { background-color:purple }
- 用法: 选择页面上所列出的多种类型的HTML元素,并对它们应用相同的样式
- 例子:

```css
h1,h2,h3,h4,h5,h6 { background-color:purple }
```

这条规则将使所有的`<h1>`到`<h6>`标题元素的背景颜色变为紫色

除了上述两个你提到的知识点,幻灯片中还介绍了其他几种选择器类型,我也总结如下:

**知识点3: 全元素类型选择器**

- 定义: 使用通配符`*`作为选择器,选择页面上所有元素
- 用法: 对页面上所有元素应用相同的样式
- 例子:

```css
* { font-weight:bold }
```

**知识点4: 特定元素ID选择器**

- 定义: 使用`#`加上元素的id属性值作为选择器,如`#p1, #p3 { background-color:aqua }`
- 用法: 选择具有指定id的元素,并对它们应用样式
- 例子:

```css
#p1, #p3 { background-color:aqua }
```

 

## Chapter 4: Client-Side Programming-JavaScript

考试题：Using a regexp instance, write the JavaScript code to test if a string value start with “MUST” , followed by 20 digits and end with 0-10 words characters
解答：

目的：

验证字符串是否符合以下格式：

* 以 "MUST" 开头
* 后跟 20 个数字
* 以 0 到 10 个单词字符结尾

代码详解：

```javascript
function isValidString(str) {
  // 正则表达式模式匹配格式
  const pattern = /^MUST\d{20}[\w]{0,10}$/;
  return pattern.test(str);
}

// 测试用例
const testStrings = [
  "MUST12345678901234567890abc",  // 有效
  "MUST123456789012345678",       // 无效（缺少尾部字符）
  "MUST1234a5678901234567890",     // 无效（包含非数字字符）
  "notMUST12345678901234567890",   // 无效（不以 MUST 开头）
];

for (const testString of testStrings) {
  console.log(`${testString} is valid: ${isValidString(testString)}`);
}
```

1. `isValidString` 函数：

* 接收字符串 `str` 作为参数。
* 定义正则表达式模式 `pattern`，用于匹配字符串格式：
    * `^`: 匹配字符串开头
    * `MUST`: 匹配字面字符 "MUST"
    * `\d{20}`: 匹配 20 个连续数字
    * `[\w]{0,10}`: 匹配 0 到 10 个单词字符（字母、数字、下划线）
    * `$`: 匹配字符串结尾
* 使用 `pattern.test(str)` 方法测试字符串 `str` 是否符合模式。
    * 如果匹配，返回 `true`；否则，返回 `false`。

2. 测试用例：

* 定义测试字符串数组 `testStrings`，包含多种格式的字符串。
* 使用循环遍历每个测试字符串 `testString`：
    * 调用 `isValidString(testString)` 获取验证结果。
    * 将测试字符串和验证结果输出到控制台。

总结：

该代码有效地检查了字符串是否符合指定格式，并提供了测试用例来演示其功能。

**知识点1: JavaScript函数**

- 定义: 函数是一段可重复使用的代码块,可以接受输入参数,执行特定操作,并返回结果。
- 用法:

1) 函数声明

```js
function 函数名(参数1, 参数2, ...) {
  // 函数体代码
  return 结果;
}
```

2) 函数调用

```js
函数名(实参1, 实参2, ...);
```

- 例子:

```js
// 函数声明
function add(a, b) {
  return a + b;
}

// 函数调用
let sum = add(2, 3); // sum = 5
```
**知识点2: 递归函数**

- 定义: 递归函数是一种函数在其函数体内直接或间接调用自身的函数。
- 用法: 递归函数通常有一个终止条件,当满足条件时递归结束,否则会无限循环下去。
- 例子: 计算阶乘

```js
function factorial(n) {
  if (n === 0) { // 终止条件
    return 1; 
  } else {
    return n * factorial(n - 1); // 递归调用
  }
}

console.log(factorial(5)); // 输出 120
```
**知识点3: JavaScript正则表达式**

- 定义: 正则表达式是用于匹配字符串中字符组合的模式。
- 用法:

1) 通过正则表达式字面量创建  
通过正则表达式字面量创建：使用斜杠符号 `/` 将正则表达式包裹起来，后面可以跟随一些标志（flags）来修改匹配的行为。

```js
let regex = /pattern/flags;
```

2) 通过RegExp对象构造函数创建  
通过RegExp对象构造函数创建：可以使用RegExp对象的构造函数来创建正则表达式，传入要匹配的模式和相应的标志。

```js
let regex = new RegExp('pattern', 'flags');
```

3) 测试匹配  
可以使用 `test()` 方法来测试一个字符串是否匹配了给定的正则表达式模式，它会返回一个布尔值（true或false），表示是否有匹配。

```js
regex.test(str); // 返回true或false
```

4) 在字符串上使用正则方法

```js
str.match(regex); // 查找匹配
str.replace(regex, newStr); // 替换匹配
```

举个例子，假设你想要检查一个字符串是否包含 "hello" 这个单词，你可以这样使用正则表达式：
```js
let regex = /hello/;
let str = "hello world";
console.log(regex.test(str)); // 输出 true
```

- 例子: 匹配Email地址

```js
let emailRegex = /\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}\b/;
emailRegex.test('test@example.com'); // true
```

## Chapter 5: Host Objects-Browsers and the DOM

好的,根据你提供的Chapter 5 Host Objects-Browsers and the DOM幻灯片,以下是你需要复习的DOM、HTML内在事件属性onload和window.alert()函数相关知识点:

**知识点1: DOM (Document Object Model)**

- 定义: DOM是一个应用程序编程接口(API),允许程序和脚本动态访问和更新HTML(或XML)文档的内容、结构和样式。
- 用法: 通过DOM,JavaScript可以访问HTML文档的所有元素,并对其进行操作,例如修改元素的内容、属性、样式等。主要通过document对象及其子对象(Element对象)来实现。
- 例子:

```js
// 获取id为"myElement"的元素
var elem = document.getElementById("myElement");

// 修改元素的HTML内容
elem.innerHTML = "新的HTML内容";

// 修改元素的CSS样式 
elem.style.color = "red";
elem.style.backgroundColor = "#ccc";
```

**知识点2: HTML内在事件属性onload**

- 定义: onload是HTML的一个内在事件属性,当页面或某个资源完成加载时触发。
- 用法: onload事件属性可以添加到<body>或<img>等元素上,当相应的资源加载完成时,会执行指定的JavaScript代码。
- 例子:

```html
<body onload="initFunction()">
  <!-- 页面内容 -->

  <script>
    function initFunction() {
      // 页面加载完成后执行的代码
      alert("页面加载完毕!");
    }
  </script>
</body>
```

```html
<img src="loading.gif" onload="showContent()" />
```

**知识点3: window.alert()函数**

- 定义: alert()是浏览器提供的一个宿主对象函数,用于在页面上显示一个带有指定消息和一个确定按钮的对话框。
- 用法: alert(msg)函数接受一个字符串参数作为要显示的消息内容。显示对话框后,脚本会暂停执行,直到用户点击确定按钮。
- 例子:

```js
window.alert("Hello World!");
alert("这是一条警告消息");
```

老师PPT放的示例代码：

好的,这段代码展示了如何使用JavaScript操作HTML文档对象模型(DOM)来实现鼠标滑过图片时切换图片的效果。我将打印出代码并解释每一部分:

```html
<!DOCTYPE html
        PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
            "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
        <head>
            <title>Rollover.html</title>
            <script type="text/javascript" src="rollover.js">
            </script>
            <meta http-equiv="Content-Script-Type" content="text/javascript" />
        </head>
        <body>
            <p>
                <img id="img1" src="CFP2.png" alt="flower pot"
                    height="86" width="44"
                    onmouseover="show('img1', 'CFP22.png');"
                    onmouseout="show('img1', 'CFP2.png');" />
        </p>
    </body>
</html>
```

```js
// rollover.js
function show(eltId, URL) {
    var elt = window.document.getElementById(eltId);
    elt.setAttribute("src", URL);
    return;
}
```
1. 这是一个HTML文件,包含了文档类型声明、HTML、head和body元素。

2. `<script src="rollover.js"></script>`引入了一个外部JavaScript文件rollover.js。

3. `<meta>` 元素告诉浏览器本文档中的事件处理程序使用JavaScript编写。

4. `<img>`元素定义了一个图像,通过src属性指定了初始图片文件。

5. `id="img1"`为图像元素指定了一个唯一ID,以便JavaScript代码可以引用它。

6. `onmouseover`和`onmouseout`是HTML事件处理属性,分别在鼠标移入和移出图像时触发。它们调用了JavaScript函数`show()`并传入图像ID和新的图片URL作为参数。

7. rollover.js文件定义了`show()`函数:
    - 首先使用`document.getElementById()`获取ID为`eltId`的元素对象
    - 然后使用`elt.setAttribute("src", URL)`设置该元素的src属性为新的图片URL
    - 从而实现了在鼠标移入/移出时切换图片的效果

这个示例展示了如何结合使用HTML和JavaScript来添加交互行为。通过操作DOM元素的属性,可以动态更新网页内容,提高用户体验。

## Chapter 6: Server-side Programming-Java Servlets

**知识点1: Servlet生命周期**

- 定义: Servlet生命周期描述了Servlet从创建到销毁的整个过程,包括实例化、初始化、服务和销毁四个阶段。
- 用法:
  
  1) 实例化 - Web容器创建Servlet实例
  2) 初始化 - 调用init()方法初始化Servlet
  3) 服务 - 调用service()方法响应客户端请求,service()一般会调用像doGet()这样的方法
  4) 销毁 - 调用destroy()方法销毁Servlet
- 例子:
  
  ```java
  public class HelloCounter extends HttpServlet {
      // 这是Servlet的一个成员变量,用于记录访问次数
      private int visits=0;
  
      /**
       * 响应任何HTTP GET请求,返回一个带访问计数的HTML页面
       * 这个方法对应Servlet生命周期的"服务"阶段
       */
      public void doGet(HttpServletRequest request,
                        HttpServletResponse response) 
        throws ServletException, IOException {
          // 设置响应的内容类型
          response.setContentType("text/html; charset=\"UTF-8\"");
  
          // 获取输出流用于构建响应内容  
          PrintWriter servletOut = response.getWriter();
  
          // 更新访问计数
          visits++;
  
          // 输出HTML响应内容
          servletOut.println("..."); 
          servletOut.close();
      }
  }
  ```

**知识点2: `HttpServletRequest`和`HttpServletResponse`**

- 定义: HttpServletRequest封装了客户端发送的HTTP请求信息,HttpServletResponse用于构建对客户端的响应。
- 用法:
  1) 通过HttpServletRequest可以获取请求参数、请求头、会话信息等
  2) 通过HttpServletResponse可以设置响应状态码、响应头、输出响应内容等
- 例子:
  ```java
  // 获取请求参数
  String name = request.getParameter("name");
  
  // 获取请求头
  String userAgent = request.getHeader("User-Agent");
  
  // 获取或创建会话
  HttpSession session = request.getSession();
  
  // 设置响应状态码 
  response.setStatus(HttpServletResponse.SC_OK);
  
  // 设置响应头
  response.setHeader("Content-Type", "text/html");
  
  // 获取输出流
  PrintWriter out = response.getWriter();
  out.println("Hello World!");
  ```

**知识点3: Servlet会话跟踪**

- 定义: 会话跟踪是Web应用程序在多次请求之间保持状态的机制。
- 用法:
  1) 调用request.getSession()获取或创建HttpSession对象
  2) 通过HttpSession对象存储和获取会话数据
  3) 会话数据可在多次请求之间共享
- 例子:
  ```java
  // 获取或创建会话
  HttpSession session = request.getSession();
  
  // 判断是否是新会话
  if (session.isNew()) {
      // 新会话,更新访问者计数
      visits++;
  }
  
  // 存储会话数据
  session.setAttribute("visits", visits); 
  
  // 获取会话数据
  Integer visitCount = (Integer)session.getAttribute("visits");
  ```

**注释1:**

```java
/* 
 * 这段代码定义了一个继承自HttpServlet的Servlet类HelloCounter
 * HttpServlet是Servlet API中的一个基类,提供了处理HTTP请求的基本功能
 */
public class HelloCounter extends HttpServlet {
    // 这是一个成员变量,用于记录Servlet被访问的次数
    private int visits=0;

    /**
     * 这个方法用于响应HTTP GET请求
     * 当客户端发送GET请求访问这个Servlet时,Web容器会调用这个方法
     * request封装了客户端请求信息,response用于构建对客户端的响应
     */
    public void doGet(HttpServletRequest request,
                      HttpServletResponse response)
      throws ServletException, IOException {
        // 设置响应的内容类型为HTML
        response.setContentType("text/html; charset=\"UTF-8\"");
        
        // 获取输出流,用于输出响应内容到客户端
        PrintWriter servletOut = response.getWriter();

        // 更新访问计数
        visits++;

        // 使用servletOut输出HTML格式的响应内容
        servletOut.println("..."); 
        
        // 关闭输出流
        servletOut.close();
    }
}
```

**注释2:**

```java
// 这行代码获取当前HTTP请求的会话对象,如果不存在则创建一个新的会话
HttpSession session = request.getSession();

// 判断当前会话是否是新创建的
if (session.isNew()) {
    // 如果是新会话,说明是一个新访问者,所以更新访问者计数
    visits++;
}
```

这段代码的作用是: 通过检查会话是否是新创建的,来判断当前请求是否来自一个新的访问者。如果是新访问者,就增加访问者计数visits。会话对象可以在多次请求之间保持状态,所以通过会话对象就可以跟踪访问者。



**完整的HelloCounter**

```java
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

/**
 * 带访问计数的Hello World! servlet
 */
public class HelloCounter extends HttpServlet
{ 
    // 程序（Web服务器）启动后servlet被执行的次数
    private int visits=0;

    /**
     * 响应任何HTTP GET请求，并返回一个带有访问计数的HTML Hello World! 页面。
     */
    public void doGet (HttpServletRequest request,
                       HttpServletResponse response) 
      throws ServletException, IOException
    {
        // 在响应头中设置HTTP内容类型
        response.setContentType("text/html; charset=\"UTF-8\"");
        
        // 获取用于创建响应主体的PrintWriter对象
        PrintWriter servletOut = response.getWriter();

        // 计算对该servlet的URL的访问次数
        visits++;

        // 创建响应主体，包括访问计数
        servletOut.println(
            "<!DOCTYPE html \n" +
            "    PUBLIC \"-//W3C//DTD XHTML 1.0 Strict//EN\" \n" +
            "    \"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd\"> \n" +
            "<html xmlns='http://www.w3.org/1999/xhtml'> \n" +
            "  <head> \n" +
            "    <title> \n" +
            "      HelloCounter.java \n" +
            "    </title> \n" +
            "  </head> \n" + 
            "  <body> \n" +
            "    <p> \n" + 
            "       Hello World! \n" +
            "    </p> \n" +
            "    <p> \n" +
            "       这个页面自服务器最近一次重启以来被访问了 \n" +
            visits +
            "       次。 \n" +
            "    </p> \n" +
            "  </body> \n" +
            "</html> ");
        servletOut.close();
    }
}
```





**完整的VisitorCounter**

```java
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

/**
 * 带访问者计数的Hello World! servlet。
 * 单个用户在短时间内的多次访问被计为一次访问。
 */
public class VisitorCounter extends HttpServlet
{ 
    // 程序（Web服务器）启动后对servlet的访问者数量
    private int visits=0;

    /**
     * 响应任何HTTP GET请求，并返回一个带有访问者计数的HTML Hello World! 页面。
     */
    public void doGet (HttpServletRequest request,
                       HttpServletResponse response) 
      throws ServletException, IOException
    {
        // 在响应头中设置HTTP内容类型
        response.setContentType("text/html; charset=\"UTF-8\"");
        
        // 获取用于创建响应主体的PrintWriter对象
        PrintWriter servletOut = response.getWriter();

        // 确定是否为该用户的第一次访问，如果是，则更新访问计数
        HttpSession session = request.getSession();
        if (session.isNew()) {
            visits++;
        }

        // 创建响应主体，包括访问者计数
        servletOut.println(
            "<!DOCTYPE html \n" +
            "    PUBLIC \"-//W3C//DTD XHTML 1.0 Strict//EN\" \n" +
            "    \"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd\"> \n" +
            "<html xmlns='http://www.w3.org/1999/xhtml'> \n" +
            "  <head> \n" +
            "    <title> \n" +
            "      VisitorCounter.java \n" +
            "    </title> \n" +
            "  </head> \n" + 
            "  <body> \n" +
            "    <p> \n" + 
            "       Hello World! \n" +
            "    </p> \n" +
            "    <p> \n" +
            "       这个页面被访问了 \n" +
            visits +
            "       次，自服务器最近一次重启以来。 \n" +
            "    </p> \n" +
            "  </body> \n" +
            "</html> ");
        servletOut.close();
    }
}

```


