# 目录

- [目录](#目录)
  - [目标](#目标)
  - [1. XMLHttpRequest的基本使用](#1-xmlhttprequest的基本使用)
    - [1.1 什么XMLHttpRequest](#11-什么xmlhttprequest)
    - [1.2 使用xhr发起GET请求](#12-使用xhr发起get请求)
    - [1.3 了解xhr对象的readyState属性](#13-了解xhr对象的readystate属性)
    - [1.4 使用xhr发起带参数的GET请求](#14-使用xhr发起带参数的get请求)
    - [1.5 查询字符串](#15-查询字符串)
      - [1.5.1 什么是查询字符串](#151-什么是查询字符串)
      - [1.5.2. GET请求携带参数的本质](#152-get请求携带参数的本质)
    - [1.6 URL编码与解码](#16-url编码与解码)
      - [1.6.1 什么是URL编码](#161-什么是url编码)
      - [1.6.2 如何对URL进行编码与解码](#162-如何对url进行编码与解码)
      - [1.6.3 URL编码的注意事项](#163-url编码的注意事项)
    - [1.7 使用xhr发起POST请求](#17-使用xhr发起post请求)
  - [2. 数据交换格式](#2-数据交换格式)
    - [2.1 什么是数据交换格式](#21-什么是数据交换格式)
    - [2.2 XML](#22-xml)
    - [2.2.1  什么是XML](#221--什么是xml)
    - [2.2.2 XML和HTML的区别](#222-xml和html的区别)
    - [2.2.3 XML的缺点](#223-xml的缺点)
    - [2.3 JSON](#23-json)
      - [2.3.1 什么是JSON](#231-什么是json)
      - [2.3.2 JSON的两种结构](#232-json的两种结构)
      - [2.3.3 JSON语法注意事项](#233-json语法注意事项)
      - [2.3.4 JSON和JS对象的关系](#234-json和js对象的关系)
      - [2.3.5 JSON和JS对象的互转](#235-json和js对象的互转)
      - [2.3.6 序列化和反序列化](#236-序列化和反序列化)
  - [3. 封装自己的Ajax函数](#3-封装自己的ajax函数)
    - [3.1 要实现的效果](#31-要实现的效果)
    - [3.2 定义options参数选项](#32-定义options参数选项)
    - [3.3 处理data参数](#33-处理data参数)
    - [3.4 定义itheima函数](#34-定义itheima函数)
    - [3.5 判断请求的类型](#35-判断请求的类型)
  - [4. XMLHttpRequest Level2的新特性](#4-xmlhttprequest-level2的新特性)
    - [4.1 认识XMLHttpRequest Level2](#41-认识xmlhttprequest-level2)
      - [4.1.1 旧版XMLHttpRequest的缺点](#411-旧版xmlhttprequest的缺点)
      - [4.1.2 XMLHttpRequest Level2的新功能](#412-xmlhttprequest-level2的新功能)
    - [4.2 设置HTTP请求时限](#42-设置http请求时限)
    - [4.3 FormData对象管理表单数据](#43-formdata对象管理表单数据)
    - [4.4 上传文件](#44-上传文件)
      - [4.4.1. 定义UI结构](#441-定义ui结构)
      - [4.4.2 验证是否选择了文件](#442-验证是否选择了文件)
      - [4.4.3. 向FormData中追加文件](#443-向formdata中追加文件)
      - [4.4.4 使用 xhr 发起上传文件的请求](#444-使用-xhr-发起上传文件的请求)
      - [4.4.5 监听onreadystatechange事件](#445-监听onreadystatechange事件)
    - [4.5 显示文件上传进度](#45-显示文件上传进度)
      - [4.5.1 导入需要的库](#451-导入需要的库)
      - [4.5.2 基于Bootstrap渲染进度条](#452-基于bootstrap渲染进度条)
      - [4.5.3  监听上传进度的事件](#453--监听上传进度的事件)
      - [4.5.4 监听上传完成的事件](#454-监听上传完成的事件)
  - [5. jQuery高级用法](#5-jquery高级用法)
    - [5.1 jQuery实现文件上传](#51-jquery实现文件上传)
      - [5.1.1. 定义UI结构](#511-定义ui结构)
      - [5.1.2 验证是否选择了文件](#512-验证是否选择了文件)
      - [5.1.3 向FormData中追加文件](#513-向formdata中追加文件)
      - [5.1.4 使用jQuery发起上传文件的请求](#514-使用jquery发起上传文件的请求)
    - [5.2 jQuery实现loading效果](#52-jquery实现loading效果)
      - [5.2.1 ajaxStart(callback)](#521-ajaxstartcallback)
      - [5.2.2 2. ajaxStop(callback)](#522-2-ajaxstopcallback)
  - [6. axios](#6-axios)
    - [6.1 什么是axios](#61-什么是axios)
    - [6.2 axios发起GET请求](#62-axios发起get请求)
    - [6.3 axios发起POST请求](#63-axios发起post请求)
    - [6.4 直接使用axios发起请求](#64-直接使用axios发起请求)
      - [6.4.1 直接使用axios发起GET请求](#641-直接使用axios发起get请求)
      - [6.4.2 直接使用axios发起POST请求](#642-直接使用axios发起post请求)
    - [7 表格对比三种请求方式](#7-表格对比三种请求方式)
      - [GET请求](#get请求)

## 目标

- 能够知道如何使用XMLHttpRequest发起Ajax请求
- 能够知道如何封装自己的Ajax函数
- 能够使用XMLHttpRequest Level2中提供的新特性
- 能够知道jQuery中如何实现文件上传与loading效果
- 能够知道如何使用axios发起Ajax请求

## 1. XMLHttpRequest的基本使用

### 1.1 什么XMLHttpRequest

XMLHttpRequest（简称 xhr）是浏览器提供的 Javascript 对象，通过它，可以请求服务器上的数据资源。之前所学的 jQuery 中的 Ajax 函数，就是基于 xhr 对象封装出来的。

```mermaid
graph TD
A[XMLHttpRequest] --> B[JQUery中的Ajax]
    B --> C[$.get]
    B --> D[$.post]
    B --> E[$.ajax]    

```

思考：能否直接使用xhr对象
发起Ajax请求？

### 1.2 使用xhr发起GET请求

步骤：

1. 创建 xhr 对象
2. 调用 xhr.open() 函数
3. 调用 xhr.send() 函数
4. 监听 xhr.onreadystatechange 事件  

``` JavaScript
// 1. 创建 XHR 对象

var xhr = new XMLHttpRequest()
// 2. 调用 open 函数，指定 请求方式 与 URL地址
xhr.open('GET', 'http://www.liulongbin.top:3006/api/getbooks')
// 3. 调用 send 函数，发起 Ajax 请求
xhr.send()
// 4. 监听 onreadystatechange 事件
xhr.onreadystatechange = function() {
    // 4.1 监听 xhr 对象的请求状态 readyState ；与服务器响应的状态 status
    if (xhr.readyState === 4 && xhr.status === 200) { //固定写法
        // 4.2 打印服务器响应回来的数据
        console.log(xhr.responseText)
    }
}

```

### 1.3 了解xhr对象的readyState属性

XMLHttpRequest 对象的 readyState 属性，用来表示当前 Ajax 请求所处的状态。每个 Ajax 请求必然处于以下状态中的一个：
| 值  | 状态             | 描述                                                |
| --- | ---------------- | --------------------------------------------------- |
| 0   | UNSENT           | XMLHttpRequest 对象已被创建，但尚未调用 open方法。  |
| 1   | OPENED           | open() 方法已经被调用。                             |
| 2   | HEADERS_RECEIVED | send() 方法已经被调用，响应头也已经被接收。         |
| 3   | LOADING          | 数据接收中，此时 response 属性中已经包含部分数据。  |
| 4   | DONE             | Ajax 请求完成，这意味着数据传输已经彻底完成或失败。 |

### 1.4 使用xhr发起带参数的GET请求

使用 xhr 对象发起带参数的 GET 请求时，只需在调用 xhr.open 期间，为 URL 地址指定参数即可：

```JavaScript
// ...省略不必要的代码
xhr.open('GET', 'http://www.liulongbin.top:3006/api/getbooks?id=1')
// ...省略不必要的代码
```

这种在 URL 地址后面拼接的参数，叫做==查询字符串==。

### 1.5 查询字符串

#### 1.5.1 什么是查询字符串

定义：查询字符串（URL 参数）是指在 URL 的末尾加上用于向服务器发送信息的字符串（变量）。
格式：将英文的 ? 放在URL 的末尾，然后再加上 参数＝值 ，想加上多个参数的话，使用 & 符号进行分隔。以这个形式，可以将想要发送给服务器的数据添加到 URL 中。

```url地址
// 不带参数的 URL 地址
http://www.liulongbin.top:3006/api/getbooks
// 带一个参数的 URL 地址
http://www.liulongbin.top:3006/api/getbooks?id=1
// 带两个参数的 URL 地址
http://www.liulongbin.top:3006/api/getbooks?id=1&bookname=西游记
```

#### 1.5.2. GET请求携带参数的本质

无论使用 `$.ajax()`，还是使用 `$.get()`，又或者直接使用 xhr 对象发起 GET 请求，当需要携带参数的时候，本质上，都是直接将参数以查询字符串的形式，追加到 URL 地址的后面，发送到服务器的。

```JavaScript
$.get('url', {name: 'zs', age: 20}, function() {})
// 等价于
$.get('url?name=zs&age=20', function() {})

$.ajax({ method: 'GET', url: 'url', data: {name: 'zs', age: 20}, success: function() {} })
// 等价于
$.ajax({ method: 'GET', url: 'url?name=zs&age=20', success: function() {} })

```

### 1.6 URL编码与解码

#### 1.6.1 什么是URL编码

- URL 地址中，只允许出现英文相关的字母、标点符号、数字，因此，在 URL 地址中不允许出现中文字符。
- 如果 URL 中需要包含中文这样的字符，则必须对中文字符进行编码（转义）。
- URL编码的原则：使用安全的字符（没有特殊用途或者特殊意义的可打印字符）去表示那些不安全的字符。
- URL编码原则的通俗理解：使用英文字符去表示非英文字符。

```URL
http://www.liulongbin.top:3006/api/getbooks?id=1&bookname=西游记
// 经过 URL 编码之后，URL地址变成了如下格式：中文字符编码是三组百分号
http://www.liulongbin.top:3006/api/getbooks?id=1&bookname=%E8%A5%BF%E6%B8%B8%E8%AE%B0
```

#### 1.6.2 如何对URL进行编码与解码

浏览器提供了 URL 编码与解码的 API，分别是：
    encodeURI()  编码的函数
    decodeURI()  解码的函数

```JavaScript
encodeURI('黑马程序员')
// 输出字符串  %E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98
decodeURI('%E9%BB%91%E9%A9%AC')
// 输出字符串  黑马

```

#### 1.6.3 URL编码的注意事项

由于浏览器会自动对 URL 地址进行编码操作，因此，大多数情况下，程序员不需要关心 URL 地址的编码与解码操作。

更多关于 URL 编码的知识，请参考如下博客：
<https://blog.csdn.net/Lxd_0111/article/details/78028889>

### 1.7 使用xhr发起POST请求

步骤：

1. 创建 xhr 对象
2. 调用 xhr.open() 函数
3. 设置 Content-Type 属性（固定写法）
4. 调用 xhr.send() 函数，同时指定要发送的数据
5. 监听 xhr.onreadystatechange 事件

```JavaScript
// 1. 创建 xhr 对象
var xhr = new XMLHttpRequest()
// 2. 调用 open()
xhr.open('POST', 'http://www.liulongbin.top:3006/api/addbook')
// 3. 设置 Content-Type 属性（固定写法）
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')
// 4. 调用 send()，同时将数据以查询字符串的形式，提交给服务器
xhr.send('bookname=水浒传&author=施耐庵&publisher=天津图书出版社')
// 5. 监听 onreadystatechange 事件
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        console.log(xhr.responseText)
    }
}

```

## 2. 数据交换格式

### 2.1 什么是数据交换格式

数据交换格式，就是服务器端与客户端之间进行数据传输与交换的格式。
前端领域，经常提及的两种数据交换格式分别是 XML 和 JSON。其中 XML 用的非常少，所以，我们重点要学习的数据交换格式就是 JSON。
![数据交换](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230111111232.png)

### 2.2 XML

### 2.2.1  什么是XML

XML 的英文全称是 EXtensible Markup Language，即可扩展标记语言。因此，XML 和 HTML 类似，也是一种标记语言。

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Document</title>
  </head>
  <body></body>
</html>
```

```XML
<note>
  <to>ls</to>    //从谁
  <from>zs</from>  //到谁
  <heading>通知</heading> //标题
  <body>晚上开会</body>   //内容 
</note>

```

### 2.2.2 XML和HTML的区别

XML 和 HTML 虽然都是标记语言，但是，它们两者之间没有任何的关系。

- HTML 被设计用来描述网页上的内容，是网页内容的载体
- XML 被设计用来传输和存储数据，是数据的载体
![数据交换](https://gitee.com/AuroraManito/ampic-go/raw/master/ajax/itheima/20230111111521.png)

### 2.2.3 XML的缺点

```XML
<note>
  <to>ls</to>
  <from>zs</from>
  <heading>通知</heading>
  <body>晚上开会</body>
</note>
```

1. XML 格式臃肿，和数据无关的代码多，体积大，传输效率低
2. 在 Javascript 中解析 XML 比较麻烦

### 2.3 JSON

#### 2.3.1 什么是JSON

- 概念：JSON 的英文全称是 JavaScript Object Notation，即“JavaScript 对象表示法”。简单来讲，JSON 就是 Javascript 对象和数组的字符串表示法，它使用文本表示一个 JS 对象或数组的信息，因此，JSON 的本质是字符串。
- 作用：JSON 是一种轻量级的文本数据交换格式，在作用上类似于 XML，专门用于存储和传输数据，但是 JSON 比 XML 更小、更快、更易解析。
- 现状：JSON 是在 2001 年开始被推广和使用的数据格式，到现今为止，JSON 已经成为了主流的数据交换格式。

#### 2.3.2 JSON的两种结构

JSON 就是用字符串来表示 Javascript 的对象和数组。所以，JSON 中包含对象和数组两种结构，通过这两种结构的相互嵌套，可以表示各种复杂的数据结构。

==对象结构==：对象结构在 JSON 中表示为 `{ }` 括起来的内容。数据结构为 `{ key: value, key: value, … }` 的键值对结构。其中，key 必须是使用英文的双引号包裹的字符串，value 的数据类型可以是数字、字符串、布尔值、null、数组、对象6种类型。

```JSON
//不合法的案例
{
    name: "zs",
    'age': 20,
    "gender": '男',
    "address": undefined,
    "hobby": ["吃饭", "睡觉", '打豆豆']
    say: function() {}
}
//标准的JSON案例
{
    "name": "zs",
    "age": 20,
    "gender": "男",
    "address": null,
    "hobby": ["吃饭", "睡觉", "打豆豆"]
}

```

==数组结构==：数组结构在 JSON 中表示为 [ ] 括起来的内容。数据结构为 [ "java", "javascript", 30, true … ] 。数组中数据的类型可以是数字、字符串、布尔值、null、数组、对象6种类型。

```JSON
[ "java", "python", "php" ]
[ 100, 200, 300.5 ]
[ true, false, null ]
[ { "name": "zs", "age": 20}, { "name": "ls", "age": 30} ]
[ [ "苹果", "榴莲", "椰子" ], [ 4, 50, 5 ] ]
```

#### 2.3.3 JSON语法注意事项

1. 属性名必须使用双引号包裹
2. 字符串类型的值必须使用双引号包裹
3. JSON 中不允许使用单引号表示字符串
4. JSON 中不能写注释
5. JSON 的最外层必须是对象或数组格式
6. 不能使用 undefined 或函数作为 JSON 的值

JSON 的作用：在计算机与网络之间存储和传输数据。
JSON 的本质：用字符串来表示 Javascript 对象数据或数组数据。

#### 2.3.4 JSON和JS对象的关系

JSON 是 JS 对象的字符串表示法，它使用文本表示一个 JS 对象的信息，本质是一个字符串。例如：

```JavaScript
//这是一个对象
var obj = {a: 'Hello', b: 'World'}

//这是一个 JSON 字符串，本质是一个字符串
var json = '{"a": "Hello", "b": "World"}'
```

#### 2.3.5 JSON和JS对象的互转

要实现从 JSON 字符串转换为 JS 对象，使用 JSON.parse() 方法：

```JavaScript
var obj = JSON.parse('{"a": "Hello", "b": "World"}')
//结果是 {a: 'Hello', b: 'World'}
```

要实现从 JS 对象转换为 JSON 字符串，使用 JSON.stringify() 方法：

```JavaScript
var json = JSON.stringify({a: 'Hello', b: 'World'})
//结果是 '{"a": "Hello", "b": "World"}'
```

#### 2.3.6 序列化和反序列化

把数据对象转换为字符串的过程，叫做序列化，例如：调用 JSON.stringify() 函数的操作，叫做 JSON 序列化。
把字符串转换为数据对象的过程，叫做反序列化，例如：调用 JSON.parse() 函数的操作，叫做 JSON 反序列化。

## 3. 封装自己的Ajax函数

### 3.1 要实现的效果

```JavaScript
<!-- 1. 导入自定义的ajax函数库 -->
<script src="./itheima.js"></script>

<script>
    // 2. 调用自定义的 itheima 函数，发起 Ajax 数据请求
    itheima({
        method: '请求类型',
        url: '请求地址',
        data: { /* 请求参数对象 */ },
        success: function(res) { // 成功的回调函数
            console.log(res)     // 打印数据
        }
    })
</script>

```

### 3.2 定义options参数选项

itheima() 函数是我们自定义的 Ajax 函数，它接收一个配置对象作为参数，配置对象中可以配置如下属性：

- method   请求的类型
- url           请求的 URL 地址
- data        请求携带的数据
- success   请求成功之后的回调函数

### 3.3 处理data参数

需要把 data 对象，转化成查询字符串的格式，从而提交给服务器，因此提前定义 resolveData 函数如下：

```javascript
/**
 * 处理 data 参数
 * @param {data} 需要发送到服务器的数据
 * @returns {string} 返回拼接好的查询字符串 name=zs&age=10
 */
function resolveData(data) {
  var arr = []
  for (var k in data) {
    arr.push(k + '=' + data[k])
  }
  return arr.join('&')
}
```

### 3.4 定义itheima函数

在 itheima() 函数中，需要创建 xhr 对象，并监听 onreadystatechange 事件：

```JavaScript
function itheima(options) {
  var xhr = new XMLHttpRequest()
  // 拼接查询字符串
  var qs = resolveData(options.data)

  // 监听请求状态改变的事件
  xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
      var result = JSON.parse(xhr.responseText)
      options.success(result)
    }
  }
}
```

### 3.5 判断请求的类型

不同的请求类型，对应 xhr 对象的不同操作，因此需要对请求类型进行 if … else … 的判断：

```JavaScript
 if (options.method.toUpperCase() === 'GET') {
    // 发起 GET 请求
    xhr.open(options.method, options.url + '?' + qs)
    xhr.send()
  } else if (options.method.toUpperCase() === 'POST') {
    // 发起 POST 请求
    xhr.open(options.method, options.url)
    xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')
    xhr.send(qs)
  }

```

## 4. XMLHttpRequest Level2的新特性

### 4.1 认识XMLHttpRequest Level2

#### 4.1.1 旧版XMLHttpRequest的缺点

1. 只支持文本数据的传输，无法用来读取和上传文件
2. 传送和接收数据时，没有进度信息，只能提示有没有完成

#### 4.1.2 XMLHttpRequest Level2的新功能

- 可以设置 HTTP 请求的时限
- 可以使用 FormData 对象管理表单数据
- 可以上传文件
- 可以获得数据传输的进度信息

### 4.2 设置HTTP请求时限

有时，Ajax 操作很耗时，而且无法预知要花多少时间。如果网速很慢，用户可能要等很久。新版本的 XMLHttpRequest 对象，增加了 timeout 属性，可以设置 HTTP 请求的时限
`xhr.timeout = 3000`
上面的语句，将最长等待时间设为 3000 毫秒。过了这个时限，就自动停止HTTP请求。与之配套的还有一个 timeout 事件，用来指定回调函数：

```Javascript
 xhr.ontimeout = function(event){
     alert('请求超时！')
 }
```

见：[09.设置超时时限.html](https://gitee.com/AuroraManito/note/tree/master/sgg/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98AJAX%E9%9B%B6%E5%9F%BA%E7%A1%80%E5%88%B0%E7%B2%BE%E9%80%9A_%E6%95%B4%E5%90%88Git%E6%A0%B8%E5%BF%83%E5%86%85%E5%AE%B9%E5%85%A8%E5%A5%97%E6%95%99%E7%A8%8B/AJAX%E5%8A%A0%E5%BC%BA%E8%B5%84%E6%96%99/code/09.设置超时时限.html)

### 4.3 FormData对象管理表单数据

Ajax 操作往往用来提交表单数据。为了方便表单处理，HTML5 新增了一个 FormData 对象，可以模拟表单操作：
见：[10.演示FormData对象的基本使用.html](https://gitee.com/AuroraManito/note/tree/master/sgg/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98AJAX%E9%9B%B6%E5%9F%BA%E7%A1%80%E5%88%B0%E7%B2%BE%E9%80%9A_%E6%95%B4%E5%90%88Git%E6%A0%B8%E5%BF%83%E5%86%85%E5%AE%B9%E5%85%A8%E5%A5%97%E6%95%99%E7%A8%8B/AJAX%E5%8A%A0%E5%BC%BA%E8%B5%84%E6%96%99/code/10.演示FormData对象的基本使用.html)

```JavaScript
      // 1. 新建 FormData 对象
      var fd = new FormData()
      // 2. 为 FormData 添加表单项
      fd.append('uname', 'zs')
      fd.append('upwd', '123456')
      // 3. 创建 XHR 对象
      var xhr = new XMLHttpRequest()
      // 4. 指定请求类型与URL地址
      xhr.open('POST', 'http://www.liulongbin.top:3006/api/formdata')
      // 5. 直接提交 FormData 对象，这与提交网页表单的效果，完全一样
      xhr.send(fd)

```

FormData对象也可以用来获取网页表单的值，
HTML见 [11.使用FormData快速获取表单中的数据.html](https://gitee.com/AuroraManito/note/tree/master/sgg/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98AJAX%E9%9B%B6%E5%9F%BA%E7%A1%80%E5%88%B0%E7%B2%BE%E9%80%9A_%E6%95%B4%E5%90%88Git%E6%A0%B8%E5%BF%83%E5%86%85%E5%AE%B9%E5%85%A8%E5%A5%97%E6%95%99%E7%A8%8B/AJAX%E5%8A%A0%E5%BC%BA%E8%B5%84%E6%96%99/code/11.使用FormData快速获取表单中的数据.html)

示例代码如下：

```JavaScript
 // 获取表单元素
 var form = document.querySelector('#form1')
 // 监听表单元素的 submit 事件
 form.addEventListener('submit', function(e) {
    e.preventDefault()
     // 根据 form 表单创建 FormData 对象，会自动将表单数据填充到 FormData 对象中
     var fd = new FormData(form)
     var xhr = new XMLHttpRequest()
     xhr.open('POST', 'http://www.liulongbin.top:3006/api/formdata')
     xhr.send(fd)
     xhr.onreadystatechange = function() {}
})
```

### 4.4 上传文件

新版 XMLHttpRequest 对象，不仅可以发送文本信息，还可以上传文件。
实现步骤：

1. 定义 UI 结构
2. 验证是否选择了文件
3. 向 FormData 中追加文件
4. 使用 xhr 发起上传文件的请求
5. 监听 onreadystatechange 事件

源码：[12.上传文件.html](https://gitee.com/AuroraManito/note/tree/master/sgg/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98AJAX%E9%9B%B6%E5%9F%BA%E7%A1%80%E5%88%B0%E7%B2%BE%E9%80%9A_%E6%95%B4%E5%90%88Git%E6%A0%B8%E5%BF%83%E5%86%85%E5%AE%B9%E5%85%A8%E5%A5%97%E6%95%99%E7%A8%8B/AJAX%E5%8A%A0%E5%BC%BA%E8%B5%84%E6%96%99/code/12.上传文件.html)

#### 4.4.1. 定义UI结构

```HTML
    <!-- 1. 文件选择框 -->
    <input type="file" id="file1" />
    <!-- 2. 上传按钮 -->
    <button id="btnUpload">上传文件</button>
    <br />
    <!-- 3. 显示上传到服务器上的图片 -->
    <img src="" alt="" id="img" width="800" />

```

#### 4.4.2 验证是否选择了文件

```JS
//JavaScript

 // 1. 获取上传文件的按钮
 var btnUpload = document.querySelector('#btnUpload')
 // 2. 为按钮添加 click 事件监听
 btnUpload.addEventListener('click', function() {
     // 3. 获取到选择的文件列表
     var files = document.querySelector('#file1').files
     if (files.length <= 0) {
         return alert('请选择要上传的文件！')
     }
     // ...后续业务逻辑
 })

```

#### 4.4.3. 向FormData中追加文件

```JavaScript

// 1. 创建 FormData 对象
 var fd = new FormData()
 // 2. 向 FormData 中追加文件
 fd.append('avatar', files[0])

```

#### 4.4.4 使用 xhr 发起上传文件的请求

```JS
//JavaScript
 // 1. 创建 xhr 对象
 var xhr = new XMLHttpRequest()
 // 2. 调用 open 函数，指定请求类型与URL地址。其中，请求类型必须为 POST
 xhr.open('POST', 'http://www.liulongbin.top:3006/api/upload/avatar')
 // 3. 发起请求
 xhr.send(fd)
```

#### 4.4.5 监听onreadystatechange事件

```JS
//JavaScript
   
xhr.onreadystatechange = function() {
  if (xhr.readyState === 4 && xhr.status === 200) {
    var data = JSON.parse(xhr.responseText)
    if (data.status === 200) { // 上传文件成功
      // 将服务器返回的图片地址，设置为 <img> 标签的 src 属性
      document.querySelector('#img').src = 'http://www.liulongbin.top:3006' + data.url
    } else { // 上传文件失败
      console.log(data.message)
    }
  }
}
```

### 4.5 显示文件上传进度

新版本的 XMLHttpRequest 对象中，可以通过监听 xhr.upload.onprogress 事件，来获取到文件的上传进度。语法格式如下：

```JS
//JavaScript
 // 创建 XHR 对象
 var xhr = new XMLHttpRequest()
 // 监听 xhr.upload 的 onprogress 事件
 xhr.upload.onprogress = function(e) {
    // e.lengthComputable 是一个布尔值，表示当前上传的资源是否具有可计算的长度
    if (e.lengthComputable) {
        // e.loaded 已传输的字节
        // e.total  需传输的总字节
        var percentComplete = Math.ceil((e.loaded / e.total) * 100)
    }
 }

```

源码：[13.计算文件的上传进度.html](https://gitee.com/AuroraManito/note/tree/master/sgg/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98AJAX%E9%9B%B6%E5%9F%BA%E7%A1%80%E5%88%B0%E7%B2%BE%E9%80%9A_%E6%95%B4%E5%90%88Git%E6%A0%B8%E5%BF%83%E5%86%85%E5%AE%B9%E5%85%A8%E5%A5%97%E6%95%99%E7%A8%8B/AJAX%E5%8A%A0%E5%BC%BA%E8%B5%84%E6%96%99/code/13.计算文件的上传进度.html)

#### 4.5.1 导入需要的库

```HTML
<!-- HTML -->
   
    <link rel="stylesheet" href="./lib/bootstrap.css" />
    <script src="./lib/jquery.js"></script>

```

#### 4.5.2 基于Bootstrap渲染进度条

```HTML
<!-- HTML -->
 <!-- 进度条 -->
    <div class="progress" style="width: 500px; margin: 10px 0;">
      <div class="progress-bar progress-bar-info progress-bar-striped active" id="percent" style="width: 0%">
        0%
      </div>
    </div>

```

#### 4.5.3  监听上传进度的事件

```JS
//JavaScript
 xhr.upload.onprogress = function(e) {
    if (e.lengthComputable) {
    // 1. 计算出当前上传进度的百分比
    var percentComplete = Math.ceil((e.loaded / e.total) * 100)
    $('#percent')
        // 2. 设置进度条的宽度
        .attr('style', 'width:' + percentComplete + '%')
        // 3. 显示当前的上传进度百分比
        .html(percentComplete + '%')
    }
 }

```

#### 4.5.4 监听上传完成的事件

```JS
//JavaScript
   
 xhr.upload.onload = function() {
     $('#percent')
         // 移除上传中的类样式
         .removeClass()
         // 添加上传完成的类样式
         .addClass('progress-bar progress-bar-success')
 }
```

## 5. jQuery高级用法

### 5.1 jQuery实现文件上传

源码：[14.使用jQuery实现文件上传.html](https://gitee.com/AuroraManito/note/tree/master/sgg/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98AJAX%E9%9B%B6%E5%9F%BA%E7%A1%80%E5%88%B0%E7%B2%BE%E9%80%9A_%E6%95%B4%E5%90%88Git%E6%A0%B8%E5%BF%83%E5%86%85%E5%AE%B9%E5%85%A8%E5%A5%97%E6%95%99%E7%A8%8B/AJAX%E5%8A%A0%E5%BC%BA%E8%B5%84%E6%96%99/code/14.使用jQuery实现文件上传.html)

#### 5.1.1. 定义UI结构

```JavaScript
   
    <!-- 导入 jQuery -->
    <script src="./lib/jquery.js"></script>

    <!-- 文件选择框 -->
    <input type="file" id="file1" />
    <!-- 上传文件按钮 -->
    <button id="btnUpload">上传</button>
```

#### 5.1.2 验证是否选择了文件

```JavaScript
 $('#btnUpload').on('click', function() {
     // 1. 将 jQuery 对象转化为 DOM 对象，并获取选中的文件列表
     var files = $('#file1')[0].files
     // 2. 判断是否选择了文件
     if (files.length <= 0) {
         return alert('请选择图片后再上传！‘)
     }
 })

```

#### 5.1.3 向FormData中追加文件

```JavaScript
 // 向 FormData 中追加文件
 var fd = new FormData()
 fd.append('avatar', files[0])

```

#### 5.1.4 使用jQuery发起上传文件的请求

```JavaScript
 $.ajax({
     method: 'POST',
     url: 'http://www.liulongbin.top:3006/api/upload/avatar',
     data: fd,
     // 不修改 Content-Type 属性，使用 FormData 默认的 Content-Type 值
     contentType: false,
     // 不对 FormData 中的数据进行 url 编码，而是将 FormData 数据原样发送到服务器
     processData: false,
     success: function(res) {
         console.log(res)
     }
 })
```

### 5.2 jQuery实现loading效果

#### 5.2.1 ajaxStart(callback)

Ajax 请求开始时，执行 ajaxStart 函数。可以在 ajaxStart 的 callback 中显示 loading 效果，示例代码如下

```javascript
 // 自 jQuery 版本 1.8 起，该方法只能被附加到文档
 $(document).ajaxStart(function() {
     $('#loading').show()
 })
```

注意： $(document).ajaxStart() 函数会监听当前文档内所有的 Ajax 请求

#### 5.2.2 2. ajaxStop(callback)

Ajax 请求结束时，执行 ajaxStop 函数。可以在 ajaxStop 的 callback 中隐藏 loading 效果，示例代码如下：

```JavaScript
 // 自 jQuery 版本 1.8 起，该方法只能被附加到文档
 $(document).ajaxStop(function() {
     $('#loading').hide()
 })
```

## 6. axios

### 6.1 什么是axios

Axios 是专注于网络数据请求的库。
相比于原生的 XMLHttpRequest 对象，axios 简单易用。
相比于 jQuery，axios 更加轻量化，只专注于网络数据请求
源码：[15.axios的基本使用.html](https://gitee.com/AuroraManito/note/tree/master/sgg/%E9%BB%91%E9%A9%AC%E7%A8%8B%E5%BA%8F%E5%91%98AJAX%E9%9B%B6%E5%9F%BA%E7%A1%80%E5%88%B0%E7%B2%BE%E9%80%9A_%E6%95%B4%E5%90%88Git%E6%A0%B8%E5%BF%83%E5%86%85%E5%AE%B9%E5%85%A8%E5%A5%97%E6%95%99%E7%A8%8B/AJAX%E5%8A%A0%E5%BC%BA%E8%B5%84%E6%96%99/code/15.axios的基本使用.html)

### 6.2 axios发起GET请求

axios 发起 get 请求的语法：

`axios.get('url', { params: { /*参数*/ } }).then(callback)`

具体的请求示例如下：

```JavaScript
 // 请求的 URL 地址
 var url = 'http://www.liulongbin.top:3006/api/get'
 // 请求的参数对象
 var paramsObj = { name: 'zs', age: 20 }
 // 调用 axios.get() 发起 GET 请求
 axios.get(url, { params: paramsObj }).then(function(res) {
     // res.data 是服务器返回的数据
     var result = res.data
     console.log(res)
 })
```

### 6.3 axios发起POST请求

axios 发起 post 请求的语法：

`axios.post('url', { /*参数*/ }).then(callback)`

具体的请求示例如下：

```JavaScript
 // 请求的 URL 地址
 var url = 'http://www.liulongbin.top:3006/api/post'
 // 要提交到服务器的数据
 var dataObj = { location: '北京', address: '顺义' }
 // 调用 axios.post() 发起 POST 请求
 axios.post(url, dataObj).then(function(res) {
     // res.data 是服务器返回的数据
     var result = res.data
     console.log(result)
 })
```

### 6.4 直接使用axios发起请求

axios 也提供了类似于 jQuery 中 $.ajax() 的函数，语法如下：

```JavaScript
 axios({
     method: '请求类型',
     url: '请求的URL地址',
     data: { /* POST数据 */ },
     params: { /* GET参数 */ }
 }) .then(callback)
```

#### 6.4.1 直接使用axios发起GET请求

```JavaScript
 axios({
     method: 'GET',
     url: 'http://www.liulongbin.top:3006/api/get',
     params: { // GET 参数要通过 params 属性提供
         name: 'zs',
         age: 20
     }
 }).then(function(res) {
     console.log(res.data)
 })
```

#### 6.4.2 直接使用axios发起POST请求

```JavaScript
 axios({
     method: 'POST',
     url: 'http://www.liulongbin.top:3006/api/post',
     data: { // POST 数据要通过 data 属性提供
         bookname: '程序员的自我修养',
         price: 666
     }
 }).then(function(res) {
     console.log(res.data)
 })
```
