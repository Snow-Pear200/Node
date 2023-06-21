1jQuery

##  **安装** 

在⻚⾯引⼊即可 

```javascript
<script src="js/jquery-3.4.1.js" type="text/javascript" ></script>
```

# 2.2. Jquery**核⼼** 

 $ 符号在 jQuery 中代表对 jQuery 对象的引⽤， "jQuery"是核⼼对象。通过该对象可以获取jQuery对 象，调⽤jQuery提供的⽅法等。只有jQuery对象才能调⽤jQuery提供的⽅法。

```javascript
$ <==> jQuery
```

## 2.3. Dom**对象 与** Jquery**包装集对象** 

​	明确 Dom 对象和 jQuery 包装集的概念， 将极⼤的加快我们的学习速度。原始的 Dom 对象只有 DOM 接⼝提供的⽅法和属性，通过js代码获取的对象都是 Dom 对象；⽽通过 jQuery 获取的对象是 jQuery 包 装集对象，简称jQuery对象，只有jQuery对象才能使⽤jQuery提供的⽅法

## 2.3.1. Dom**对象**

javascript 中获取 Dom 对象，Dom 对象只有有限的属性和⽅法：

```javascript
var div = document.getElementById("testDiv");
var divs = document.getElementsByTagName("div");
```

## 2.3.2. Jquery**包装集对象**

​	可以说是 Dom 对象的扩充。在 jQuery 的世界中将所有的对象， ⽆论是⼀个还是⼀组，都封装成⼀个 jQuery 包装集，⽐如获取包含⼀个元素的 jQuery 包装集：

```javascript
var jQueryObject = $("#testDiv");
```

## 2.3.3. Dom**对象 转** Jquery**对象**

Dom 对象转为 jQuery 对象，只需要利⽤ $() ⽅法进⾏包装即可

```javascript
var domDiv = document.getElementById('mydiv'); // 获取Dom对象
	mydiv = $(domDiv);
```

## 2.3.4. Jquery**对象 转** Dom**对象**

​	jQuery 对象转 Dom 对象，只需要取数组中的元素即可

```javascript
// 第⼀种⽅式 获取jQuery对象
var jqueryDiv = jQuery('#mydiv');
// 第⼆种⽅式 获取jQuery对象
jqueryDiv = $('#mydiv');
var dom = jqueryDiv[0]; // 将以获取的jquery对象转为dom
```

​	通过遍历 jQuery 对象数组得到的对象是 Dom 对象，可以通过 $() 转为 jQuery 对象

```javascript
$('#mydiv').each(function() {//遍历
 	var jquery = $(this); 
});
```

案例：

```javascript
<div id="mydiv">write less, do more</div>
<script type="text/javascript">
 	console.log("-------------获取dom对象------------------")
 	// dom对象
 	var domDiv = document.getElementById("mydiv");
 	console.log(domDiv);
 	
 	console.log("-------------获取jquery对象------------------")
 	// 获取jquery对象
 	// 第⼀种⽅式
 	var jqueryDiv = jQuery('#mydiv');
 	console.log(jqueryDiv);
 	// 第⼆种⽅式
 	jqueryDiv = $('#mydiv');
 	console.log(jqueryDiv);
 	
 	console.log("-------------dom转jquery------------------")
 	// dom转jquery包装集/对象
 	var obj = $(domDiv);
 	console.log(obj);
 	
 	console.log("-------------jquery转dom------------------")
 	// jquery对象转dom对象
 	var dom = $('#mydiv')[0]; // 获取jquery对象转为dom
 	// 或
 	var dom2 = jqueryDiv[0]; // 将jquery对象转为dom
 	console.log(dom);
 	console.log(dom2);
 
 	/* this代表了dom对象，不是jquery对象 */
 	console.log("-------------dom转jquery------------------")
 	$('#mydiv').each(function() {
 		// 通过id选择器选择了id为mydiv的所有元素然后进⾏遍历
 		// 那么遍历出的每个元素就是id为mydiv的标签元素
 		// ⽽this就代表了当前的这个元素
 	var jquery = $(this);
 	});
 	
 	console.log("-------------jquery转dom------------------")
 		$('#mydiv').each(function() {
 		var dom3 = this; 
 	});
</script>
```

# Jquery**选择器**

