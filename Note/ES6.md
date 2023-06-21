# **ECMASript 6** **新特性**

## **2.1.let** **关键字** 

let 关键字用来声明变量，使用 let 声明的变量有几个特点： 

1) 不允许重复声明 

2) 块儿级作用域 

3) 不存在变量提升 

4) 不影响作用域链 

**应用场景：以后声明变量使用** **let** **就对了** 

## **2.2. const** **关键字** 

const 关键字用来声明常量，const 声明有以下特点 

1) 声明必须赋初始值 

2) 标识符一般为大写 

3) 不允许重复声明 

4) 值不允许修改 

5) 块儿级作用域 

**注意对象属性修改和数组元素变化不会出发 const 错误**

**应用场景：声明对象类型使用** **const，非对象类型声明选择** **let** 

## **2.3.**变量的解构赋值

ES6 允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称 

为解构赋值。

```javascript
//数组的解构赋值
const arr = ['张学友', '刘德华', '黎明', '郭富城'];
let [zhang, liu, li, guo] = arr;

//对象的解构赋值
const lin = {
 name: '林志颖',
 tags: ['车手', '歌手', '小旋风', '演员']
};
let {name, tags} = lin;
//复杂解构
let wangfei = {
 name: '王菲',
 age: 18,
 songs: ['红豆', '流年', '暧昧', '传奇'],
 history: [
 {name: '窦唯'},
 {name: '李亚鹏'},
 {name: '谢霆锋'}
 ]
};
let {songs: [one, two, three], history: [first, second, third]} = 
wangfei;
```

**注意：频繁使用对象方法、数组元素，就可以使用解构赋值形式**

## **2.6.箭头函数**

箭头函数的注意点: 

​	1) 如果形参只有一个，则小括号可以省略 

​	2) 函数体如果只有一条语句，则花括号可以省略，函数的返回值为该条语句的 

​	执行结果 

​	3) 箭头函数 this 指向声明时所在作用域下 this 的值 

​	4) 箭头函数不能作为构造函数实例化   

​	5) 不能使用 arguments

* 箭头函数适合与this无关的回调， （定时器，数组）的方法回调
* 箭头函数不合适与this有关的回调，（事件回调，对象的方法）
* 

**注意：箭头函数不会更改** **this** **指向，用来指定回调函数会非常合适**



```javascript
	函数参数默认值
		//ES6 允许给函数参数赋值初始值
        //1. 形参初始值 具有默认值的参数, 一般位置要靠后(潜规则)
        // function add(a,c=10,b) {
        //     return a + b + c;
        // }
        // let result = add(1,2);
        // console.log(result);

        //2. 与解构赋值结合
        function connect({ host = "127.0.0.1", username, password, port }) {
            console.log(host)
            console.log(username)
            console.log(password)
            console.log(port)
        }
        connect({
            host: 'atguigu.com',
            username: 'root',
            password: 'root',
            port: 3306
        })
```

## **2.7. rest** **参数** 

ES6 引入 rest 参数，用于获取函数的实参，用来代替 arguments

```javascript
 <script>
        //代替arguments
        // function data() {
        //     console.log(arguments);
        // }
        // data('12', '23', 'qw')  //Arguments(3) ['12', '23', 'qw', callee: ƒ, Symbol(Symbol.iterator): ƒ]

        //rest
        // function data(...args) {
        //     console.log(args);
        // }
        // data('12', '23', 'qw')  //['12', '23', 'qw'] 是数组

        //rest参数必须放在最后
        function fn(a, b, ...args) {
            console.log(a);
            console.log(b);
            console.log(args);
        }
        fn(1, 2, 3, 4, 5)
</script>
```

**注意：rest **参数非常适合不定个数参数函数的场景



## **2.8. spread** **扩展运算符**

扩展运算符（spread）也是三个点（...）。它好比 rest 参数的逆运算，将一 个数组转为用逗号分隔的参数序列，对数组进行解包。

```javascript
<body>
    <div></div>
    <div></div>
    <div></div>
    <script>
        // 扩展运算符能将数组转换为逗号分隔的 参数序列
        const tfboys = ['易烊千玺', '王源', '王俊凯']

        function chunwan() {
            console.log(arguments);
        }
        // chunwan(...tfboys)// chunwan('易烊千玺', '王源', '王俊凯')

    </script>
    <script>
        // 扩展运算符的使用
        // const kuaizi = ['王太利', '小样']
        // const feihuang = ['增益', '零花']
        // // const zuixuanapple = kuaizi.concat(feihuang)
        // const zuixuanapple = [...kuaizi, ...feihuang]
        // console.log(zuixuanapple);

        //数组的克隆
        // const sanzhihua = ['e', 'g', 'm']
        // const sanyecao = [...sanzhihua]
        // console.log(sanyecao);

        //伪数组转为真数组
        const divs = document.querySelectorAll("div")
        console.log(divs);
        const divArr = [...divs]
        console.log(divArr); // [div, div, div]
    </script>
</body>
```

## **2.9.Symbol** 

**2.9.1.Symbol** **基本使用** 

ES6 引入了一种新的原始数据类型 Symbol，表示独一无二的值。它是 JavaScript 语言的第七种数据类型，是一种类似于字符串的数据类型。 

Symbol 特点 

​	1) Symbol 的值是唯一的，用来解决命名冲突的问题 

​	2) Symbol 值不能与其他数据进行运算 

​	3) Symbol 定义 的 对象属 性 不能 使 用 for…in 循 环遍 历 ，但 是可 以 使 用 Reflect.ownKeys 来获取对象的所有键名 

```javascript
 //Reflect.ownKeys
const obj = {
  a: 1,
  [Symbol.for('b')]: 2, 
  [Symbol.for('c')]: 3
};

console.log(Reflect.ownKeys(obj));
// 输出 ["a", Symbol(b), Symbol(c)]
```

