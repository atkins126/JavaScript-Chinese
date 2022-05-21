# JavaScript-Useful
## 为什么JavaScript行内样式要写到document底部？
- JavaScript执行机制是从上往下执行的，所以浏览器加载完文档内容（DOM元素）之后再加载JS对DOM元素进行操作
<br/>如果我们将JS放到文档的上面，那么JS找不到对应的DOM元素，也就不能对DOM元素进行操作，并且报错

- 当然，我们可以通过入口函数来解决这个问题:
```JS
// 等页面内容全部加载完毕,包括DOM元素、图片、flash、css等才会执行入口函数中的JS代码
window.addEventListener('load',() => {

})
// or
// 只要DOM元素加载完毕就会立即执行JS代码
window.addEventListener('DOMContentLoaded',() => {

})
```
--- 
## JavaScript输出语句
```JS
// 弹出警告框⚠
window.alert()

// 写入浏览器控制台
console.log()
console.dir()

// 写入内容到HTML元素内
innerHTML

// 写入到HTML文档
// 没有什么大用-基本用不到
// 如果文档已完成加载 再执行document.write()方法，是会造成页面覆盖的
document.write()
```
--- 
## 字面量
- 字面量是指由字母、数字等构成的字符串或者数值
- 字面量只能作为值出现（键 = 值）
- 它们是你在脚本中字面上写出来的固定的值
- Literals represent values in JavaScript. These are fixed values—not variables—that you literally provide in your script
```JS
// 数字字面量(Number)
3.15926   100   -66

// 字符串字面量(String)
'Hello'   "World"   'JavaScript'

// 表达式字面量
66 * 88   22 + 66

// 数组字面量(Array)
[ 30 , 66 , 20 , 100 ]

// 对象字面量(Object)
{ username: "Brave-AirPig", age: 22, hobby: [ "敲代码", "敲代码" ] }

// 函数字面量(function)
function firstFunction( x, y ) {
  return x * y
}
```
--- 
## JavaScript语句
JavaScript语句是发送给浏览器的命令，也就是指定浏览器去做一些事情<br/>
假如我们想让DOM元素变为红色：
```JS
document.querySelector('#test-dom').style.backgroundColor = 'red'
```
_JS代码规范可以写分号 ; 也可以不写，并没有强制的要求_
___
## JavaScript代码块
在我们集中操作一个或者一块的DOM元素，会使用JS代码块形式来进行集中处理一些相关联的操作<br/>
比如用户做出一个操作，可以改变多个DOM元素属性，没有必要分开写多个DOM的操作，那样只会让我们后期重构时徒增困难
<br/>
这时我们可以使用构造函数来将这些动作封装起来-形成一个代码块

```JS
function myFunction () {
  document.querySelector('#test-firstDom').innerHTML = 'Hello World'
  document.querySelector('#test-lastDom').style.color = 'yellow'
}
```
___
## JavaScript变量
我们可以主观认为变量是存储数据的容器，不过这只是让我们便于理解<br/>
其实真正意义上变量是在内存中去帮我们开辟出了一块存储数据的空间，有了这片空间，我们便可以存储数据
![变量](./images/%E5%8F%98%E9%87%8F.png)
当然-我们需要使用这些数据的时候-可以通过变量名来获取修改数据
```JS
let username = "Hello JavaScript"
username = "Hello World"
console.dir(username)
// Hello World
// 一个变量被重新赋值之后，它原有的值会被覆盖掉，JavaScript语句从上往下执行，以最后一次赋值为准
```
***变量命名规范***：
- 建议为字母开头
- 可以是$或者_开头，但是并不建议这么做
- 变量名称对大小写很敏感
- 建议遵守小驼峰命名法
- 建议变量名要有意义
<br/>