​		和使⽤ JS 操作Dom⼀样，获取⽂档中的节点对象是很频繁的⼀个操作，在jQuery中提供了简便的⽅式 供我们查找|定位元素，称为jQuery选择器，选择器可以说是最考验⼀个⼈ jQuery 功⼒的地⽅，通俗的 讲, Selector 选择器就是"⼀个表示特殊语意的字符串"。 只要把选择器字符串传⼊上⾯的⽅法中就能够选 择不同的 Dom 对象并且以 jQuery 包装集的形式返回。 

​		jQuery 选择器按照功能主要分为"选择"和"过滤"。 并且是配合使⽤的，具体分类如下。基础选择器掌握即可 ,其他⽤到再查阅。

## 3.1. **基础选择器**

| **选择器**      | 名称                          | 举例                                         |
| --------------- | ----------------------------- | -------------------------------------------- |
| id选择器        | \#id                          | $("#testDiv")选择id为testDiv的元素           |
| 元素名称选择 器 | element                       | $("div")选择所有div元素                      |
| 类选择器        | .class                        | $(".blue")选择所有class=blue的元素           |
| 选择所有元素    | *                             | $("*")选择⻚⾯所有元素                       |
| 组合选择器      | selector1,selector2,selectorN | $("#testDiv,span,.blue")同时选中多个选择器匹 |

```javascript
<body>
    <div id="mydiv1" class="blue">元素选择器</div>
    <div id="mydiv1">id选择器1 <span>span中的内容</span> </div>
    <span class="blue">样式选择器</span>

    <script src="./js/jquery-3.6.4.js"></script>
    <script>
        //1.id选择器   $('#id属性值')  选择id为指定值的元素对象 (如果有多个同名id 只取第一个)
        let mydiv = $('#mydiv1')
        console.log(mydiv);

        //2.类选择器   $('.属性值')   选择所有class为指定值的元素对象 
        let clas = $('.blue')
        console.log(clas);

        //3.元素选择器  $('标签名/元素名')   选择所有为指定标签的元素对象
        let spans = $('span')
        console.log(spans);

        //4.通用选择器  $('*')    选择所有的元素对象
        let all = $('*')
        console.log(all);

        //5.组合选择器  $('选择器1,选择器2,...')  选择指定选择器的元素对象 
        let group = $('#mydiv,div,.blue')
        console.log(group); //3个 重复的不会再次选取

    </script>
</body>
```

## 3.2. **层次选择器**

| **选择器** | **名称**            | **举例**                                          |
| ---------- | ------------------- | ------------------------------------------------- |
| 后代选择器 | ancestor descendant | $("#parent div")选择id为parent的元素的所有div元素 |
| ⼦代选择器 | parent > child      | $("#parent>div")选择id为parent的直接div⼦元素     |
| 相邻选择器 | prev + next         | $(".blue + img")选择css类为blue的下⼀个img元素    |
| 同辈选择器 | prev ~ sibling      | $(".blue ~ img")选择css类为blue的之后的img元素    |

```html
	<style>
        .testColor {
            background: green;
        }

        .gray {
            background: gray;
        }
    </style>
</head>

<body>
    <div id="parent">层次择器
        <div id="child" class="testColor">⽗选择器
            <div class="gray">⼦选择器</div>
            <img src="http://www.baidu.com/img/bd_logo1.png" width="270" height="129" />
            <img src="http://www.baidu.com/img/bd_logo1.png" width="270" height="129" />
        </div>
        <p>p元素</p>
        <div>
            选择器2<div>选择器2中的div</div>
        </div>
    </div>

    <script src="./js/jquery-3.6.4.js"></script>
    <script>
        //1.后代选择器 父元素 指定元素  $('父元素 指定元素') 包含第一代第二代第三代...所有元素
        let hd = $('#parent div')
        console.log(hd);

        //2.子代选择器 父元素>指定元素  $('父元素>指定元素') 父元素第一代的所有元素
        let zd = $('#parent>div')
        console.log(zd);

        //3.相邻选择器 元素+指定元素    $('元素+指定元素') 选择元素的下一个指定元素 只会查找下一个元素 如果元素不存在则获取不到 ( 只会找直接挨着的)
        let xl = $('#child + div')
        console.log(xl);  //只会找直接挨着的

        //4.同辈选择器 元素~指定元素    $('元素~指定元素') 选择元素的下面所有指定元素
        let imgs = $('.gray~img')
        console.log(imgs);

    </script>
</body>
```

## 3.3. **表单选择器**