```javascript
    <script>
        //创建symble
        let s = Symbol()
        /*   // console.log(s, typeof s);
          let s2 = Symbol('这是symlol')
          let s3 = Symbol('这是symlol')
          console.log(s2);  // Symbol(这是symlol)
          console.log(s3 === s2); //false */

        //Symbol.for创建
        let s4 = Symbol.for('尚硅谷')
        let s5 = Symbol.for('尚硅谷')
        console.log(s4, typeof s4); //Symbol(尚硅谷) 'symbol'
        console.log(s4 === s5); //true

        //不能与其他数据类型进行计算
        // let result = s + 100      //不行
        // let result = s > 100     //不行
        // let result = s + '100'       //不行

        //USONB 数据类型
        // u undefined
        // s string
        // o object
        // n nomber null
        // b boolean
    </script>
</body>
```

```javascript
<script>
        // Symbol.hasInstance
        class Person {
            static [Symbol.hasInstance](param) {
                console.log(param);
                console.log('我被用来检测类型了');
                return false
            }
        }

        let o = {}
        console.log(o instanceof Person);

        //Symbol.isConcatSpreadable
        const arr = [1, 2, 3]
        const arr2 = [4, 5, 6]

        arr2[Symbol.isConcatSpreadable] = false // false 不可展开，true 默认可展开
        //isConcatSpreadable是Symbol里面的属性 而Symbol.isConcatSpreadable又是arr2里面的属性
        console.log(arr.concat(arr2));//[1, 2, 3, Array(3)]
    </script>
```



symbol创建对像属性

```javascript
<body>
    <script>
        //向对象添加属性方法 up down
        let game = {
            name: '俄罗斯方块',
            up: function () { },
            down: function () { }
        };

        //声明一个对象
        let methods = {
            up: Symbol('描述11'),
            down: Symbol('描述22')
        }
        game[methods.up] = function () {
            console.log('我可以改变形状');
        }
        game[methods.down] = function () {
            console.log('我可以快速下降');
        }
        console.log(game);//{name: '俄罗斯方块', up: ƒ, down: ƒ, Symbol(描述11): ƒ, Symbol(描述22): ƒ}

        let youxi = {
            name: '狼人杀',
            [Symbol("描述")]: function () {
                console.log('L我可以发言');
            },
            [Symbol('这是描述')]: function () {
                console.log('我可以自爆');
            }
        }
        console.log(youxi);//{name: '狼人杀', Symbol(描述): ƒ, Symbol(这是描述): ƒ}
    </script>
</body>
```

### **2.9.2.Symbol** **内置值** 

除了定义自己使用的 Symbol 值以外，ES6 还提供了 11 个内置的 Symbol 值，指向语言内部使用的方法。可以称这些方法为魔术方法，因为它们会在特定的场 景下自动执行。 

| Symbol.hasInstance        | 当其他对象使用 instanceof 运算符，判断是否为该对象的实例时，会调用这个方法 |
| ------------------------- | ------------------------------------------------------------ |
| Symbol.isConcatSpreadable | 对象的 Symbol.isConcatSpreadable 属性等于的是一个布尔值，表示该对象用于 Array.prototype.concat()时，是否可以展开。 |
| Symbol.species            | 创建衍生对象时，会使用该属性                                 |
| Symbol.match              | 当执行 str.match(myObject) 时，如果该属性存在，会调用它，返回该方法的返回值。 |
| Symbol.replace            | 当该对象被 str.replace(myObject)方法调用时，会返回该方法的返回值。 |
| Symbol.search             | 当该对象被 str.search (myObject)方法调用时，会返回该方法的返回值。 |
| Symbol.split              | 当该对象被 str.split(myObject)方法调用时，会返回该方法的返回值。 |
| Symbol.iterator           | 对象进行 for...of 循环时，会调用 Symbol.iterator 方法，返回该对象的默认遍历器 |
| Symbol.toPrimitive        | 该对象被转为原始类型的值时，会调用这个方法，返回该对象对应的原始类型值。 |
| Symbol. toStringTag       | 在该对象上面调用 toString 方法时，返回该方法的返回值         |
| Symbol. unscopables       | 该对象指定了使用 with 关键字时，哪些属性会被 with环境排除。  |
|                           |                                                              |
|                           |                                                              |

```javascript
<body>
    <script>
        // Symbol.hasInstance
        // class Person {
        //     static [Symbol.hasInstance](param) {
        //         console.log(param);
        //         console.log('我被用来检测类型了');
        //         return false
        //     }
        // }

        // let o = {}
        // console.log(0 instanceof Person);

        //Symbol.isConcatSpreadable
        const arr = [1, 2, 3]
        const arr2 = [4, 5, 6]

        arr2[Symbol.isConcatSpreadable] = false // false 不可展开，true 默认可展开
        //isConcatSpreadable是Symbol里面的属性 而Symbol.isConcatSpreadable又是arr2里面的属性
        console.log(arr.concat(arr2));//[1, 2, 3, Array(3)]
    </script>
</body>
```

## **2.10.** **迭代器** 

遍历器（Iterator）就是一种机制。它是一种接口，为各种不同的数据结构提 供统一的访问机制。任何数据结构只要部署 Iterator 接口，就可以完成遍历操作。

1) ES6 创造了一种新的遍历命令 for...of 循环，Iterator 接口主要供 for...of 消费 

2) 原生具备 iterator 接口的数据(可用 for of 遍历) 

​	a) Array 

​	b) Arguments 

​	c) Set 

​	d) Map 

​	e) String 

​	f) TypedArray 

​	g) NodeList 

3) ==工作原理== 

​	a) 创建一个指针对象，指向当前数据结构的起始位置 

​	b) 第一次调用对象的 next 方法，指针自动指向数据结构的第一个成员 

​	c) 接下来不断调用 next 方法，指针一直往后移动，直到指向最后一个成员 

​	d) 每调用 next 方法返回一个包含 value 和 done 属性的对象 

**注**: **需要自定义遍历数据的时候，要想到迭代器。** 

## **2.11.** **生成器** 

生成器函数是 ES6 提供的一种异步编程解决方案，语法行为与传统函数完全不同 

代码说明： 

​	1) * 的位置没有限制 

​	2) 生成器函数返回的结果是迭代器对象，调用迭代器对象的 next 方法可以得到 

​	yield 语句后的值 

​	3) yield 相当于函数的暂停标记，也可以认为是函数的分隔符，每调用一次 next 

