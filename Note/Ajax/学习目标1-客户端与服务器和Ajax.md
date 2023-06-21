# 目录

- [目录](#目录)
  - [学习目标](#学习目标)
  - [1.客户端与服务器](#1客户端与服务器)
    - [1.1上网的目的](#11上网的目的)
    - [1.2服务器](#12服务器)
    - [1.3客户端](#13客户端)
  - [2.URL地址](#2url地址)
    - [2.1 URL地址的概念](#21-url地址的概念)
    - [2.2 URL地址的组成部分](#22-url地址的组成部分)
  - [3.客户端与服务器的通信过程](#3客户端与服务器的通信过程)
    - [3.1图解客户端与服务器的通信过程](#31图解客户端与服务器的通信过程)
    - [3.2基于浏览器的开发者工具分析通信过程](#32基于浏览器的开发者工具分析通信过程)
  - [4.服务器对外提供了哪些资源](#4服务器对外提供了哪些资源)
    - [4.1例举网页中常见的资源](#41例举网页中常见的资源)
    - [4.2数据也是资源](#42数据也是资源)
    - [4.3数据是网页的灵魂](#43数据是网页的灵魂)
    - [4.4网页中如何请求数据](#44网页中如何请求数据)
    - [4.5资源的请求方式](#45资源的请求方式)
  - [5.了解Ajax](#5了解ajax)
    - [5.1什么是Ajax](#51什么是ajax)
    - [5.2为什么要学Ajax](#52为什么要学ajax)
    - [5.3 Ajax的典型应用场景](#53-ajax的典型应用场景)
  - [6. jQuery中的Ajax](#6-jquery中的ajax)
    - [6.1了解jQuery中的Ajax](#61了解jquery中的ajax)
    - [6.2 $.get()函数的语法](#62-get函数的语法)
      - [6.2.1 $.get()发起不带参数的请求](#621-get发起不带参数的请求)
      - [6.2.2 $.get()发起带参数的请求](#622-get发起带参数的请求)
    - [6.3 $.post()函数的语法](#63-post函数的语法)
      - [6.3.1 $.post()向服务器提交数据](#631-post向服务器提交数据)
    - [6.4 $.ajax()函数的语法](#64-ajax函数的语法)
      - [6.4.1 使用$.ajax()发起GET请求](#641-使用ajax发起get请求)
      - [6.4.2 使用$.ajax()发起POST请求](#642-使用ajax发起post请求)
  - [7 接口](#7-接口)
    - [7.1 接口的概念](#71-接口的概念)
  - [7.2 分析接口的请求过程](#72-分析接口的请求过程)
    - [7.2.1 通过GET方式请求接口的过程](#721-通过get方式请求接口的过程)
    - [7.2.2 通过POST方式请求接口的过程](#722-通过post方式请求接口的过程)
  - [7.3接口测试工具](#73接口测试工具)
    - [7.3.1 什么是接口测试工具](#731-什么是接口测试工具)
    - [7.3.2 下载并安装PostMan](#732-下载并安装postman)
    - [7.3.3 了解PostMan界面的组成部分](#733-了解postman界面的组成部分)
    - [7.4 使用PostMan测试GET接口](#74-使用postman测试get接口)
    - [7.5使用PostMan测试POST接口](#75使用postman测试post接口)
    - [7.6 接口文档](#76-接口文档)
      - [7.6.1.什么是接口文档](#761什么是接口文档)
      - [7.6.2.接口文档的组成部分](#762接口文档的组成部分)
      - [7.6.3 接口文档示例](#763-接口文档示例)
  - [8.案例 - 图书管理](#8案例---图书管理)
    - [8.1 渲染UI结构](#81-渲染ui结构)
    - [8.2 案例用到的库和插件](#82-案例用到的库和插件)
    - [8.3 渲染图书列表（核心代码）](#83-渲染图书列表核心代码)
  - [8.4 删除图书（核心代码)](#84-删除图书核心代码)
    - [8.5 添加图书（核心代码）](#85-添加图书核心代码)
  - [9案例 – 聊天机器人](#9案例--聊天机器人)
    - [9.1 演示案例要完成的效果](#91-演示案例要完成的效果)
    - [9.2 梳理案例的代码结构](#92-梳理案例的代码结构)
    - [9.3 将用户输入的内容渲染到聊天窗口](#93-将用户输入的内容渲染到聊天窗口)
    - [9.4 发起请求获取聊天消息](#94-发起请求获取聊天消息)
    - [9.5 将机器人的聊天内容转为语音](#95-将机器人的聊天内容转为语音)
    - [9.6 通过 `<audio>` 播放语音](#96-通过-audio-播放语音)
    - [9.7 使用回车发送消息](#97-使用回车发送消息)

## 学习目标

- 能够知道和服务器相关的基本概念
- 能够知道客户端和服务器通信的过程
- 能够知道数据也是一种资源
- 能够说出什么是Ajax以及应用场景
- 能够使用jQuery中的Ajax函数请求数据
- 能够知道接口和接口文档的概念

## 1.客户端与服务器

### 1.1上网的目的

- 刷微博
- 浏览新闻
- 在线听音乐
- 在线看电影
- etc...

上网的本质目的:通过互联网的形式来获取和消费资源

### 1.2服务器

上网过程中，负责存放和对外提供资源的电脑，叫做服务器。

![服务器](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230112155248.png)

### 1.3客户端

上网过程中，负责获取和消费资源的电脑，叫做客户端。

![客户端](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230112155513.png)

## 2.URL地址

### 2.1 URL地址的概念

URL(全称是UniformResourceLocator)中文叫统一资源定位符，用于标识互联网上每个资源的唯一存放位置。浏览器只有通过URL地址，才能正确定位资源的存放位置，从而成功访问到对应的资源。

常见的URL举例:
<http://www.baidu.com>
<http://www.taobao.com>
<http://www.cnblogs.com/liulongbinblogs/p/11649393.html>

### 2.2 URL地址的组成部分

URL地址一般由三部组成:
①客户端与服务器之间的通信协议
②存有该资源的服务器名称
③资源在服务器上具体的存放位置

![URL地址的组成部分](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230112155617.png)

## 3.客户端与服务器的通信过程

### 3.1图解客户端与服务器的通信过程

![图解客户端与服务器的通信过程](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230112174940.png)

### 3.2基于浏览器的开发者工具分析通信过程

![基于浏览器的开发者工具分析通信过程](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230112175017.png)

1. 打开Chrome浏览器
2. Ctrl+Shift+l打开Chrome的开发者工具
3. 切换到Network面板
4. 选中Doc页签
5. 刷新页面，分析客户端与服务器的通信过程

## 4.服务器对外提供了哪些资源

### 4.1例举网页中常见的资源

![例举网页中常见的资源](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230112175117.png)

### 4.2数据也是资源

网页中的数据，也是服务器对外提供的一种资源。例如股票数据、各行业排行榜等。
![数据也是资源](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230112175146.png)

### 4.3数据是网页的灵魂

![数据是网页的灵魂](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230112175210.png)

### 4.4网页中如何请求数据

数据，也是服务器对外提供的一种资源。只要是资源，必然要通过请求-处理-响应的方式进行获取。

![网页中如何请求数据](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230112175310.png)

如果要在网页中请求服务器上的数据资源，则需要用到XMLHttpRequest对象。
XMLHttpRequest(简称xhr）是浏览器提供的js成员，通过它，可以请求服务器上的数据资源。
最简单的用法`var xhrObj = new XMLHttpRequest()`

### 4.5资源的请求方式

客户端请求服务器时，请求的方式有很多种，最常见的两种请求方式分别为get和post请求。
get请求通常用于获取服务端资源（向服务器要资源)
> 例如:根据URL地址，从服务器获取HTML文件、css文件、js文件、图片文件、数据资源等

post 请求通常用于向服务器提交数据(往服务器发送资源)

> 例如:登录时向服务器提交的登录信息、注册时向服务器提交的注册信息、添加用户时向服务器提交的用户信息等各种数据提交操作

## 5.了解Ajax

### 5.1什么是Ajax

Ajax的全称是Asynchronous Javascript And XML(异步JavaScript和XML)。
通俗的理解:在网页中利用XMLHttpRequest对象和服务器进行数据交互的方式，就是Ajax

### 5.2为什么要学Ajax

之前所学的技术，只能把网页做的更美观漂亮，或添加一些动画效果，但是，Ajax能让我们轻松实现网页与服务器之间的数据交互。
![Ajax交互例图](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113090121.png)

### 5.3 Ajax的典型应用场景

用户名检测:注册用户时，通过ajax的形式，动态检测用户名是否被占用。

![Ajax的典型应用场景1](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113090205.png)

搜索提示:当输入搜索关键字时，通过 ajax的形式，动态加载搜索提示列表。

![Ajax的典型应用场景2](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113090234.png)

数据分页显示:当点击页码值的时候，通过ajax的形式，根据页码值动态刷新表格的数据。

![Ajax的典型应用场景3](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113090300.png)

数据的增删改查:数据的添加、删除、修改、查询操作，都需要通过ajax的形式，来实现数据的交互。

![[Ajax的典型应用场景4](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113090342.png)

## 6. jQuery中的Ajax

### 6.1了解jQuery中的Ajax

浏览器中提供的XMLHttpRequest用法比较复杂，所以jQuery对 XMLHttpRequest进行了封装，提供了一系列Ajax相关的函数，极大地降低了Ajax的使用难度。
jQuery中发起Ajax请求最常用的三个方法如下:

```JS
//JavaScript
$.get()
$.post()
$.ajax()
```

### 6.2 $.get()函数的语法

jQuery 中 $.get()函数的功能单一，专门用来发起get请求，从而将服务器上的资源请求到客户端来进行使用。

```javascript
$.get(url,[data],[callback])
```

中括号为可选项，其中，三个参数各自代表的含义如下:

| 参数名   | 参数类型 | 是否必选 | 说明                     |
| :------- | :------- | :------- | :----------------------- |
| url      | string   | 是       | 要请求的资源地址         |
| data     | object   | 否       | 请求资源期间要携带的参数 |
| callback | function | 否       | 请求成功时的回调函数     |

#### 6.2.1 $.get()发起不带参数的请求

使用$.get(函数发起不带参数的请求时，直接提供请求的URL地址和请求成功之后的回调函娄
即可，示例代码如下:

```JS

$.get('http://www.liulongbin.top:3006/api/getbooks', function(res) {
    console.log(res); // 这里的 res 是服务器返回的数据
})
```

所有的AJAX请求都可以通过XHR进行查看
![调试get请求](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113090833.png)

>`CTRL`+`SHIFT`+`I`打开开发者工具

```javascript
<body>

    <button id="btnGET">发起不带参数的get请求</button>
    <script src="./lib/jquery.js"></script>
    <script>
        $(function () {
            $("#btnGET").on('click', function () {
                $.get("http://www.liulongbin.top:3006/api/getbooks", function (res) {
                    console.log(res);
                })
            })
        })
    </script>
</body>
```



#### 6.2.2 $.get()发起带参数的请求

使用 $.get() 函数发起带参数的请求时，示例代码如下：

```JS
//JavaScript
$.get('http://www.liulongbin.top:3006/api/getbooks', { id: 1 }, function(res) {
    console.log(res);
 })
```

![发起带参数的请求](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113091023.png)

```javascript
<body>
    <button id="btnGetInfo">发起带参数的请求</button>
    <script src="./lib/jquery.js"></script>
    <script>
        $("#btnGetInfo").on('click', function () {
            $.get('http://www.liulongbin.top:3006/api/getbooks', { id: 1 }, function (res) {
                console.log(res);
            })
        })
    </script>
</body>
```



### 6.3 $.post()函数的语法

jQuery 中 $.post() 函数的功能单一，专门用来发起 post 请求，从而向服务器提交数据。

```javascript
$.post() 函数的语法如下：
	$.post(url, [data], [callback])
```

其中，三个参数各自代表的含义如下：

| 参数名   | 参数类型 | 是否必选 | 说明                     |
| :------- | :------- | :------- | :----------------------- |
| url      | string   | 是       | 提交数据的地址           |
| data     | object   | 否       | 要提交的数据             |
| callback | function | 否       | 数据提交成功时的回调函数 |

#### 6.3.1 $.post()向服务器提交数据

使用 $post() 向服务器提交数据的示例代码如下：
参数类型：对象

```JS
//JavaScript
$.post(
   
    'http://www.liulongbin.top:3006/api/addbook', // 请求的URL地址
     { bookname: '水浒传', author: '施耐庵', publisher: '上海图书出版社' }, // 提交的数据
  
      function(res) { // 回调函数      
      console.log(res)；   
      }
 
)
```

![返回值](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113091351.png)

### 6.4 $.ajax()函数的语法

相比于 `$.get()` 和 `$.post()` 函数，jQuery 中提供的 `$.ajax()` 函数，是一个功能比较综合的函数，它允许我们对 Ajax 请求进行更详细的配置。
`$.ajax()` 函数的基本语法如下：

```JavaScript
$.ajax({
    type: '', // 请求的方式，例如 GET 或 POST
    url: '',  // 请求的 URL 地址
    data: { },// 这次请求要携带的数据
    success: function(res) { } // 请求成功之后的回调函数
})
```

#### 6.4.1 使用$.ajax()发起GET请求

用 $.ajax() 发起 GET 请求时，只需要将 type 属性的值设置为 'GET' 即可

```JS
//JavaScript
$.ajax({
    type: 'GET', // 请求的方式
    url: 'http://www.liulongbin.top:3006/api/getbooks',  // 请求的 URL 地址
    data: { id: 1 },// 这次请求要携带的数据
    success: function(res) { // 请求成功之后的回调函数
    console.log(res)
    }
})
```

#### 6.4.2 使用$.ajax()发起POST请求

```JS
//JavaScript
$.ajax({
    type: 'POST', // 请求的方式
    url: 'http://www.liulongbin.top:3006/api/addbook',  // 请求的 URL 地址
    data: { // 要提交给服务器的数据
        bookname: '水浒传',
        author: '施耐庵',
        publisher: '上海图书出版社'
    },
    success: function(res) { // 请求成功之后的回调函数
        console.log(res)
    }
}
```

## 7 接口

### 7.1 接口的概念

使用 Ajax 请求数据时，被请求的 URL 地址，就叫做数据接口（简称接口）。同时，每个接口必须有请求方式。
例如：
<http://www.liulongbin.top:3006/api/getbooks>  获取图书列表的接口(GET请求)
<http://www.liulongbin.top:3006/api/addbook>   添加图书的接口（POST请求）

## 7.2 分析接口的请求过程

### 7.2.1 通过GET方式请求接口的过程

![通过GET方式请求接口的过程](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113091907.png)

### 7.2.2 通过POST方式请求接口的过程

![通过POST方式请求接口的过程](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113091949.png)

## 7.3接口测试工具

### 7.3.1 什么是接口测试工具

为了验证接口能否被正常被访问，我们常常需要使用接口测试工具，来对数据接口进行检测。
好处：接口测试工具能让我们在不写任何代码的情况下，对接口进行调用和测试。
![什么是接口测试工具](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113092039.png)

### 7.3.2 下载并安装PostMan

访问 PostMan 的官方下载网址 <https://www.getpostman.com/downloads/>，下载所需的安装程序后，直接安装即可。
![下载并安装PostMan](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113092112.png)

### 7.3.3 了解PostMan界面的组成部分

PostMan界面的组成部分，从上到下，从左到右，分别是：

> - 菜单栏
> - 工具栏
> - 左侧历史记录与集合面板
> - 请求页签
> - 请求地址区域
> - 请求参数区域
> - 响应结果区域
> - 状态栏

![了解PostMan界面的组成部分](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113092152.png)

### 7.4 使用PostMan测试GET接口

> 步骤：
1.选择请求的方式
2.填写请求的URL地址
3.填写请求的参数
4.点击 Send 按钮发起 GET 请求
5.查看服务器响应的结果

![使用PostMan测试GET接口](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113092325.png)

### 7.5使用PostMan测试POST接口

>步骤：
1.选择请求的方式
2.填写请求的URL地址
3.选择 Body 面板并勾选数据格式
4.填写要发送到服务器的数据
5.点击 Send 按钮发起 POST 请求
6.查看服务器响应的结果

![使用PostMan测试POST接口](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113092453.png)

### 7.6 接口文档

#### 7.6.1.什么是接口文档

接口文档，顾名思义就是接口的说明文档，它是我们调用接口的依据。好的接口文档包含了对接口URL，参数以及输出内容的说明，我们参照接口文档就能方便的知道接口的作用，以及接口如何进行调用。

#### 7.6.2.接口文档的组成部分

接口文档可以包含很多信息，也可以按需进行精简，不过，一个合格的接口文档，应该包含以下6项内容，从而为接口的调用提供依据：
> 接口名称：用来标识各个接口的简单说明，如登录接口，获取图书列表接口等。
> 接口URL：接口的调用地址。
> 调用方式：接口的调用方式，如 GET 或 POST。
> 参数格式：接口需要传递的参数，每个参数必须包含参数名称、参数类型、是否必选、参数说明这4项内容。
> 响应格式：接口的返回值的详细描述，一般包含数据名称、数据类型、说明3项内容。
> 返回示例（可选）：通过对象的形式，例举服务器返回数据的结构。

#### 7.6.3 接口文档示例

![接口文档示例1](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113092653.png)

![接口文档示例2](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113092711.png)

![接口文档示例3](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113092735.png)

## 8.案例 - 图书管理

### 8.1 渲染UI结构

![渲染UI结构](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113092815.png)

### 8.2 案例用到的库和插件

用到的 css 库 bootstrap.css
用到的 javascript 库 jquery.js
用到的 vs code 插件 Bootstrap 3 Snippets
使用方法：输入bs3

![bootstrap使用案例](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230113092847.png)

### 8.3 渲染图书列表（核心代码）

```JavaScript
function getBookList() {
    // 1. 发起 ajax 请求获取图书列表数据
    $.get('http://www.liulongbin.top:3006/api/getbooks', function(res) {
        // 2. 获取列表数据是否成功
        if (res.status !== 200) return alert('获取图书列表失败！')
        // 3. 渲染页面结构
        var rows = []
        $.each(res.data, function(i, item) { // 4. 循环拼接字符串
            rows.push('<tr><td>' + item.id + '</td><td>' + item.bookname + '</td><td>' + item.author + '</td><td>' + item.publisher + '</td><td><a href="javascript:;">删除</a></td></tr>')
           })
        $('#bookBody').empty().append(rows.join('')) // 5. 渲染表格结构
    })
}
```

## 8.4 删除图书（核心代码)

 W3C规范自定义属性 要以data-开头。

```JS
//JavaScript
 //无法绑定 因为DOM元素.del还未被渲染
     /**
     *  $('.del').on('click', function () {
     *       console.log('ok')
     *  })
     */
    

        // 通过代理的方式为动态添加的元素绑定点击事件
      $('tbody').on('click', '.del', function () {
        var id = $(this).attr('data-id')
        $.get('http://www.liulongbin.top:3006/api/delbook', { id: id }, function (res) {
          if (res.status !== 200) return alert('删除图书失败！')
          getBookList();
        })
      }
```

### 8.5 添加图书（核心代码）

```JS
//JavaScript
// 1. 检测内容是否为空
var bookname = $('#bookname').val()
var author = $('#author').val()
var publisher = $('#publisher').val()
if (bookname === '' || author === '' || publisher === '') {
    return alert('请完整填写图书信息！')
}
// 2. 发起 ajax 请求，添加图书信息
$.post(
    'http://www.liulongbin.top:3006/api/addbook',
    { bookname: bookname, author: author, publisher: publisher },
        function(res) {
        // 3. 判断是否添加成功
        if (res.status !== 201) return alert('添加图书失败！')
            getBookList() // 4. 添加成功后，刷新图书列表
            $('input:text').val('') // 5. 清空文本框内容
            }    
)
```

## 9案例 – 聊天机器人

### 9.1 演示案例要完成的效果

> 实现步骤：
>
> 1. 梳理案例的代码结构
> 2. 将用户输入的内容渲染到聊天窗口
> 3. 发起请求获取聊天消息
> 4. 将机器人的聊天内容转为语音
> 5. 通过 `<audio>`播放语音
> 6. 使用回车键发送消息

### 9.2 梳理案例的代码结构

梳理页面的 UI 布局
将业务代码抽离到 chat.js 中
了解 resetui() 函数的作用

### 9.3 将用户输入的内容渲染到聊天窗口

```JS
//JavaScript
// 为发送按钮绑定点击事件处理函数
$('#btnSend').on('click', function () {
    var text = $('#ipt').val().trim() // 获取用户输入的内容
    if (text.length <= 0) { // 判断用户输入的内容是否为空
       return $('#ipt').val('')
    }
    // 将用户输入的内容显示到聊天窗口中
    $('#talk_list').append('<li class="right_word"><img src="img/person02.png" /> <span>' + text + '</span></li>')
    resetui() // 重置滚动条的位置
    $(‘#ipt’).val('') // 清空输入框的内容
// TODO: 发起请求，获取聊天消息
})    
```

### 9.4 发起请求获取聊天消息

```JS
//JavaScript
function getMsg(text) {
    $.ajax({
      method: 'GET',
      url: 'http://ajax.frontend.itheima.net:3006/api/robot',
      data: {
        spoken: text
      },
      success: function (res) {
        if (res.message === 'success') {
            var msg = res.data.info.text
            $('#talk_list').append('<li class="left_word"><img src="img/person01.png" /> <span>' + msg + '</span></li>')
            resetui()
            // TODO: 发起请求，将机器人的聊天消息转为语音格式
        }
      }
    })
```

### 9.5 将机器人的聊天内容转为语音

```JS
//JavaScript
function getVoice(text) {
    $.ajax({
      method: 'GET',
      url: 'http://ajax.frontend.itheima.net:3006/api/synthesize',
      data: {
        text: text
      },
      success: function (res) {
// 如果请求成功，则 res.voiceUrl 是服务器返回的音频 URL 地址
        if (res.status === 200) {
            $('#voice').attr('src', res.voiceUrl)
        }
      }
    })
  }
```

### 9.6 通过 `<audio>` 播放语音

<!-- 音频播放语音内容 -->
`<audio src="" id="voice" autoplay style="display: none;"></audio>`

### 9.7 使用回车发送消息

```JS
//JavaScript
// 让文本输入框响应回车事件后，提交消息
$('#ipt').on('keyup', function (e) {
// e.keyCode 可以获取到当前按键的编码
    if (e.keyCode === 13) {
// 调用按钮元素的 click 函数，可以通过编程的形式触发按钮的点击事件
        $('#btnSend').click()
    }
})
```