| Form           | 名称      | 举例                                                         |
| -------------- | --------- | ------------------------------------------------------------ |
| 表单选择器     | :input    | 查找所有的input元素：$(":input")；注意：会匹配所有的input、textarea、select和button元素。 |
| ⽂本框选择器   | :text     | 查找所有⽂本框：$(":text")                                   |
| 密码框选择器   | :password | 查找所有密码框：$(":password")                               |
| 单选按钮选择器 | :radio    | 查找所有单选按钮：$(":radio")                                |
| 复选框选择器   | :checkbox | 查找所有复选框：$(":checkbox")                               |
| 提交按钮选择器 | :submit   | 查找所有提交按钮：$(":submit")                               |
| 图像域选择器   | :image    | 查找所有图像域：$(":image")                                  |
| 重置按钮选择器 | :reset    | 查找所有重置按钮：$(":reset")                                |
| 按钮选择器     | :button   | 查找所有按钮：$(":button")                                   |
| ⽂件域选择器   | :file     | 查找所有⽂件域：$(":file")                                   |

```javascript
<body>
    <form id='myform' name="myform" method="post">
        <input type="hidden" name="uno" value="9999" disabled="disabled" />
        姓名:<input type="text" id="uname" name="uname" /><br />
        密码:<input type="password" id="upwd" name="upwd" value="123456" /><br />
        年龄:<input type="radio" name="uage" value="0" checked="checked" />⼩屁孩
        <input type="radio" name="uage" value="1" />你懂得 <br />
        爱好:<input type="checkbox" name="ufav" value="篮球" />篮球
        <input type="checkbox" name="ufav" value="爬床" />爬床
        <input type="checkbox" name="ufav" value="代码" />代码<br />
        来⾃:<select id="ufrom" name="ufrom">
            <option value="-1" selected="selected">请选择</option>
            <option value="0">北京</option>
            <option value="1">上海</option>
        </select><br />
        简介:<textarea rows="10" cols="30" name="uintro"></textarea><br />
        头像:<input type="file" /><br />
        <input type="image" src="http://www.baidu.com/img/bd_logo1.png" width="20" height="20" />
        <button type="submit" onclick="return checkForm();">提交</button>
        <button type="reset">重置</button>

    </form>
    <script src="./js/jquery-3.6.4.js"></script>
    <script>
        //1.表单选择器 :input 查找所有的input元素：$(":input")；注意：会匹配所有的input、textarea、select和button元素。
        let inputs = $(':input')
        console.log(inputs); // 14个
        //元素选择器
        let inputs2 = $('input') // 10个 input、textarea、select和button元素不算
        console.log(inputs2);

        //2.文本框选择器
        let text = $(':text')
        console.log(text);
        // 表单选择器           :input        查找所有的input元素：        $(":input")； 注意：会匹配所有的input、textarea、select和button元素。
        // ⽂本框选择器         :text         查找所有⽂本框：$(":text")
        // 密码框选择器         :password     查找所有密码框：$(":password")
        // 单选按钮选择器       :radio        查找所有单选按钮：$(":radio")
        // 复选框选择器         :checkbox     查找所有复选框：$(":checkbox")
        // 提交按钮选择器       :submit       查找所有提交按钮：$(":submit")
        // 图像域选择器         :image        查找所有图像域：$(":image")
        // 重置按钮选择器       :reset        查找所有重置按钮：$(":reset")
        // 按钮选择器           :button       查找所有按钮：$(":button")
        // ⽂件域选择器         :file         查找所有⽂件域：$(":file")
    </script>
</body>
```

# Jquery Dom**操作**

​	jQuery也提供了对HTML节点的操作，⽽且在原⽣js的基础之上进⾏了优化，使⽤起来更加⽅便。 

​	常⽤的从⼏个⽅⾯来操作，查找元素（选择器已经实现）；创建节点对象；访问和设置节点对象的 

值，以及属性；添加节点；删除节点；删除、添加、修改、设定节点的CSS样式等。注意：以下的操作 

⽅式只适⽤于jQuery对象。

## 4.1. **操作元素的属性**

### 4.1.1. **获取属性**

| 方法                   | 说明                                                         | 举例                                         |
| ---------------------- | ------------------------------------------------------------ | -------------------------------------------- |
| attr(属性名称，属性值) | 设置指定的属性值，操作 checkbox 时，选中返回 checked，没有选中返回 undefined。 | attr('checked',’checked’)，attr('name',’zs’) |
| prop(属性名称，属性值) | 设置具有true和false的属性值                                  | prop('checked',’true’)                       |

	1. 固有属性 attr和prop均可操作 
 	2. prop不能操作自定义属性，attr可操作自定义属性
 	3. 固有属性：元素本身就有的属性 (id,name,class...) 
 	4. 返回值是boolean的属性 (checked, selected,disabled)
 	5. 自定义属性
 	6. 总结如果属性的类型是布尔(checked, selected,disabled) 则使用prop方法 否则使用attr方法