​	方法，执行一段代码 

​	4) next 方法可以传递实参，作为 yield 语句的返回值

```javascript
<script>
        //生成器其实就是一个特殊函数
        //异步编程 
        // yield 相当于代码的分隔符 
        //遇到yield 就停止，遇到next就继续
        function* gen() {
            // console.log('你好1');
            yield '一直没有耳朵'
            // console.log('你好2');
            yield '美誉'
            // console.log('你好3');
            yield '美2'
        }
        let iterator = gen()
        // console.log(iterator);

        // iterator.next()        // 你好
        // iterator.next()        // 你好1 你好2
        // iterator.next()       // 你好1 你好2 你好3

        console.log(iterator.next()) //{value: '一直没有耳朵', done: false}
        console.log(iterator.next()) //{value: '美誉', done: false}
        console.log(iterator.next()) //{value: '美2', done: false}
        console.log(iterator.next()) //{value: undefined, done: true}

        //遍历
        // for (let v of gen()) {
        //     console.log(v);
        // }
    </script>
```

### 生成器函数

生成器函数传入参数

```javascript
<script>
        //iterator.next() 的返回结果是yield 后面的结果或者语句
        function* gen(arg) {
            console.log(arg);
            let one = yield 111
            console.log(one); //BBB
            let two = yield 222
            console.log(two); //CCC
            let three = yield 333
            console.log(three); //DDD
        }

        //执行获取迭代器对象
        let iterator = gen('AAA')
        console.log(iterator.next());//{value: 111, done: false}

        //next方法可以传入实参 第二次调用next()传入的参数将作为 第一个yield整体的返回结果
        console.log(iterator.next('BBB')) //{value: 222, done: false}

        //第三次调用next()传入的参数将作为 第二个yield整体的返回结果
        console.log(iterator.next('CCC')) //{value: 222, done: false}

        //第四次调用next()传入的参数将作为 第三个yield整体的返回结果
        console.log(iterator.next('DDD')) //{value: 222, done: false}

        // console.log(iterator.next())//{value: 111, done: false}
        // console.log(iterator.next())//{value: 222, done: false}
        // console.log(iterator.next())//{value: 333, done: false}
        // console.log(iterator.next())//{value: undefined, done: true}
    </script>
```

生成器函数实例-1

```javascript
<script>
        //异步编程 文件操作，网络操作，数据库操作
        //1s 后控制台输出 111 2s后控制台输出222 3s后控制台输出333
        function one() {
            setTimeout(() => {
                console.log(111);
            }, 1000)
        }

        function two() {
            setTimeout(() => {
                console.log(222);
            }, 2000)
        }

        function three() {
            setTimeout(() => {
                console.log(333);
            }, 3000)
        }

        function* gen() {
            yield one()
            yield two()
            yield three()
        }

        //调用生成器函数
        let iterator = gen()
        iterator.next()
        iterator.next()
        iterator.next()
    </script>
```

生成器函数实例-2

```javascript
<script>
        //模拟获取 1.用户数据，2.订单数据，3.商品数据 按顺序
        function getUsers() {
            setTimeout(() => {
                let data = '用户数据'
                //调用next方法，并且将数据传入
                iterator.next(data) // 这是第二次调用next() 它的实参 将作为第一个yield 的返回结果
            }, 1000)
        }

        function getOrders() {
            setTimeout(() => {
                let data = '订单数据'
                iterator.next(data) // 这是第3次调用next() 它的实参 将作为第2个yield 的返回结果
            }, 1000)
        }

        function getGoods() {
            setTimeout(() => {
                let data = '商品数据'
                iterator.next(data) // 这是第4次调用next() 它的实参 将作为第3个yield 的返回结果
            }, 1000)
        }

        function* gen() {
            let users = yield getUsers()
            console.log(users);
            let orders = yield getOrders()
            console.log(orders);
            let goods = yield getGoods()
            console.log(goods);
        }

        //调用生成器函数
        let iterator = gen()
        iterator.next()
    </script>
```

## **2.12. Promise**

Promise 是 ES6 引入的异步编程的新解决方案。语法上 Promise 是一个构造函数， 

用来封装异步操作并可以获取其成功或失败的结果。 

​	1) Promise 构造函数: Promise (excutor) {} 

​	2) Promise.prototype.then 方法 

​	3) Promise.prototype.catch 方法

### promise基本语法

```javascript
<script>
        const p = new Promise((resolve, reject) => {
            setTimeout(function () {
                // let data = '用户数据成功'
                // resolve(data)

                let data2 = '用户数据失败'
                reject(data2)
            }, 1000)
        })

        //调用promise 对象的then方法
        p.then(value => {
            console.log(value);
        }, reason => {
            console.log(reason);
        })
    </script>
```

### promise封装读取文件

```javascript
//1. 引入 fs 模块
const { rejects } = require('assert');
const fs = require('fs');
const { resolve } = require('path');

//2. 调用方法读取文件
// fs.readFile('./resources/为学.md', (err, data) => {
//     //如果失败, 则抛出错误
//     if (err) throw err;
//     //如果没有出错, 则输出内容
//     console.log(data.toString());
// });

//3.使用Promise 封装
const p = new Promise((resolve, reject) => {
    fs.readFile("./resources/为学.md", (err, data) => {
        if (err) reject(err)
        resolve(data)
    })
})

p.then(value => {
    console.log(value.toString());
}, reason => {
    console.log('失败');
})
```

promise封装ajax

```javascript
<script>
        //  接口地址: https://api.apiopen.top/getJoke
        const p = new Promise((resolve, reject) => {
            const xhr = new XMLHttpRequest()
            xhr.open('get', 'http://jsonplaceholder.typicode.com/posts')
            xhr.send()
            xhr.onreadystatechange = function () {
                if (xhr.readyState === 4) {
                    if (xhr.status >= 200 && xhr.status < 300) {
                        // console.log(xhr.response);
                        resolve(xhr.response)
                    } else {
                        // console.log(xhr.status);
                        reject(xhr.status)
                    }
                }
            }
        })

        p.then(value => {
            console.log(value);
        }, reason => {
            console.log(reason);
        })
    </script>
```