***一次性声明多个变量***：
```JS
let username = "Brave-AirPig",
    age = 22,
    hobby = ["敲代码","敲代码"]
```
***一次性给多个变量赋同一个值***：
```JS
let x , y , z = 10
```
这样真的可以实现一次性给多个变量赋同一个值吗？并不可以：
```JS
// undefined  undefined 10
// 在JS语言中是不能这样这样操作的，它会以最后一个变量为准来进行赋值操作
```
___
## ES6新语法let与const
早在2015年之前，JS还在使用var来声明变量
<br/>
在2015年之后一直到今天，JS随着时代不断的进步，ECMAScript版本迭代了很多，以ES6为一个节点，划分出了ES5版本（ES6以下都叫ES5）、ES6版本（ES6以及ES6以上版本都统称为ES6）

- 如今我们常用let来进行变量的声明
- 使用const进行常量的声明（常量即是不可变的）
<br/>

***为什么要使用let和const***？
- ES6之前在JS中使用的var是有一个变量提升的(预编译)
```JS
console.log(a)
var a = 10
// 进行预编译
var a
console.log(a)
a = 10
// 输出结果为undefined-因为声明未赋值
```
- 而let则不会进行预编译
```JS
console.log(a)
let a = 10
// 终端是会报错的-提示我们没有a这个变量
```
- 在块级作用域中let声明的变量是不会被外界访问到的，有效的避免了一些全局变量的污染
```JS
if (true) {
  let a = 10
}
console.log(a)
// 报错：a is not defined

// 我们可以使用var来演示一下：
if (true) {
  var a = 10
}
console.log(a)
// 访问到了10
```
- const声明的是一个常量，数据是不可以更改的
```JS
const a = 10
a = 20
// 报错：Assignment to constant variable
```
---
## 数据类型
JavaScript数据类型分为两大数据类型
- 值类型（原始值）:

***直接表示在语言底层的不可变数据，如果我们对JavaScript中的原始值类型的数据进行了操作，那么它的返回值会是一个新的数据，而不是更改了原始值***
- 引用类型（对象）:将多个属性组合在一起的一个集合
### 值类型：
- Number => 数字型

整型、浮点型、NaN（非数值）、+Infinity无穷大、-Infinity无穷小

>从 ECMAScript 2015 开始，除了 Number.MAX_SAFE_INTEGER 和 Number.MIN_SAFE_INTEGER，你还可以通过 Number.isSafeInteger() 来检查值是否在双精度浮点数的取值范围内-----
超出这个范围，JavaScript 中的整数将不再安全，该值将表示为与该值近似的双精度浮点数。
- BigInt => 基础数值类型

可以表示任意精度的整数，相比于数字类型，BigInt可以有过之而无不及的安全地存储和操作大整数
```JS
// 通过在整数末尾附加字母 n 或调用构造函数我们便可以创建一个BigInt类型数据(BigInt本身不是一个构造函数，我们不能new)
// 但是BigInt类型的数据并不等同于一个数字，如果进行数字间的运算，会抛出 TypeError 数据错误
const bignum = BigInt(Number.MAX_SAFE_INTEGER)
console.log(bignum)
// 9007199254740991n
console.log(2n)
// 2n
console.log(bignum + 1n)
// 9007199254740992n
console.log(bignum + 1)
/* Cannot mix BigInt and other types, use explicit conversions  无法混合BigInt和其他类型，请使用显式转换 */
```

- String => 字符串型

表示文本数据

且字符串是有长度的，长度就是它的字符('元素')的数量

```JS
const str = 'Hello World'
console.log(str.length)
// 11

// 并且还可以使用索对应引来获取到指定字符（'元素'）
console.log(str[0])
// H
```

不过我们需要注意的是 JavaScript 的字符串是不可更改的，一旦被创建就不能被修改，但是可以基于原始值的一些操作创建新的字符串 :
```JS
// 将一个或多个字符串与原始字符串合并，返回一个新的字符串
// str.substring(indexStart[, indexEnd])
// indexStart:填写字符索引，从该索引位置开始截取,之前的不要
// indexEnd:填写字符索引，从该索引位置开始截取,之后的不要

const str = 'Hello JavaScript'
console.log(str.substring(3))
// lo JavaScript
console.log(str.substring(3,8))
// lo Ja

// 它的前身是：substr()不过将来可能会被被舍弃
```
```JS
// 合并字符串 返回一个新字符串 concat() 并且就算不是字符串也会被隐式转换为字符串进行拼接
// str.concat(str2, [, ...strN])
const str = 'Hello'
const str2 = 'World'
console.log(str.concat(str2))
// HelloWorld

// 不过我们立马会想到另一种代替它的方法：使用赋值运算符来代替它
// 性能也必定会强于concat()方法
console.log(str + str2)
// HelloWorld
```