```javascript
<script src="./js/jquery-3.6.4.js"></script>
    <script>
        //属性的分类   固有属性: 元素本身就有的属性 (id,name,class...) 
        //             返回值是boolean的属性 (checked, selected,disabled)
        //             自定义属性

        //区别:
        //1. 如果是固有属性 attr(),prop()均可获取,
        //2. 如果是自定义属性 attr可获取prop不可获取
        //3. 如果是布尔值属性 若设置了属性 attr()返回具体的值,prop返回true
        //4. 如果是布尔值属性 若未设置属性 attr()返回undefined, prop返回false

        //1.获取属性
        // 1.1 attr(属性名,属性值)
        //固有属性
        let name = $('#aa').attr('name')
        console.log(name);
        // 1.2 prop(属性名,属性值)
        let name2 = $('#aa').prop('name')
        console.log(name2);

        //返回值是布尔类型 (元素设置了属性)
        let cke = $('#aa').attr('checked')
        console.log(cke);  //checked
        let cke2 = $('#aa').prop('checked')
        console.log(cke2); //true

        //返回值是布尔类型 (元素没有设置属性)
        let cke3 = $('#bb').attr('checked')
        console.log(cke3);  // undefined
        let cke4 = $('#bb').prop('checked')
        console.log(cke4); // false

        //自定义属性
        let abc1 = $('#aa').attr('abc')
        console.log(abc1); // aabbcc
        let abc2 = $('#aa').prop('abc')
        console.log(abc2); // undefined

		//2.设置属性
        //2.1 attr('属性名','属性值')  prop('属性名'，属性值)
        // 2.1.1固有属性
        $('#aa').attr('value', '1')
        $('#bb').prop('value', '2')

        //2.1.2返回值是布尔类型 
        // $('#bb').attr('checked','checked')
        $('#bb').prop('checked', false)
        $('#bb').prop('checked', 'checked')

        //2.2 自定义属性
        $('#aa').attr('uname', 'admin')
        $('#aa').prop('uage', '16')


        //3.移除属性  removeAttr  
        $('#aa').removeAttr('checked')

        //总结如果属性的类型是布尔(checked, selected,disabled) 则使用prop方法 否则使用attr方法
 </script>
```

### 4.2. **操作元素的样式**

​		对于元素的样式，也是⼀种属性，由于样式⽤得特别多，所以对于样式除了当做属性处理外还可以有 

专⻔的⽅法进⾏处理。

| 方法                   | 说明                          |
| ---------------------- | ----------------------------- |
| attr("class")          | 获取class属性的值，即样式名称 |
| attr("class","样式名") | 修改class属性的值，修改样式   |
| addClass("样式名")     | 添加样式名称                  |
| css()                  | 添加具体的样式                |
| removeClass(class)     | 移除样式名称                  |

增加元素的具体样式，格式：

1. attr("class")          获取元素样式名
2. attr("class","样式名") 设置元素的样式 原来的样式会被覆盖
3. addClass("样式名")     添加样式名称  出现相同样式以css中后定义的为准
4. css()    添加具体的样式 相当于添加(行内样式)  设置单个css('具体样式名'，'样式值')，	多个样式css({'具体样式名'：'样式值'，'具体样式名'：'样式值'，...})
5. removeClass(class)     移除样式名称

```javascript
<style type="text/css">
        div {
            padding: 8px;
            width: 180px;
        }

        .blue {
            background: blue;
        }

        .larger {
            font-size: 30px;
        }

        .pink {
            background-color: pink;
        }

        .green {
            background: green;
        }
    </style>
</head>

<body>
    <h3>css()⽅法设置元素样式</h3>
    <div id="conBlue" class="blue larger">天蓝⾊</div>
    <div id="conRed">⼤红⾊</div>
    <div id="remove" class="blue larger">天蓝⾊</div>
    <script src="./js/jquery-3.6.4.js"></script>
    <script>
        //操作元素的样式
        // 1.attr("class")          获取元素样式名
        let cal = $('#conBlue').attr('class')
        console.log(cal); // blue larger

        // 2.attr("class","样式名") 设置元素的样式 原来的样式会被覆盖
        $('#conBlue').attr('class', 'green')

        // 3.addClass("样式名")     添加样式名称  出现相同样式以css中后定义的为准
        $('#conBlue').addClass('larger')
        $('#conBlue').addClass('pink')

        // 4.css()    添加具体的样式 相当于添加(行内样式)  设置单个css('具体样式名'，'样式值')，多个样式css({'具体样式名'：'样式值'，'具体样式名'：'样式值'，...})
        $('#conRed').css('font-size', '50px')
        $('#conRed').css({ 'font-size': '40px', 'color': 'yellow' })

        // 5.removeClass(class)     移除样式名称
        $('#remove').removeClass('larger')
    </script>
</body>
```