### promise-then方法

```javascript
<script>
        const p = new Promise((resolve, reject) => {
            setTimeout(() => {
                resolve("用户数据")
                // reject("出错了")
            }, 1000)
        })
        //调用 then方法 then方法的返回结果 是Promise对象 对象状态由回调函数的执行结果决定
        //1. 如果回调函数中返回的结果是 非 promise 类型的属性, 状态为成功, 返回值为对象的成功的值

        let result = p.then(value => {
            // console.log(value);

            //1.非promise类型的属性
            // return '123'  //[[PromiseState]] 成功

            //2.promise类型的属性
            // return new Promise((resolve, reject) => { //取决于这个promise的状态
            //     // resolve('ok')
            //     // reject('err')
            // })

            //3.抛出错误
            // throw '出错了' //失败

        }, reason => {
            console.warn(reason);
        })
        //链式调用
        // p.then(value => {

        // }).then(value => {

        // });
        console.log(result);
</script>
```

### promise-catch方法

```javascript
<script>
        const p = new Promise((resolve, reject) => {
            setTimeout(() => {
                // resolve("用户数据")
                reject("出错了")
            }, 1000)
        })

        // p.then(value => {
        //     console.log(value);
        // }, reason => {
        //     console.log(reason);
        // })

        p.catch(reason => {
            console.log(reason);
        })
</script>
```

promise读取多个文件实践

```javascript
const fs = require("fs")

// fs.readFile("./resources/为学.md", (err, data1) => {
//     fs.readFile("./resources/插秧诗.md", (err, data2) => {
//         fs.readFile("./resources/观书有感.md", (err, data3) => {
//             let result = data1 + '\r\n' + data2 + '\r\n' + data3
//             console.log(result);
//         })
//     })
// })

//使用promise实现
const p = new Promise((resolve, reject) => {
    fs.readFile("./resources/为学.md", (err, data) => {
        resolve(data)
    })
})

p.then(value => {
    // console.log(value.toString());
    return new Promise((resolve, reject) => {
        fs.readFile("./resources/插秧诗.md", (err, data) => {
            resolve([value, data])
        })
    })
}).then(value => {
    return new Promise((resolve, reject) => {
        fs.readFile("./resources/观书有感.md", (err, data) => {
            value.push(data)
            resolve(value)
        })
    })
}).then(value => {
    console.log(value.join('\r\n'));
})
```

## **2.13. Set**

ES6 提供了新的数据结构 Set（集合）。它类似于数组，但成员的值都是唯 一的，集合实现了 iterator 接口，所以可以使用『扩展运算符』和『for…of…』进 行遍历，集合的属性和方法： 

​	1) size 

​		返回集合的元素个数 

​	2) add 

​		增加一个新元素，返回当前集合 

​	3) delete 删除元素，返回 boolean 值 

​	4) has 

​		检测集合中是否包含某个元素，返回 boolean 值 

​	5) clear 

​		清空集合，返回 undefined

### 基础操作

```javascript
<script>
        // 声明一个set
        let s = new Set()
        console.log(s, typeof s);//Set(0) {size: 0} 'object'
        let s2 = new Set([1, 2, 3, 4, 5, 1])
        console.log(s2); //Set(5) {1, 2, 3, 4, 5} 自动去重

        //元素个数
        console.log(s2.size); // 5 相当于length
        //添加元素
        s2.add('add')
        //删除元素
        s2.delete('add')
        //检测
        console.log(s2.has(7)); //false
        //清空
        // s2.clear()
        //b遍历
        for (let v of s2) {
            console.log(v);
        }
        console.log(s2);
    </script>
```

### set方法实践

```javascript
<script>
        let arr = [1, 2, 3, 4, 5, 4, 3, 2, 1]
        //1.去重
        // let res = [...new Set(arr)]
        // console.log(res); // [1, 2, 3, 4, 5]

        //2.交集
        let arr2 = [4, 5, 6, 5, 6]
        // let res = [...new Set(arr)].filter(item => {
        //     let s2 = new Set(arr2) // 4,5,6
        //     if (s2.has(item)) {
        //         return true
        //     } else {
        //         return false
        //     }
        // })
        // console.log(res); //  [4, 5]

        //简化
        // let res = [...new Set(arr)].filter(item => new Set(arr2).has(item))
        // console.log(res); //  [4, 5]

        //3.并集
        // let union = [...new Set([...arr, ...arr2])]
        // console.log(union);

        //4.差集: 如a里面有123，b里面有345 a与b的差集是12， b与a的差集是45  a减a交b
        let diff = [...new Set(arr)].filter(item => !(new Set(arr2).has(item)))
        console.log(diff);
    </script>
```

## **2.14. Map**

ES6 提供了 Map 数据结构。它类似于对象，也是键值对的集合。但是“键” 的范围不限于字符串，各种类型的值（包括对象）都可以当作键。Map 也实现了 iterator 接口，所以可以使用『扩展运算符』和『for…of…』进行遍历。

### Map 的属 性和方法： 

### 	1) size 

​		返回 Map 的元素个数 

### 	2) set 

​		增加一个新元素，返回当前 Map 

### 	3) get 

​		返回键名对象的键值 

### 	4) has 

​		检测 Map 中是否包含某个元素，返回 boolean 值 

### 	5) clear 

​		清空集合，返回 undefined 

```javascript
 <script>
        //声明 Map
        let m = new Map()

        //添加元素
        m.set('name', '尚硅谷')

        console.log(m); //Map(1) {'name' => '尚硅谷'}

        m.set('change', function () {
            console.log('添加');
        })
        console.log(m);//Map(2) {'name' => '尚硅谷', ƒ => undefined}

        let key = {
            school: '校区'
        }
        m.set(key, ['北京', '上海', '深圳'])
        console.log(m); //Map(3) {'name' => '尚硅谷', ƒ => undefined, {…} => Array(3)}

        console.log(m.size); //3

        //删除
        m.delete('name')
        console.log(m); //Map(2) {ƒ => undefined, {…} => Array(3)}

        //获取
        console.log(m.get('change')); //ƒ () {console.log('添加');}
        console.log(m.get(key));  // ['北京', '上海', '深圳']

        //清空
        // m.clear()
        // console.log(m);

        //遍历
        for (let v of m) {
            console.log(v);// 数组 键 值
        }
    </script>
```

