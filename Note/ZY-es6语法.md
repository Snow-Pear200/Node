# 展开运算符

```javascript
合并数组：
let arr1 = [1,2,3]
let arr2 = [...arr1,7,9];//[1,2,3,7,9]

合并对象：
 let obj1={
        name:"jack"
    }
 let obj2={
        age:18
    }
 let obj3={...obj1,...obj2};
	console.log(obj3)

声明变量：
let [b,...a]=[1,2,3]
console.log(a) // [2,3]

展开对象
  var obj1 = {
  	age:34
  }
  var obj2 = {
  	...obj1,
  	num:15
  }
  运算结果：
  {
  	age:34,
  	num:15
  }
```

# 解构赋值

## 数组解构

```javascript
let [a,b]=[4,5];
等价于：
	let a=4;
	let b=5;

默认值：
let [ a , b = 3 ] = [ 2 ] ;
	a//2
	b//3
```

## 对象解构

```javascript
let {foo,bar} = {
	foo : "aaa",
	bar : "bbb"
}
	等价于：
let foo="aaa";
let bar="bbb";
默认值
let {a = {}, b = 1} = {a: undefined, b: 10}
console.log(a, b) // {} 10

函数默认值
function ok(a=88){
            console.log(a);
        }
     ok(100)//100
```

嵌套解构

```javascript
let { stu:{name,age} }={
              stu:{
                  name:"jack",
                  age:18
              }
        }
  console.log(name,age);//jack 18
```

# dos命令

**常用dos命令**

1，【dir】，列出当前目录下的所有文件/文件夹

2，【cd ..】，返回上级目录

3，【cd 目录名】，进入下一级目录

4，【磁盘名:】，进入指定磁盘根目录

例如：c: 	d:

5，【cls】清屏

6，【md 文件夹名】新建文件夹  新建文件：【cd  > 文件名】

7，【ipconfig】查看IP地址

# git命令

进入到磁盘  cd  c:

创建文件夹 mkdir 文件夹名字

创建文件 touch  文件名字

清屏  clear

# es6新增数组处理方法

## **from** 

### 一个参数的情况

将具有length属性的，类似数组的对象，转换为数组。

```javascript
let arrayLike = {
   "0": "a",
   "1": "b",
   "3": "c",
   length: 5
};
var let = Array.from(arrayLike );//[ a , b , undefined , c , undefined ]
//把类似数组的对象转成数组
```

### 两个参数的情况

//Array.from还可以接受第二个参数，作用类似于数组的map方法

```javascript
var map = Array.from(arrayLike, x => x + x);
 Array.from(obj,(x,i)=>console.log(x,i)) // 两个参数 每一项和索引
```

## find() 和 findIndex()

find，找到符合条件的成员 , 找到一个之后不再找了

```javascript
var item = [1, 4, -5, 10].find(x=>{
	return x>9;
});	//10
```

findIndex() 找下标，找到一个之后不再找了

```javascript
var item = [1, 4, -5, 10，100].findIndex(x=>{
	return x>9;
});	//3 
```

# 占位

```javascript
 var  arry=[1,4,12,,50];
  console.log(arry.length); // 5
```

# 数组去重

```javascript
 let arr = [1, 2, 3, 4, 5, 1, 2, 6]
        let res = new Set(arr)
         console.log(res)//{1,2,3,4,5,6}
  console.log([...res]);)//[1, 2, 3, 4, 5, 6]
  
  console.log(Array.from(res));//[1, 2, 3, 4, 5, 6]
```



# 模块化开发

浏览器不识别es6模块化，需要给script标签添加  type=module

## 在ji入口文件：index.js引入 js文件

js文件抛出的两种方法

```javascript
1,export
    let b = '这是b.js'
	 export { b }
2,let b = '这是b.js'
	function bFun() {
	    console.log('这是bfun');
	}
	export default {
	    b,
	    bFun
	}      
```

文件接受的两种方法

```javascript
1,import { a } from './a.js'
	console.log(a);

2,import abc from './b.js' //抛出用的default
	console.log(abc.b);
	console.log(abc.bFun);
```



