### 4.3. **操作元素的内容**

对于元素还可以操作其中的内容，例如⽂本，值，甚⾄是html。

| 方法               | 说明                           |
| ------------------ | ------------------------------ |
| html()             | 获取元素的html内容             |
| html("html, 内容") | 设定元素的html内容             |
| text()             | 获取元素的⽂本内容，不包含html |
| text("text 内容")  | 设置元素的⽂本内容，不包含html |
| val()              | 获取元素value值                |
| val("值")          | 设定元素的value值              |

1. 表单元素：文本框，密码框，radio ，checkbox，隐藏域hidden，文本域textarea，下拉框select
2. 非表单元素：div span h1~h6 table等

* 1.html() 获取元素内容 包含html标签 (非表单元素)
* 2.html("html内容") 设置元素的内容 包含html标签 (非表单元素)
*  3.text() 获取元素内容(纯文本内容，不识别标签) (非表单元素)
* 4.text("text 内容") 设置元素内容(纯文本内容，不识别标签) (非表单元素)
* 5.val() 获取元素的值 (表单元素)
* 6.val("值") 设置元素的值 (表单元素)

```javascript
<body>
    <h3><span>html()和text()⽅法设置元素内容</span></h3>
    <div id="html"></div>
    <div id="html2"></div>
    <div id="text"></div>
    <div id="text2"></div>
    <input type="text" name="uname" id="op" value="oop" />
    <script src="./js/jquery-3.6.4.js"></script>
    <script>
        //表单元素：文本框，密码框，radio ，checkbox，隐藏域hidden，文本域textarea，下拉框select
        // 非表单元素：div span h1~h6 table等

        // 1.html() 获取元素内容 包含html标签 (非表单元素)
        console.log($('h3').html());//<span>html()和text()⽅法设置元素内容</span>

        // 2.html("html内容") 设置元素的内容 包含html标签 (非表单元素)
        $('#html').html(`<h2>上海</h2>`)
        $('#html2').html('上海')
        let html = $('#html').html()
        let html2 = $('#html2').html()
        console.log(html); //<h2>上海</h2>
        console.log(html2); //上海

        // 3.text() 获取元素内容(纯文本内容，不识别标签) (非表单元素)
        console.log($("h3").text()); //html()和text()⽅法设置元素内容

        // 4.text("text 内容") 设置元素内容(纯文本内容，不识别标签) (非表单元素)
        $('#text').text('北京')
        $('#text2').text('<h2>北京</h2>')
        let txt = $('#text').text()
        let txt2 = $('#text2').text()
        console.log(txt); //北京
        console.log(txt2); // <h2>北京</h2>

        // 5.val() 获取元素的值 (表单元素)
        let val = $('#op').val()
        console.log(val); // oop

        // 6.val("值") 设置元素的值 (表单元素)
        $('#op').val('太难起')
    </script>
</body>

```

### 4.4. **创建元素**

在jQuery中创建元素很简单，直接使⽤核⼼函数即可

```javascript
$('元素内容');
```

```javascript
$('<p>this is a paragraph!!!</p>');
```

### 4.5. **添加元素**

| 方法                           | 说明                                                         |
| ------------------------------ | ------------------------------------------------------------ |
| prepend(content)               | 在被选元素内部的开头插⼊元素或内容，被追加的 content 参 数，可以是字符、HTML 元素标记。 |
| $(content).prependTo(selector) | 把 content 元素或内容加⼊ selector 元素开头                  |
| append(content)                | 在被选元素内部的结尾插⼊元素或内容，被追加的 content 参 数，可以是字符、HTML 元素标记。 |
| $(content).appendTo(selector)  | 把 content元素或内容插⼊selector 元素内，默认是在尾部        |
| before()                       | 在元素前插⼊指定的元素或内容:$(selector).before(content)     |
| after()                        | 在元素后插⼊指定的元素或内容:$(selector).after(content)      |