## **2.15. class** **类** 

​		ES6 提供了更接近传统语言的写法，引入了 Class（类）这个概念，作为对 象的模板。通过 class 关键字，可以定义类。基本上，ES6 的 class 可以看作只是 一个语法糖，它的绝大部分功能，ES5 都可以做到，新的 class 写法只是让对象 原型的写法更加清晰、更像面向对象编程的语法而已。 

知识点： 

​	1) class 声明类 

​	2) constructor 定义构造函数初始化 

​	3) extends 继承父类 

​	4) super 调用父级构造方法 

​	5) static 定义静态方法和属性 

​	6) 父类方法可以重写 

### 基本语法

```javascript
<script>
        //手机
        // function Phone(brand, price) {
        //     this.brand = brand
        //     this.price = price
        // }

        // //添加方法
        // Phone.prototype.call = function () {
        //     console.log('我可以打电话');
        // }

        // //实例对象
        // let Huawei = new Phone('华为', 5999)
        // Huawei.call()
        // console.log(Huawei);

        class Phone {
            //构造方法 名字固定
            constructor(brand, price) {
                this.brand = brand
                this.price = price
            }

            //方法必须使用该语法  不能是ES5的写法 ：function(){}
            call() {
                console.log('我可以打电话');
            }
        }

        let xiaomi = new Phone('小米', 1999)
        console.log(xiaomi);
        xiaomi.call()
    </script>
```

ES5组合继承

```javascript
<script>
        //手机
        function Phone(brand, price) {
            this.brand = brand;
            this.price = price;
        }

        Phone.prototype.call = function () {
            console.log("我可以打电话");
        }

        //智能手机
        function SmartPhone(brand, price, color, size) {
            Phone.call(this, brand, price);
            this.color = color;
            this.size = size;
        }

        //设置子级构造函数的原型
        SmartPhone.prototype = new Phone;
        SmartPhone.prototype.constructor = SmartPhone;

        //声明子类的方法
        SmartPhone.prototype.photo = function () {
            console.log("我可以拍照")
        }

        SmartPhone.prototype.playGame = function () {
            console.log("我可以玩游戏");
        }

        const chuizi = new SmartPhone('锤子', 2499, '黑色', '5.5inch');

        console.log(chuizi);
        chuizi.playGame() //我可以玩游戏
        chuizi.photo() //我可以拍照
        chuizi.call() //我可以打电话
    </script>
```

### 类继承

```javascript
<script>
        class Phone {
            //构造方法
            constructor(brand, price) {
                this.brand = brand;
                this.price = price;
            }
            //父类的成员属性
            call() {
                console.log("我可以打电话!!");
            }
        }

        class SmartPhone extends Phone {
            //构造方法
            constructor(brand, price, color, size) {
                super(brand, price);// Phone.call(this, brand, price)
                this.color = color;
                this.size = size;
            }

            photo() {
                console.log("拍照");
            }

            playGame() {
                console.log("玩游戏");
            }

            call() {
                console.log('我可以进行视频通话');
                super.call()
            }
        }

        const xiaomi = new SmartPhone('小米', 799, '黑色', '4.7inch');
        console.log(xiaomi); //SmartPhone {brand: '小米', price: 799, color: '黑色', size: '4.7inch'}
        xiaomi.call();  //我可以进行视频通话
        xiaomi.photo();  //拍照
        xiaomi.playGame();  //玩游戏
    </script>
```

### class的get和set

```javascript
 <script>
        // get 和 set
        class Phone {
            get price() {
                console.log("价格属性被读取了");
                // return 'iloveyou';
            }

            set price(newVal) { //设置属性必须要有一个参数
                console.log('价格属性被修改了');
            }
        }

        //实例化对象
        let s = new Phone();

        console.log(s.price); //  他的返回值就是属性的值
        // s.price = 'free';
</script>
```

## **2.16.** **数值扩展** 

**2.16.1.** 

**二进制和八进制** 

ES6 提供了二进制和八进制数值的新的写法，分别用前缀 0b 和 0o 表示。 

**2.16.2.** 

**Number.isFinite()** **与** **Number.isNaN()**  

Number.isFinite() 用来检查一个数值是否为有限的 

Number.isNaN() 用来检查一个值是否为 NaN 

**2.16.3.** 

**Number.parseInt()** **与** **Number.parseFloat()**  

ES6 将全局方法 parseInt 和 parseFloat，移植到 Number 对象上面，使用不变。 

**2.16.4.** 

**Math.trunc** 

用于去除一个数的小数部分，返回整数部分。

**2.16.5.** 

**Number.isInteger** 

Number.isInteger() 用来判断一个数值是否为整数

```javascript
<script>
        //0. Number.EPSILON 是 JavaScript 表示的最小精度
        //EPSILON 属性的值接近于 2.2204460492503130808472633361816E-16
        function equal(a, b) {
            if (Math.abs(a - b) < Number.EPSILON) {
                return true;
            } else {
                return false;
            }
        }
        console.log(0.1 + 0.2 === 0.3); // false
        console.log(equal(0.1 + 0.2, 0.3)) //true

        //1. 二进制和八进制
        let b = 0b1010; // 0b 二进制
        let o = 0o777;  // 0o 八进制
        let d = 100;    // 
        let x = 0xff;   // 0x 16进制
        console.log(b);
        console.log(o);
        console.log(d);
        console.log(x);

        //2. Number.isFinite  检测一个数值是否为有限数
        console.log(Number.isFinite(100)); //true
        console.log(Number.isFinite(100 / 0)); //false
        console.log(Number.isFinite(Infinity)); //false

        //3. Number.isNaN 检测一个数值是否为 NaN
        console.log(Number.isNaN(123)); false
        console.log(Number.isNaN('asd')); false
        console.log(Number.isNaN(Number('sd'))); //true

        //4. Number.parseInt Number.parseFloat字符串转整数
        console.log(Number.parseInt('5211314love')); //5211314
        console.log(Number.parseFloat('3.1415926神奇')); //3.1415926

        //5. Number.isInteger 判断一个数是否为整数
        console.log(Number.isInteger(5)); //true
        console.log(Number.isInteger(2.2)); //false

        //6. Math.trunc 将数字的小数部分抹掉
        console.log(Math.trunc(3.6)); //3

        //7. Math.sign 判断一个数到底为正数 负数 还是零
        console.log(Math.sign(100)); // 1
        console.log(Math.sign(0));  //0
        console.log(Math.sign(-20000)); //-1
    </script>
```

