#### 1.闭包
闭包就是能够读取其他函数内部变量的函数

闭包是指有权访问另一个函数作用域中变量的函数，创建闭包的最常见的方式就是在一个函数内创建另一个函数，通过另一个函数访问这个函数的局部变量,利用闭包可以突破作用链域

闭包的特性：

函数内再嵌套函数
内部函数可以引用外层的参数和变量
参数和变量不会被垃圾回收机制回收
说说你对闭包的理解

使用闭包主要是为了设计私有的方法和变量。闭包的优点是可以避免全局变量的污染，缺点是闭包会常驻内存，会增大内存使用量，使用不当很容易造成内存泄露。在js中，函数即闭包，只有函数才会产生作用域的概念

闭包 的最大用处有两个，一个是可以读取函数内部的变量，另一个就是让这些变量始终保持在内存中

闭包的另一个用处，是封装对象的私有属性和私有方法

好处：能够实现封装和缓存等；

坏处：就是消耗内存、不正当使用会造成内存溢出的问题

使用闭包的注意点

由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题，在IE中可能导致内存泄露
解决方法是，在退出函数之前，将不使用的局部变量全部删除

### 2.JavaScript原型，原型链 ? 有什么特点？
每个对象都会在其内部初始化一个属性，就是prototype(原型)，当我们访问一个对象的属性时

如果这个对象内部不存在这个属性，那么他就会去prototype里找这个属性，这个prototype又会有自己的prototype，于是就这样一直找下去，也就是我们平时所说的原型链的概念

关系：instance.constructor.prototype = instance.__proto__

特点：

JavaScript对象是通过引用来传递的，我们创建的每个新对象实体中并没有一份属于自己的原型副本。当我们修改原型时，与之相关的对象也会继承这一改变
当我们需要一个属性的时，Javascript引擎会先看当前对象中是否有这个属性， 如果没有的

就会查找他的Prototype对象是否有这个属性，如此递推下去，一直检索到 Object 内建对象

### 3.Javascript如何实现继承？
构造继承

原型继承

实例继承

拷贝继承

原型prototype机制或apply和call方法去实现较简单，建议使用构造函数与原型混合方式
```js
function Parent(){
	this.name = 'wang';
}

function Child(){
        this.age = 28;
}
    
Child.prototype = new Parent();//继承了Parent，通过原型

var demo = new Child();
alert(demo.age);
alert(demo.name);//得到被继承的属性
```

###  4.this指向问题
普通函数和全局中指向window,严格模式下是undefined
构造函数中指向实例化对象
事件函数中指向函数的直接调用者
定时器中指向window,严格模式下是undefined
严格模式下，禁止this指向全局对象

### 5.异步编程的实现方式
回调函数

优点：简单、容易理解
缺点：不利于维护，代码耦合高
事件监听(采用时间驱动模式，取决于某个事件是否发生)：

优点：容易理解，可以绑定多个事件，每个事件可以指定多个回调函数
缺点：事件驱动型，流程不够清晰
发布/订阅(观察者模式)

类似于事件监听，但是可以通过‘消息中心’，了解现在有多少发布者，多少订阅者
Promise对象

优点：可以利用then方法，进行链式写法；可以书写错误时的回调函数；
缺点：编写和理解，相对比较难
Generator函数

优点：函数体内外的数据交换、错误处理机制
缺点：流程管理不方便
async函数

优点：内置执行器、更好的语义、更广的适用性、返回的是Promise、结构清晰。
缺点：错误处理机制

### 6.深浅拷贝
浅拷贝

Object.assign
或者展开运算符

深拷贝

//immutable
递归
可以通过 JSON.parse(JSON.stringify(object)) 来解决
```js
let a = {
    age: 1,
    jobs: {
        first: 'FE'
    }
}
let b = JSON.parse(JSON.stringify(a))
a.jobs.first = 'native'
console.log(b.jobs.first) // FE
```
该方法也是有局限性的

会忽略 undefined
不能序列化函数
不能解决循环引用的对象

### new 做了什么?

new 开辟一块内存空间
空间地址赋给this
给this添加属性和方法
把this返回

### react生命周期

挂载阶段四个钩子函数的执行次序
  a.constructor(props,context)
  b. getDerivedStateFromProps(props,state)
  c.render
  d.componentDidMount
5.卸载阶段的钩子函数只有一个
  componentWillUnmount
6.更新阶段的钩子函数
  a.shouldComponentUpdate(nextProps,nextState)
    返回true 就会render
    返回false 不回render 
 可以加条件减少不必要的渲染，增加性能

 PureComponent 进行浅比对，进行性能的优化 （纯组件）

 对无状态组件用 React.memo(组件)

 我们把 参数是组件 返回值也是组件 这类组件我们叫 "高阶组件"(HOC)
 本质是高阶函数 （map filter forEach ....)

 b.    getSnapshotBeforeUpdate(prevProps,prevState)
        必须和componentDidUpdate一起用
        必须返回一个值
        不能和旧版的钩子函数一起使用
        目的是为了返回数据更新前的dom状态
 c. componentDidUpdate(prevProps,prevState,snapshot)
 
 # vue

#### 5、虚拟DOM

* 什么是MVP、MVC、MVVM模式？
	* M  model数据
	* V  view视图
	* C  control控制器
* 如何理解MVVM？
	* VM 即视图模型，你可以理解为虚拟DOM
* 什么是虚拟DOM？
	虚拟DOM就是一个json对象，它用于对真实DOM进行描述。
* 什么是diff运算？
	当Vue实例中的数据发生变化时，Vue会获得一份对虚拟DOM的拷贝，如此我们就有两份虚拟DOM，一份是数据变化前的虚拟DOM，一份是数据变化后的虚拟DOM。所谓的Diff运算，就是对这两份虚拟DOM进行差异比较，从而找出它们的最小差异。再把这份最小的差异渲染到真实DOM中去。
	MVVM框架，基于这种虚拟DOM的Diff运算，大大地减少了DOM的频繁操作，减少DOM操作本身就是一种性能优化。所以MVVM框架有利于性能优化，非常适合数据化的产品应用开发。
  
# 面试题

1. 异步转同步

回调
async await

2. 判断数据类型