```javascript
<style>
        div {
            margin: 10px 0px;
        }

        span {
            color: white;
            padding: 8px
        }

        .red {
            background-color: red;
        }

        .blue {
            background-color: blue;
        }

        .green {
            background-color: green;
        }

        .pink {
            background-color: pink;
        }

        .gray {
            background-color: gray;
        }
    </style>
</head>

<body>
    <h3>prepend()⽅法前追加内容</h3>
    <h3>prependTo()⽅法前追加内容</h3>
    <h3>append()⽅法后追加内容</h3>
    <h3>appendTo()⽅法后追加内容</h3>
    <span class="red">男神</span>
    <span class="blue">偶像</span>
    <div class="green">
        <span>⼩鲜⾁</span>
    </div>
    <script src="./js/jquery-3.6.4.js"></script>
    <script>
        // 1.创建元素
        // let p = '<p>这是p元素</p>'
        // console.log(p);
        // console.log($('p'));

        let span = "<span>小奶狗</span>"
        let span2 = "<span>小狼狗</span>"
        let span3 = "<span>小猫</span>"
        let span4 = "<span>小兔子</span>"


        // 2.添加元素
        //2.1 前追加子元素
        // 指定元素.prepend(内容)     在指定元素内部的最前面追加内容，内容可以字符串，html元素，或者jQuery对象
        // $('内容').prependTo(指定元素)    把内容追加到元素内部的最前面，内容可以字符串，html元素，或者jQuery对象
        $(".green").prepend(span)
        $(span2).prependTo('.green')

        //2.2 后追加子元素
        // 指定元素.append(内容)     在指定元素内部的最后面追加内容，内容可以字符串，html元素，或者jQuery对象
        // $('内容').appendTo(指定元素)    把内容追加到元素内部的最后面，内容可以字符串，html元素，或者jQuery对象
        $('.green').append(span3)
        $(span4).appendTo('.green')

        //注：已有的元素追加到指定元素中   会将原来元素直接剪切设置到指定位置 
        $('.green').append($('.red'))


        //2.3 前追加同级元素
        // before() 在指定元素的前面追加内容
        let sp1 = '<span class="pink">女神</span>'
        $('.blue').before(sp1)

        //2.4 后追加同级元素
        // after() 在指定元素的后面追加内容
        let sp2 = '<span class="gray">歌手</span>'
        $('.blue').after(sp2)

    </script>
</body>
```

注：已有的元素追加到指定元素中   会将原来元素直接剪切设置到指定位置

### 4.6. **删除元素**

| 方法     | 说明                                                   |
| -------- | ------------------------------------------------------ |
| remove() | 删除所选元素或指定的⼦元素，包括整个标签和内容⼀起删。 |
| empty()  | 清空所选元素的内容                                     |

```javascript
style>
        span {
            color: white;
            padding: 8px;
            margin: 5px;
            float: left;
        }

        .green {
            background-color: green;
        }

        .blue {
            background-color: blue;
        }
    </style>
</head>

<body>
    <h3>删除元素</h3>
    <span class="green">jquery<a>删除</a></span>
    <span class="blue">javase</span>
    <span class="green">http协议</span>
    <span class="blue">servlet</span>

    <script src="./js/jquery-3.6.4.js"></script>
    <script>
        // 1.remove 删除所选元素或指定的⼦元素，包括整个标签和内容⼀起删。
        // 指定元素.remove()
        $('.green').remove()

        // 2.清空元素内容 保存标签
        // 指定元素.empty()
        $('.blue').empty()

 </script>
```

### 4.7. **遍历元素**

each() 

$(selector).each(function(index,element)) :遍历元素 

参数 function 为遍历时的回调函数， 

index 为遍历元素的序列号，从 0 开始。 

element是当前的元素，此时是dom元素。

# Jquery**事件**

## 5.1. ready**加载事件**

ready()类似于 onLoad()事件   预加载事件

ready()可以写多个，按顺序执⾏ 

```javascript
$(document).ready(function(){})等价于$(function(){})
```

```javascript
<body>
    <script src="./js/jquery-3.6.4.js"></script>
    <script>
        // ready 加载事件  当页面dom解构加载完毕之后执行 类似于js中的load事件
        // ready 事件可以写多个
        // 语法： $(document).ready(function(){})
        // 简写： $(function(){})

        $(document).ready(function () {
            console.log($('#p1'));
        })

        $(function () {
            console.log($('#p1'));
        })
    </script>
    <p id="p1">文本1</p>
</body>

```

## 5.2. bind()**绑定事件**

为被选元素添加⼀个或多个事件处理程序，并规定事件发⽣时运⾏的函数。