## **2.17.** **对象扩展**

```javascript
<script>
        //1. Object.is 判断两个值是否完全相等 
        console.log(Object.is(120, 120));// === 
        console.log(Object.is(NaN, NaN));// 
        console.log(NaN === NaN);// false

        //2. Object.assign 对象的合并
        const config1 = {
            host: 'localhost',
            port: 3306,
            name: 'root',
            pass: 'root',
            test: 'test'
        };
        const config2 = {
            host: 'http://atguigu.com',
            port: 33060,
            name: 'atguigu.com',
            pass: 'iloveyou',
            test2: 'test2'
        }
        console.log(Object.assign(config1, config2)); // 合并 config2 覆盖 config1

        //3. Object.setPrototypeOf 设置原型对象  Object.getPrototypeof
        const school = {
            name: '尚硅谷'
        }
        const cities = {
            xiaoqu: ['北京', '上海', '深圳']
        }
        Object.setPrototypeOf(school, cities); // 为school设置cities
        console.log(Object.getPrototypeOf(school));
        console.log(school);
</script>
```



## **2.18.** **模块化** 

模块化是指将一个大的程序文件，拆分成许多小的文件，然后将小文件组合起来。 

### **2.18.1.** **模块化的好处** 

模块化的优势有以下几点： 

​	1) 防止命名冲突 

​	2) 代码复用 

​	3) 高维护性 

### **2.18.2.** **模块化规范产品** 

ES6 之前的模块化规范有： 

​	1) CommonJS 	=>	 NodeJS、Browserify 

​	2) AMD 	=> 	requireJS 

​	3) CMD 	=> 	seaJS

### **2.18.3.** **ES6** **模块化语法** 

模块功能主要由两个命令构成：export 和 import。 

⚫ export 命令用于规定模块的对外接口 

⚫ import 命令用于输入其他模块提供的功能 



# **第** **3** **章** **ECMASript 7** **新特性**

## **3.1.Array.prototype.includes** 

Includes 方法用来检测数组中是否包含某个元素，返回布尔类型值 

## **3.2.指数操作符** 

在 ES7 中引入指数运算符「**」，用来实现幂运算，功能与 Math.pow 结果相同

```javascript
<script>
        // includes   indexOf
        const mingzhu = ['西游记', '红楼梦', '三国演义', '水浒传'];

        //判断
        console.log(mingzhu.includes('西游记')); // true
        console.log(mingzhu.includes('金瓶梅')); //false

        // **
        console.log(2 ** 10);//
        console.log(Math.pow(2, 10));
    </script>
```

# **第** **4** **章** **ECMASript 8** **新特性**

## **4.1.async** **和** **await** 

async 和 await 两种语法结合可以让异步代码像同步代码一样 

## **4.1.1.async** **函数** 

1. async 函数的返回值为 promise 对象， 

2. promise 对象的结果由 async 函数执行的返回值决定 

```javascript
<script>
        //async 函数
        async function fn() {
            // 返回一个字符串
            // return '尚硅谷';
            // 返回的结果不是一个 Promise 类型的对象, 返回的结果就是成功 Promise 对象
            // return;
            // 抛出错误, 返回的结果是一个失败的 Promise
            // throw new Error('出错啦!');
            //返回的结果如果是一个 Promise 对象
            return new Promise((resolve, reject) => {
                // resolve('成功的数据');
                reject("失败的错误");
            });
        }

        const result = fn();
        console.log(result);

        //调用 then 方法
        result.then(value => {
            console.log(value);
        }, reason => {
            console.warn(reason);
        })
    </script>
```



## 4.1.2.await **表达式** 

1. await 必须写在 async 函数中

2. await 右侧的表达式一般为 promise 对象 

3. await 返回的是 promise 成功的值 

4. await 的 promise 失败了, 就会抛出异常, 需要通过 try...catch 捕获处理 

```javascript
<script>
        //创建 promise 对象
        const p = new Promise((resolve, reject) => {
            // resolve("用户数据");
            reject("失败啦!");
        })

        // await 要放在 async 函数中.
        async function main() {
            try {
                let result = await p;
                //
                console.log(result);
            } catch (e) {
                console.warn(e);
            }
        }
        //调用函数
        main();
    </script>
```

### async和await结合发送AJAX请求

```javascript
<script>
        // 发送 AJAX 请求, 返回的结果是 Promise 对象
        function sendAJAX(url) {
            return new Promise((resolve, reject) => {
                //1. 创建对象
                const x = new XMLHttpRequest();

                //2. 初始化
                x.open('GET', url);

                //3. 发送
                x.send();

                //4. 事件绑定
                x.onreadystatechange = function () {
                    if (x.readyState === 4) {
                        if (x.status >= 200 && x.status < 300) {
                            //成功啦
                            resolve(x.response);
                        } else {
                            //如果失败
                            reject(x.status);
                        }
                    }
                }
            })
        }

        //promise then 方法测试
        // sendAJAX("http://jsonplaceholder.typicode.com/posts").then(value => {
        //     console.log(value);
        // }, reason => { })

        // async 与 await 测试  axios
        async function main() {
            //发送 AJAX 请求
            let result = await sendAJAX("http://jsonplaceholder.typicode.com/posts");
            //再次测试
            let tianqi = await sendAJAX('http://jsonplaceholder.typicode.com/posts')

            console.log(result);
            console.log(tianqi);
        }
        main();
    </script>
```



## **4.2.Object.values** **和** **Object.entries** 

1. Object.values()方法返回一个给定对象的所有可枚举属性值的数组 

