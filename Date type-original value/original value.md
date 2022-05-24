# JavaScript 原始值数据类型 💎💎
上章我们谈到了值和变量

现在我要说每一种值都有它对应的类型，我们称这种值的类型为 ***数据类型***

我们上一章演示了数字类型和字符串类型，就像这样
```JS
let num = 22
// 22这个值就是数字类型
let str = 'Hello'
// Hello这个值就是字符串类型
```
但我想说不止这俩种数据类型

数据类型可以分为两大类：***对象类型***、***原始值类型***

或许我们可以这样想：如果你在 JavaScript 中定义了一个值，那么它的类型不是对象就是原始值

我们知道就好，现在让我们把关注点集中到原始值数据类型：

---
## 原始值数据类型 📌
原始值数据类型又可以分为7种，我希望你可以记住它们，因为里面会有我们上一章遇到的老朋友：

***数字(Number)、字符串(String)、布尔(Boolean)、未定义(Undefined)、空值(Null)、唯一标志(Symbol)、大整数(BigInt)***

1. ***Number***:它包含了整数以及浮点数( _浮点数就是带小数点的数字_ )，或者我们可以理解为 Number 就是代表浮点数，因为在 JavaScript 中哪怕你定义了一个 6 ，它的真实的值为 6.0

2. ***String***:使用引号包裹起来的字符集合，在引号中你可以随意写些什么，这个整体称为字符串，或许你可以理解为将字符像羊肉串一样串起来，OK，我想我已经开始饿了

3. ***Boolean***:布尔类型本质上是一种逻辑类型，它不像其它数据类型可以随意的书写你希望看到的值，它只有`true` or `false` 这俩个值，意味着你只能二选一，在之后的学习中，我们会大量使用到他进行一些判断

***到这里我想暂停一下,因为这是最重要的三种数据类型，我希望你可以掌握它们，我并没有说接下来的四种不重要，请不要误会我***

4. ***Undefined***:这个数据类型我更想称它为一个值，因为你会在之后的编程旅行中不断的在 console 中看到它，它代表声明但是没有赋值，就像这样：
```JS
// 声明了一个变量str
let str
// 我们想在控制台中将它打印出来
console.log(str)

// stop！我们好像并没有给到 str 一个值，可能现在来不及了
// undefined

// 为什么我们没有给值会看到一个undefined？
// 当我们去声明这样的空变量的时候，它会去自动保存 undefined 值，我们可以认为 undefined 他就是一个值
```
还有一种情况，我们可能连变量都忘记声明了
```JS
console.log(num)
// undefined
```
可能我们在之后的学习中会碰到很多 undefined 情况，不要担心，我们只需要记住上面的定义就好了，我相信你可以独立去处理这些问题

5. ***Null***:与 undefined 类似还有一种 Null 类型,它代表一个空的值（ _JavaScript 有自动垃圾回收机制，我希望你可以作为一个了解,也就是当这个变量为 Null 的时候，下次执行程序会自动的将这个变量删除掉，不会让空值占用我们的内存，也许现在我们不能够理解，不要担心，当学习完这个仓库，你一定会理解它的_ ）
6. ***Symbol***:唯一标志并不是官方定义的名称，大家都喜欢叫他为符号类型，而我更喜欢称它为 ***唯一标识数据类型*** 因为这和它的功能有关;这个数据类型是 ES6 新增的，它用来定义一个唯一的值，并且无法更改，请不要纠结于理解这些，它并不常用，如果在之后的学习中使用到了它，我会再次做一个详细的解释，相信那时你会豁然开朗
7. ***BigInt***:大整数数据类型是 ES2020 新增的，它用来表示非常大的整数，我们在之后会谈到它

***Now，让我们休息一下，我们已经学完7种数据类型了，休息期间，请允许我们讲述一个知识点 -- 关于 JavaScript 动态类型的特性*** 💤

- JavaScript 动态类型意味着我们定义一个变量的时候不需要去指定数据类型，在很多编程语言中都是需要指定数据类型的，当然也有 ***无所谓*** 的，比如 Golang这门编程语言 :

```Golang
var test String = "字符型"
// 声明一个名为 test 且数据类型为 String 的变量
var test = "字符型"
// 这两种声明方式都 OK

// Golang 语言可以通过类型推导来明确数据类型，同样建议不用提前声明变量数据类型

// OK，很抱歉打断你，请不要忘记现在是休息时间，我只是在讲一个故事，你无需在意 Golang 是什么
```
如果是 JavaScript 呢？
```JS
let test = '正确方式'、
// 正确方式

// 如果你非要加数据类型的话 ：
let test String = "错误方式"
// 语法错误：Uncaught SyntaxError: Unexpected identifier（意外标识符）
```
我们不用去提前声明变量的类型,类型会被自动确定

***我们需要知道 JavaScript 中声明的值是具有类型的值，不要理解为已经声明了一个变量，变量只存储具有类型的值***，希望你可以认真阅读这句话，这个细节很多人都会忽略掉,下面的代码会帮助你理解
```JS
666 //看似这是一个普通的数字，但是在JavaScript中，他已经被赋予为数值型

let num = 666 //这个666的数值型数据赋值给变量num
//如果666在某一些语言中，它是不能被赋值给变量的，因为变量只接受具有类型的值
```

***OK--休息时间到了，我们现在来看一下 JavaScript 动态类型第二个重点：相同变量可以用作不同的类型***

在我们的代码后面，我们可以分配一个新值来看看会发生什么？
```JS
// 首先我们声明了一个新变量叫做 types
let types
console.log(types)
// undefined

// 在这里我们改变了 types 变量中值的数据
types = 66
console.log(types)
// 66

// 在这里我们再次改变了 types 变量中值的数据
types = 'Hello'
// 最终 types 的值为 Hello
console.log(types)
// Hello

// JavaScript 不会报错，这是正常的，这是JavaScript动态类型的特点

// 就像一个盒子一开始里面什么都没有，我们放进去了一个 66，然后再次把 66 取出来，放进去了 Hello，当最后你去查看盒子里面的物品，你会发现只有 Hello

// 但是我们一定要注意！！它实际上并没有去创建一个新的变量，而分配了一个新值，这点很重要
```
这些动态类型特性奠定了 JavaScript语言 是一种弱类型语言 / 或者说是一种动态语言

***我们再来学习一个叫做 typeof 的运算符，和+（加）、-（减）、*（乘）、/（除） 一样;它的功能是查看一个值的数据类型** 💾

从以上的介绍来看，我们知道typeof的类型是运算符类型（ _请不要与以上7种数据类型混为一谈, 哪怕听起来很像_ ）

OK -- 我真的够啰嗦了，让我们一起来看看它怎么使用
```JS
// 使用console.log  -我们想在控制台中看到此运算符运行的结果
console.log(typeof true)
console.log(typeof 'Hello')
let test = 'JavaScript'
console.log(typeof test)

// boolean
// string
// string

// 如果我们这样书写字符串呢 ？
console.log(typeof Hello)
// undefined
// 如果你不给字符串引号包裹的话，JavaScript会把 Hello 当成一个变量去寻找，但是并没有寻找到，所以打印出了 undefined
```

---
## 结束 🎏
接下来让我们进入本章的尾声，我想说一说 undefined 的"兄弟" null 

null也是没有值的意思，代表空，它与 undefined 不同之处在于数据类型
```JS
console.log(typeof null)
// 控制台打印出：object（对象）
```
这并没有意义，它被认为是 JavaScript 中的一种错误，关于它的说法有很多，当然在之后我会再次说到它，但是本章到这里结束了