```javascript
语法：
	$(selector).bind( eventType [, eventData], handler(eventObject));
--------------
	eventType ：是⼀个字符串类型的事件类型，就是你所需要绑定的事件。
 这类类型可以包括如下：
 	blur, focus, focusin, focusout, load, resize, scroll, unload, click, 	dblclick, mousedown, mouseup, mousemove, mouseover, mouseout,mouseenter 	，mouseleave,change, select, submit, keydown, keypress, keyup, error

	[, eventData]：传递的参数，格式：{名:值,名2:值2}

	handler(eventObject)：该事件触发执⾏的函数

绑定单个事件
	$("元素").bind("事件类型",function(){
        
    })

直接绑定
	$("元素").事件名(function(){
        
    })

1.确定为哪些元素绑定事件
	获取元素
2.绑定什么事件（事件类型）
	第⼀个参数：事件的类型
3.相应事件触发的，执⾏的操作
	第⼆个参数：函数
```

```javascript
<body>
    <h3>bind()⽅简单的绑定事件</h3>
    <div id="test" style="cursor:pointer">点击查看名⾔</div>
    <input id="btntest" type="button" value="点击就不可⽤了" />
    <hr>
    <button id="btn1">按钮1</button>
    <button id="btn2">按钮2</button>
    <button id="btn3">按钮3</button>
    <button id="btn4">按钮4</button>
    <script src="./js/jquery-3.6.4.js"></script>
    <script>
        //1 bind绑定事件
        // 1.1绑定单个事件
        // $("元素").bind("事件类型", function () { })
        $("#test").bind("click", function () {
            console.log("123456");
        })

        // 1.2直接绑定
        // $("元素").事件名(function () { })
        $("#btntest").click(function () {
            //禁用按钮
            $(this).prop("disabled", "true")
        })

        //2.1 绑定多个事件
        // 2.1.1 bind绑定 同时为多个事件绑定同一个函数
        // 指定元素.bind("事件类型1 事件类型2 事件类型3...",function(){})
        $("#btn1").bind('click mouseout', function () {
            console.log("按钮1...");
        })

        //2.3 为元素绑定多个事件,并设置对应的函数
        // 指定元素.bind("事件类型",function(){ }).bind("事件类型",function(){ })
        $("#btn2").bind("click", function () {
            console.log('按钮2被点击');
        }).bind("mouseout", function () {
            console.log('按钮2离开');
        })

        /* 2.4 为元素绑定多个事件, 并设置对应的函数
        指定元素.bind({
            "事件类型": function () {

            },
            "事件类型": function () {

            },
        }) */
        $("#btn3").bind({
            "click": function () {
                console.log('按钮3被点击');
            },
            "mouseout": function () {
                console.log('按钮3离开');
            }
        })

        //2.5 直接绑定
        // 指定元素.事件名(function(){

        //  }).事件名(function(){

        //  });
        $("#btn4").click(function () {
            console.log('按钮4被点击');
        }).mouseout(function () {
            console.log('按钮4离开');
        })

        // 1.确定为哪些元素绑定事件
        // 获取元素
        // 2.绑定什么事件（事件类型）
        // 第⼀个参数：事件的类型
        // 3.相应事件触发的，执⾏的操作
        // 第⼆个参数：函数

    </script>
</body>
```



#  Jquery Ajax

## 6.1. $.ajax

jquery 调⽤ ajax ⽅法： 

 格式：$.ajax({}); 

 参数： 

​	 type：请求⽅式 GET/POST 

 	url：请求地址 url 

​	 async：是否异步，默认是 true 表示异步 

 	data：发送到服务器的数据 

​	 dataType：预期服务器返回的数据类型 

 	contentType：设置请求头 

​	 success：请求成功时调⽤此函数 

​	 error：请求失败时调⽤此函数

