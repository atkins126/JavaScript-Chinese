## JavaScript变量
我们可以主观认为变量是存储数据的容器，不过这只是让我们便于理解<br/>
其实真正意义上变量是在内存中去帮我们开辟出了一块存储数据的空间，有了这片空间，我们便可以存储数据

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