- Boolean => 布尔型【true、false】

_布尔表示一个逻辑实体_
- Null => 空

> _表示不存在亦或者无效对象，东尼·霍尔在1965年发明了空引用，表示一个与[空指针](https://zh.wikipedia.org/wiki/%E7%A9%BA%E6%8C%87%E6%A8%99)类似的概念，是一个已声明但并其未引用到一个有效对象的变量_

我们需要注意一点：JavaScript有自动垃圾回收机制，当我们给变量一个Null值得时候，JavaScript会释放掉该变量的引用，也就是说让变量失去原本的引用，脱离执行环境，这个值会在下一次垃圾回收器执行的时候被找到并释放

- Undefined => 未定义

_声明变量但未赋值的话会有一个默认值undefined_
- [Symbol](https://developer.mozilla.org/zh-CN/docs/Glossary/Symbol) => 符号类型

Symbol类型是唯一且不可修改的动态原始值

常用来解决命名冲突的问题

可以创建匿名的对象属性

Symbol不能和其他数据类型进行运算

Symbol定义的对象属性不能使用for...in来循环遍历--但是我们可以使用Reflect.ownkys来获取对象的所有键名

```JS
// 我始终觉得实践出真知
// 给对象添加Symbol属性：
let testObj = {
  name : "Brave-AirPig",
  [Symbol('say')] : function () {
    console.log('我说了一句话')
  },
  [Symbol('say')] : function () {
    console.log('我又说了一句话')
  }
}
console.log(testObj)

/*  
    {name: 'Brave-AirPig', Symbol(say): ƒ, Symbol(say): ƒ}
    name: "Brave-AirPig"
    Symbol(say): ƒ ()
    Symbol(say): ƒ ()
    [[Prototype]]: Object
*/

// 我们会发现为什么俩个一样的对象属性却没有报错？
// yes-是因为Symbol是唯一的

// 现在有一个对象（假设里面有1万条数据），我想往对象中添加两个属性，我不知道这个对象中有没有我想添加的这俩条数据，那么现在我应该怎么做？

let obj = { name : 'hello' } // 假设有一万条数据

// 1.使用Symbol声明另一个对象
let methods = {
  up : Symbol(),
  down : Symbol()
}

// 2.将这个methods对象的值给到obj对象
obj[ methods.up ] = function () {
  console.log('1')
}
obj[ methods.down ] = function () {
  console.log('2')
}

console.log(obj)
// {name: 'hello', Symbol(): ƒ, Symbol(): ƒ}
```

### 引用类型
- 数组 => Array

数组是一个包含了多个值的对象

我们可以单独访问列表中的每个值，并使用列表执行一些有用和高效的操作
```JS
// 需要注意的是：数组中包含数组的话称之为多维数组，我们可以通过将两组方括号链接在一起来访问数组内的另一个数组
const arr = [1,2,3,[4,5,6]]
console.log(arr[3][2])
// 6

// 获取数组长度：
console.log(arr.length)
// 4

/*******************************************/

// 字符串转换为数组  split()
// 严格来说这是一个字符串的方法
const str = 'Hello,World,Hello,JavaScript'
const arr = str.split( ',' )
console.log( arr )
console.log( arr[2] )
// (4) ['Hello', 'World', 'Hello', 'JavaScript']
// Hello

/*******************************************/

// 数组转换为字符串  join()
const arr = ['Hello', 'World', 1, 2, 3 ]
const str = arr.join( ',' )
console.log( str )
// Hello,World,1,2,3

/*******************************************/

// 数组转换为字符串的另一种方法  toString()
//相比于join()方法，toString()方法不需要参数，当然-就因为它不需要参数，所以在简单的同时失去的自定义分隔符的功能
const arr = [ 'Hello', 'World', 1, 2, 3 ]
const str = arr.toString()
console.log( str )
// // Hello,World,1,2,3

/*******************************************/

// 添加一个或多个数据到数组末尾  push()
// 添加一个或多个数据到数组首位unshift()
const arr = [ 1, 2 ]
const newArr = arr.push( 3, 4 )
console.log( arr )
// (4) [1, 2, 3, 4]

/*******************************************/

// 从数组中删除最后一个元素 pop()
// 从数组中删除第一个元素 shift()
const arr = [ 1, 2 ]
const newArr = arr.pop()
console.log( arr )
// [1]
```

- 对象 => Object

一个 JavaScript 对象就是键和值之间的映射

{ 键是一个字符串（或者 Symbol）: 值可以是任意类型的 }

函数也是一个附带可被调用功能的常规对象
- 函数 => Function

每个函数其实都是一个Function对象

(函数会在之后的内容中详细说明)
- 日期 => Date

JavaScript内置对象
```JS
const nowDate = new Date()
console.log( nowDate )
// Sat May 21 2022 17:31:39 GMT+0800 (中国标准时间)
```

- 正则 => RegExp

将文本与一个模式匹配
(正则会在之后的内容中详细说明)
---
## JavaScript动态类型
- JavaScript语言 是一种弱类型语言 / 或者说是一种动态语言
- 动态语言意味着相同变量可以用作不同的类型，并且我们不用去提前声明变量的类型，在程序运行过程中，类型会被自动确定

我们可以拿Golang来做例子 ：
```golang
// 虽然go语言可以通过类型推导来明确数据类型，同样建议不用提前声明变量数据类型
// 但我觉得go语言可以作为一个例子-因为go语言可以提前声明变量
var str String = "Golang可以提前声明该变量数据类型-就像这样"
```
如果是JavaScript呢？
```JS
let str String = 'JavaScript不用提前声明数据类型-就像这样'
// 报错 Unexpected identifier（意外标识符）
```
相同变量可以用作不同的数据类型实例 :
```JS
let types
// undefined
types = 66
// 66
types = "Hello Brave-AirPig"
// Hello Brave-AirPig
types = ["Hello","World"]
// Array(2) ['Hello', 'World']
types = true
// true
console.log(types)
// true
```
---
### typeof查看数据类型
```JS
const types = Symbol("description")
console.log(typeof types)
// symbol
```
### 创建数组的两种方式
```JS
// 字面量创建
let arr = ['Hello','World']

// 数组对象创建(1)
let arr2 = Array()
arr2[0] = 1
arr2[1] = 2
arr2[2] = 3

// 数组对象创建(2)
let arr3 = new Array('4','5','6')

console.log(arr,arr2,arr3)
/*
(2) ['Hello', 'World']
(3) [1, 2, 3] (3)
['4', '5', '6']
*/

console.log(typeof arr)
console.log(typeof arr2)
// object
// object
```

## 创建对象
```JS
const obj = {
  username : 'Brave-AirPig',
  age : 22,
  hobby : ['敲代码', '敲代码']
}
```
### 获取对象指定属性
```JS
console.log(obj.username)
// Brave-AirPig
console.log(obj['age'])
// 22
console.log(typeof obj['age'])
// number
```
该键值对在对象中是什么数据类型，那么在对象外获取到的还是什么数据类型

## 声明变量类型
```JS
const str = new String('hello')
console.log(str)
/* String {'hello'}
0: "h"
1: "e"
2: "l"
3: "l"
4: "o"
length: 5
*/
// 我们发现，使用字面量创建的String数据打印出来是一个字符串
// 而使用new构造函数创建的String数据打印出来的是一个对象类型的数组
// 我们可以更方便的操作数据

let num = new Number
num = 11
console.log(num)
// 11

const bool = new Boolean(false)
console.log(bool)
// Boolean {false}

// JavaScript 变量均为对象,当我们声明一个变量时，就创建了一个新的对象
```



