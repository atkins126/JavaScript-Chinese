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