2. Object.entries()方法返回一个给定对象自身可遍历属性 [key,value] 的数组 

```javascript
<script>
        //声明对象
        const school = {
            name: "尚硅谷",
            cities: ['北京', '上海', '深圳'],
            xueke: ['前端', 'Java', '大数据', '运维']
        };

        //获取对象所有的键
        console.log(Object.keys(school));//(3) ['name', 'cities', 'xueke']
        //获取对象所有的值
        console.log(Object.values(school));//(3) ['尚硅谷', Array(3), Array(4)]
        //entries
        console.log(Object.entries(school));//[Array(2), Array(2), Array(2)] 

        //创建Map
        const m = new Map(Object.entries(school))
        console.log(m);//{'name' => '尚硅谷', 'cities' => Array(3), 'xueke' => Array(4)}
    </script>
```



## 4.3.Object.getOwnPropertyDescriptors** 

该方法返回指定对象所有自身属性的描述对象

```javascript
<script>

        //对象属性描述
        console.log(Object.getOwnPropertyDescriptors(school));//{name: {…}, cities: {…}, xueke: {…}}

        const obj = Object.create(null, {
            name: {
                //设置值
                value: '尚硅谷',
                //属性特性
                writable: true, // 是否可写
                configurable: true, //是否可以删除
                enumerable: true // 是否可以枚举
            }
        });
    </script>
```

# **第** **5** **章** **ECMASript 9** **新特性**

## **5.1.Rest/Spread** **属性**

Rest 参数与 spread 扩展运算符在 ES6 中已经引入，不过 ES6 中只针对于数组， 在 ES9 中为对象提供了像数组一样的 rest 参数和扩展运算符

```javascript
<script>
        // Rest 参数与 spread 扩展运算符在 ES6 中已经引入，不过 ES6 中只针对于数组，
        // 在 ES9 中为对象提供了像数组一样的 rest 参数和扩展运算符

        //rest 参数
        // function connect({ host, port, ...user }) {
        //     console.log(host); //127.0.0.1
        //     console.log(port); // 3306
        //     console.log(user); //{username: 'root', password: 'root', type: 'master'}
        // }

        // connect({
        //     host: '127.0.0.1',
        //     port: 3306,
        //     username: 'root',
        //     password: 'root',
        //     type: 'master'
        // });


        //对象合并
        const skillOne = {
            q: '天音波'
        }

        const skillTwo = {
            w: '金钟罩'
        }

        const skillThree = {
            e: '天雷破'
        }
        const skillFour = {
            r: '猛龙摆尾'
        }

        const mangseng = { ...skillOne };
        console.log(mangseng)//{q: '天音波'}

        const mangseng2 = { ...skillOne, ...skillTwo };
        console.log(mangseng2); //{q: '天音波', w: '金钟罩'}

        const mangseng3 = { ...skillOne, ...skillTwo, ...skillThree, ...skillFour };
        console.log(mangseng3); //{q: '天音波', w: '金钟罩', e: '天雷破', r: '猛龙摆尾'}

        // ...skillOne   =>  q: '天音波', w: '金钟罩'
    </script>
```

## **5.2.****正则表达式命名捕获组** 

ES9 允许命名捕获组使用符号『?<name>』,这样获取捕获结果可读性更强

```javascript
<script>
        // 声明一个字符串
        // let str = '<a href="http://www.atguigu.com">尚硅谷</a>';

        // //提取 url 与 『标签文本』
        // const reg = /<a href="(.*)">(.*)<\/a>/;

        // //执行
        // const result = reg.exec(str);

        // console.log(result); //['<a href="http://www.atguigu.com">尚硅谷</a>', 'http://www.atguigu.com', '尚硅谷', index: 0, input: '<a href="http://www.atguigu.com">尚硅谷</a>', groups: undefined]
        // console.log(result[1]);//http://www.atguigu.com
        // console.log(result[2]);//尚硅谷


        //分组命名
        let str = '<a href="http://www.atguigu.com">尚硅谷</a>';
        const reg = /<a href="(?<url>.*)">(?<text>.*)<\/a>/;

        const result = reg.exec(str);
        console.log(result); //['<a href="http://www.atguigu.com">尚硅谷</a>', 'http://www.atguigu.com', '尚硅谷', index: 0, input: '<a href="http://www.atguigu.com">尚硅谷</a>', groups: {…}]

        console.log(result.groups.url); //http://www.atguigu.com

        console.log(result.groups.text); //尚硅谷
    </script>
```

## **5.3.****正则表达式反向断言** 

ES9 支持反向断言，通过对匹配结果前面的内容进行判断，对匹配进行筛选。

```javascript
<script>
        //声明字符串
        let str = 'JS5211314你知道么555啦啦啦';
        //正向断言
        // const reg = /\d+(?=啦)/;
        // const result = reg.exec(str);
        // console.log(result); //['555', index: 13, input: 'JS5211314你知道么555啦啦啦', groups: undefined]

        //反向断言
        const reg = /(?<=么)\d+/;
        const result = reg.exec(str);
        console.log(result); //['555', index: 13, input: 'JS5211314你知道么555啦啦啦', groups: undefined]
    </script>
```

## **5.4.****正则表达式** **dotAll** **模式** 

正则表达式中点 . 匹配除回车外的任何单字符，标记『s』改变这种行为，允许行 终止符出现

```javascript
<script>
        //dot  .  元字符  除换行符以外的任意单个字符
        let str = `
        <ul>
            <li>
                <a>肖生克的救赎</a>
                <p>上映日期: 1994-09-10</p>
            </li>
            <li>
                <a>阿甘正传</a>
                <p>上映日期: 1994-07-06</p>
            </li>
        </ul>`

        //需求：把电影名称和上映时间提取出来

        //声明正则
        // const reg = /<li>\s+<a>(.*?)<\/a>\s+<p>(.*?)<\/p>/;
        const reg = /<li>.*?<a>(.*?)<\/a>.*?<p>(.*?)<\/p>/gs; //dotAll
        //执行匹配
        // const result = reg.exec(str);
        // console.log(result);

        let res;
        let data = [];
        while (res = reg.exec(str)) {
            console.log(res);
            data.push({ title: res[1], time: res[2] });
        }
        //输出结果
        console.log(data);
    </script>
```