```javascript
<body>
    <button id="btn">查询数据</button>
    <!-- jquery 调⽤ ajax ⽅法：
    格式：$.ajax({});
    参数：
        ​ type：请求⽅式 GET/POST
        url：请求地址 url
        ​ async：是否异步，默认是 true 表示异步
        data：发送到服务器的数据
        ​ dataType：预期服务器返回的数据类型
        contentType：设置请求头
        ​ success：请求成功时调⽤此函数
        ​ error：请求失败时调⽤此函数 -->


    <script src="../js/jquery-3.6.4.js"></script>
    <script>
        // 点击按钮 发送ajax请求 将数据显示到页面中
        $("#btn").click(function () {
            $.ajax({
                type: "get", //请求方式
                url: "./data.txt", //请求地址
                data: { //请求对象,json对象
                    uname: "张三" //如果没有参数则不需要设置
                },
                success: function (data) { //请求成功时调用的函数 data是形参名,代表的是返回的数据
                    console.log((data));
                    //将字符串转成JSON对象
                    let obj = JSON.parse(data)
                    console.log(obj);
                }
            })

            $.ajax({
                type: "get", //请求方式
                url: "./data.txt", //请求地址
                data: { //请求对象,json对象
                    uname: "张三" //如果没有参数则不需要设置
                },
                dataType: "json", //预期返回的类型,如果是json格式,在接收到返回值时会自动封装成json对象
                success: function (data) { //请求成功时调用的函数 data是形参名,代表的是返回的数据
                    console.log((data));
                    //将字符串转成JSON对象
                    // let obj = JSON.parse(data)
                    // console.log(obj);
                    // DOM操作
                    // 创建ul
                    let ul = $("<ul></ul>")
                    //遍历返回数组
                    for (let i = 0; i < data.length; i++) {
                        //得到数组中的每一个元素
                        let user = data[i]
                        //创建一个li元素
                        let li = `<li>${user.userName}</li>`
                        //将li元素设置到ul元素中
                        ul.append(li)
                    }
                    console.log(ul);
                    //将ul设置到body标签中
                    $("body").append(ul)
                }
            })
        })
    </script>
</body>
```

## 6.2. $.get 

这是⼀个简单的 GET 请求功能以取代复杂 $.ajax 。 

请求成功时可调⽤回调函数。如果需要在出错时执⾏函数，请使⽤ $.ajax。

```javascript
// 1.请求json⽂件，忽略返回值
	$.get('js/cuisine_area.json');
```

```javascript
// 2.请求json⽂件，传递参数，忽略返回值
	$.get('js/cuisine_area.json',{name:"tom",age:100});
```

```javascript
// 3.请求json⽂件,拿到返回值,请求成功后可拿到返回值
	$.get('js/cuisine_area.json',function(data){
	 console.log(data);
	});
```

```javascript
// 4.请求json⽂件,传递参数,拿到返回值 
	$.get('js/cuisine_area.json',{name:"tom",age:100},function(data){
	 console.log(data);
	});
```

## 6.3. $.post

这是⼀个简单的 POST 请求功能以取代复杂 $.ajax 。 

请求成功时可调⽤回调函数。如果需要在出错时执⾏函数，请使⽤ $.ajax。

```javascript
// 1.请求json⽂件，忽略返回值
	$.post('../js/cuisine_area.json');
```

```javascript
// 2.请求json⽂件，传递参数，忽略返回值
	$.post('js/cuisine_area.json',{name:"tom",age:100});
```

```javascript
// 3.请求json⽂件,拿到返回值,请求成功后可拿到返回值
	$.post('js/cuisine_area.json',function(data){
	 console.log(data);
	});
```

```javascript
// 4.请求json⽂件,传递参数,拿到返回值 
	$.post('js/cuisine_area.json',{name:"tom",age:100},function(data){
	 console.log(data);
	});;
```

```javascript
<script src="../js/jquery-3.6.4.js"></script>
    <script>
        // $.get()
        // 语法:
        // $.get()("请求地址","请求参数",function(){

        // })

        // $.post() //需要服务器
        // 语法:
        // $.post()("请求地址","请求参数",function(){

        // })

        $.get("./data.json", {}, function (data) {
            console.log(data);
        })

        // $.post("./data.json", {}, function (data) {
        //     console.log(data);
        // })
    </script>
```



## 6.4. $.getJSON

表示请求返回的数据类型是JSON格式的ajax请求

```javascript
$.getJSON('js/cuisine_area.json',{name:"tom",age:100},function(data){
	 console.log(data); // 要求返回的数据格式是JSON格式
	});
```

```javascript
<script src="../js/jquery-3.6.4.js"></script>
    <script>
        // $.getJSON() 
        // 语法:
        // $.getJSON()("请求地址","请求参数",function(){

        // })  
        // 注:getJSON()方式要求返回的数据格式满足json格式(json字符串)

        $.getJSON("./data.json", {}, function (d) {
            console.log(d);
        })

        $.get("./test.txt", {}, function (d) {
            console.log(d);
        })

        //如果返回的数据不是json格式的,则无法获取
        // $.getJSON("./test.txt", {}, function (d) {
        //     console.log(d); // 不能打印
        // })
    </script>
```



















