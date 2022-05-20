# JavaScript-Useful
## 为什么JavaScript行内样式要写到document底部？
- JavaScript执行机制是从上往下执行的，所以浏览器加载完文档内容（DOM元素）之后再加载JS对DOM元素进行操作
<br/>如果我们将JS放到文档的上面，那么JS找不到对应的DOM元素，也就不能对DOM元素进行操作，并且报错

- 当然，我们可以通过入口函数来解决这个问题:
```JS
//等页面内容全部加载完毕,包括DOM元素、图片、flash、css等才会执行入口函数中的JS代码
window.addEventListener('load',() => {

})
//or
//只要DOM元素加载完毕就会立即执行JS代码
window.addEventListener('DOMContentLoaded',() => {

})
```
--- 
## JavaScript输出语句
```JS
//弹出警告框⚠
window.alert()

//写入浏览器控制台
console.log()
console.dir()

//写入内容到HTML元素内
innerHTML

//写入到HTML文档
//没有什么大用-基本用不到
//如果文档已完成加载 再执行document.write()方法，是会造成页面覆盖的
document.write()
```
--- 
## 字面量
- 字面量是指由字母、数字等构成的字符串或者数值
- 字面量只能作为值出现（键 = 值）
- 它们是你在脚本中字面上写出来的固定的值
- Literals represent values in JavaScript. These are fixed values—not variables—that you literally provide in your script
```JS
//数字字面量(Number)
3.15926   100   -66

//字符串字面量(String)
'Hello'   "World"   'JavaScript'

//表达式字面量
66 * 88   22 + 66

//数组字面量(Array)
[ 30 , 66 , 20 , 100 ]

//对象字面量(Object)
{ username: "Brave-AirPig", age: 22, hobby: [ "敲代码", "敲代码" ] }

//函数字面量(function)
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
[![变量.png](https://s1.ax1x.com/2022/05/20/OLZMuR.png)
***变量命名规范***：
- 必须为字母开头
- 可以是$或者_开头，但是并不建议这么做
- 变量名称对大小写很敏感
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
//undefined  undefined 10
//在JS语言中是不能这样这样操作的，它会以最后一个变量为准来进行赋值操作
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
//进行预编译
var a
console.log(a)
a = 10
//输出结果为undefined-因为声明未赋值
```
- 而let则不会进行预编译
```JS
console.log(a)
let a = 10
//终端是会报错的-提示我们没有a这个变量
```
- 在块级作用域中let声明的变量是不会被外界访问到的，有效的避免了一些全局变量的污染
```JS
if (true) {
  let a = 10
}
console.log(a)
//报错：a is not defined

//我们可以使用var来演示一下：
if (true) {
  var a = 10
}
console.log(a)
//访问到了10
```
- const声明的是一个常量，数据是不可以更改的
```JS
const a = 10
a = 20
//报错：Assignment to constant variable
```