# **第** **6** **章** **ECMASript 10** **新特性** 

## **6.1.Object.fromEntries** 

二维数组转对象

```javascript
<script>
        //二维数组  
        const result = Object.fromEntries([  //二维数组转对象
            ['name', '尚硅谷'],
            ['xueke', 'Java,大数据,前端,云计算']
        ]);
        console.log(result); //{name: '尚硅谷', xueke: 'Java,大数据,前端,云计算'}

        //Map
        // const m = new Map();
        // m.set('name', 'ATGUIGU');
        // const result = Object.fromEntries(m);
        // console.log(result) //{name: 'ATGUIGU'}

        // Object.entries   对象转二维数组     ES8 
        const arr = Object.entries({
            name: "尚硅谷"
        })
        console.log(arr);
    </script>
```



## **6.2.trimStart** **和** **trimEnd** 

```javascript
<script>
        // trim
        let str = '   iloveyou   ';

        console.log(str); //   iloveyou  
        console.log(str.trimStart()); //iloveyou  清除左侧
        console.log(str.trimEnd());//   iloveyou  清除右侧
</script>
```



## **6.3.Array.prototype.flat** **与** **flatMap** 

```javascript
<script>
        //flat 平
        //将多维数组转化为低位数组
        const arr = [1, 2, 3, 4, [5, 6]];
        console.log(arr.flat()); // [1, 2, 3, 4, 5, 6]

        const arr2 = [1, 2, 3, 4, [5, 6, [7, 8, 9]]];
        //参数为深度 是一个数字
        console.log(arr2.flat()); // [1, 2, 3, 4, 5, 6, Array(3)]
        console.log(arr2.flat(2)); // [1, 2, 3, 4, 5, 6, 7, 8, 9]

        //flatMap 转为一维数组
        const arr3 = [1, 2, 3, 4];

        const result = arr3.map(item => [item * 10]);
        console.log(result); //[Array(1), Array(1), Array(1), Array(1)]

        const result2 = arr3.flatMap(item => [item * 10]);
        console.log(result2); // [10, 20, 30, 40]
    </script>
```



## **6.4.Symbol.prototype.description** 

```javascript
 <script>
        //创建 Symbol
        let s = Symbol('尚硅谷');
        console.log(s.description); //尚硅谷
</script>
```

# **第** **7** **章** **ECMASript 11** **新特性** 

## **7.1.String.prototype.matchAll** 

```javascript
<script>
        let str = `<ul>
            <li>
                <a>肖生克的救赎</a>
                <p>上映日期: 1994-09-10</p>
            </li>
            <li>
                <a>阿甘正传</a>
                <p>上映日期: 1994-07-06</p>
            </li>
        </ul>`;

        //声明正则
        const reg = /<li>.*?<a>(.*?)<\/a>.*?<p>(.*?)<\/p>/sg

        //调用方法
        const result = str.matchAll(reg);
        console.log(result);
        // console.log(...result);

        for (let v of result) {
            console.log(v);
        }

        const arr = [...result];

        console.log(arr);
    </script>
```



## **7.2.**类的私有属性

```javascript
<script>
        class Person {
            //公有属性
            name;
            //私有属性
            #age;
            #weight;
            //构造方法
            constructor(name, age, weight) {
                this.name = name;
                this.#age = age;
                this.#weight = weight;
            }

            intro() {
                console.log(this.name);
                console.log(this.#age); //可以访问
                console.log(this.#weight); //可以访问
            }
        }

        //实例化
        const girl = new Person('晓红', 18, '45kg');
        console.log(girl);

        console.log(girl.name);
        // console.log(girl.#age); //访问不到
        // console.log(girl.#weight); //访问不到

        girl.intro();
</script>
```



## **7.3.Promise.allSettled** 

```javascript
<script>
        // Promise.allSettled 当里面的promise都完成（失败或成功）   返回的结果就是 成功  否则就是pending

        //声明两个promise对象
        const p1 = new Promise((resolve, reject) => {
            setTimeout(() => {
                reject('出错啦!');
                // resolve('商品数据 - 1');
            }, 1000)
        });

        const p2 = new Promise((resolve, reject) => {
            setTimeout(() => {
                // resolve('商品数据 - 2');
                reject('出错啦!');
            }, 1000)
        });

        //调用 allsettled 方法
        const result = Promise.allSettled([p1, p2]);
        console.log(result);

        // Promise.all 返回的结果 全部成功就成功，有一个失败就失败
        const res = Promise.all([p1, p2]);
        console.log(res);
    </script>
```



## **7.4.**可选链操作符

```javascript
<script>
        // ?.判断前面的值有没有传入  前面有就继续读取后面的属性
        function main(config) {
            // const dbHost = config && config.db && config.db.host;
            const dbHost = config?.db?.host;

            console.log(dbHost);
        }

        main({
            db: {
                host: '192.168.1.100',
                username: 'root'
            },
            cache: {
                host: '192.168.1.200',
                username: 'admin'
            }
        })
    </script>
```



## **7.5.**动态 **import** **导入** 



## 7.6.BigInt类型

```javascript
<script>
        //大整形
        // let n = 521n;
        // console.log(n, typeof (n)); //521n 'bigint'

        //函数
        let n = 123;
        console.log(BigInt(n));
        // console.log(BigInt(1.2)); //报错，不是整数

        //大数值运算
        let max = Number.MAX_SAFE_INTEGER;
        console.log(max); //9007199254740991
        console.log(max + 1); //9007199254740992
        console.log(max + 2); //9007199254740992 不能再加了

        console.log(BigInt(max)) // 9007199254740991n
        console.log(BigInt(max) + BigInt(1)) // 9007199254740992n
        console.log(BigInt(max) + BigInt(2)) // 9007199254740992n
    </script>
```



## **7.6.globalThis** **对象**

```javascript
<script>
    //始终指向全局对象
        console.log(globalThis); //Window {window: Window, self: Window, document: document, name: '', location: Location, …}
</script>
```















































