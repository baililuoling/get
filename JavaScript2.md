# JavaScript

## day21-day24

#### cookie

* cookie是每个客户身份的通行证，相当于一个身份证
* php里面有一个变量叫$_COOKIE可以获取cookie数组
* cookie的特点:
  * 大小有限制:4K左右
  * 条数有限制:50条左右
  * 读取有限制:同域读取，不可跨域读取，只能由来自写入cookie的同一域名的网页可进行读取
  * 时效有限制:每个cookie都有时效，最短的有效期是，会话级别：就是当浏览器关闭，那么cookie立即销毁，如果没有指定Cookie的时效，那么默认的时效是：会话级别

```js
//获取cookie
var str = document.cookie;//所有的当前域下的cookie,是字符串格式
//设置cookie
var username = 'guan';
var date = new Date();
date.setDate(date.getDate()+1);//设置时间1天后过期
document.cookie = `username=${username};expires=${date.toString()}`;//js写入cookie
//删除cookie,将过期时间设置成当前时间之前即可

//封装三个操作cookie的方法
//方法一:设置cookie
function setCookie(key,value,day){
  var date = new Date();
  date.setDate(date.getDate()+day);
  document.cookie = key+"="+value+";expires="+date.toString();//js写入cookie
}
//方法二:删除cookie
function removeCookie(key){
  setCookie(key,-1,-1);
}
//方法三:获取cookie
function getCookie(key){
  var str = document.cookie;//所有的当前域下的cookie,是字符串格式
  //字符串转数组格式
  var arr = str.split('; ');
  for(var i=0;i<arr.length;i++){
    var newArr = arr[i].split('=');
    if(newArr[0]==key){
      return newArr[1];
    }			
  }
}
```

#### localStroage/sessionStorage

* 浏览器的大小不统一，并且在IE8以上的IE版本才支持localStorage这个属性
* 目前所有的浏览器中都会把localStorage的值类型限定为string类型，这个在对我们日常比较常见的JSON对象类型需要一些转换	
* localStorage在浏览器的隐私模式下面是不可读取的	
* localStorage本质上是对字符串的读取，如果存储内容多的话会消耗内存空间，会导致页面变卡	
* localStorage不能被爬虫抓取到
* localStroage和sessionStorage区别是前者如果不人为删除则永久保存，后者是浏览器关闭后数据会被清除

```js
//记事本里面键和值都是字符串类型
//设置键值对
localStorage.username = "zhangsan";
localStorage.setItem('username','zhangsan')
//获取指定键对应的值
localStorage.getItem('username')
//删除指定键值对
localStorage.removeItem("name")
//删除所有键值对
localStorage.clear()
//获取指定下标的键
localStorage.key(0)
//storage事件
window.addEventListener('storage',function(){
  document.body.style.background = localStorage.color;
})
```

#### 中文防抖

```js
dom.addEventListener('compositionstart',function(){
  console.log('正在输入拼音')
})
dom.addEventListener('compositionend',function(){
  console.log('拼音输入完成')
})
```

#### Promise异步执行

```js
//只要实例化就会执行
var bool=true;
new Promise((resolve,reject)=>{
  var a = 1;
  if(bool){
    resolve(a)
  }else{
    reject(a)
  }
}).then((a)=>{
  console.log('我执行了resolve函数',a)
  return new Promise((resolve,reject)=>{
    if(bool){
      resolve(a)
    }else{
      reject(a)
    }
  })
},(a)=>{
  console.log('我执行了reject函数',a)
}).then((a)=>{
  console.log('第二次resolve函数',a)
},(a)=>{
  console.log('第二次reject函数',a)
})
//示例
var promise = new Promise(function(resolve,reject){
  setTimeout(function(){
    var a = Math.random();
    if(a>0.5){
      resolve(a);
    }else{
      reject(a);
    }
  },3000)
});//promise可以看做一个容器,里面放着一个将来会完成的事情
promise
.then(function(a){
  console.log('我执行了resolve函数,a的值是'+a);
  return new Promise(function(resolve,reject){
    setTimeout(function(){
      resolve("我是第二次prmose的回调函数")
    },5000)
  })
},function(a){
  console.log('我执行了reject函数,a的值是'+a)
})
.then(function(text){
  console.log(text)
},function(){
  console.log(2)
})

//错误捕捉1
var promise = new Promise(function(resolve,reject){
  var str = "abc";
  var result = JSON.parse(str);
})
promise.catch(function(e){
  console.log(e)
})
//错误捕捉2
try{
  var str = "abc";
  var result = JSON.parse(str);
}
catch(e){
  console.log(e)
}
```

## day25 bootstrap

## day26

#### 闭包

```js
//局部变量不能再函数外部访问
function fn(){
  //a 是函数fn内部的局部变量,只能在fn中访问
  var a = 1;

}
fn();
// console.log(a);//a is not defined,不能在函数外部访问

//需求:希望在函数外部能够访问a,并能够修改该变量的值
//方法一:通过return可以获取函数的返回值,但是不能修改返回值
function fn1(){		
  //在fn1执行的时候,创建一个内容空间b,赋值11,然后把空间b的值取出返回,因为后面不在使用到b,所以函数执行完成后释放b空间.
  var b = 11;
  return b;
  
}
var b = fn1();
console.log(b);
//方法二:在函数fn2里面定义一个局部变量c,然后返回一个可以操作c的函数,这样通过这个返回值,就可以操作函数fn2里面的变量c,这就是闭包.
//特点:函数内变量长期保存在内存中,容易导致内存泄漏,在函数外部可以访问函数内部变量,节约命名空间

function fn2(){
  var c = 2;
  var a = 1;
  var b = 3;
  return function(){
    c++;	
    a*=2;
    b+=4;
    console.log("c的值是"+c)		
    console.log("b的值是"+b)		
    console.log("a的值是"+a)		
  }
}
var result = fn2();
console.log(result);
result()
result()

var dd = (function(){
  var a = document.body;			
  function bb(){			
    a.style.background = "red";
  };
  return function aa(){						
    document.body.onclick = bb;
  }

})()
dd();
```

#### call,apply,bind

* fn.call():改变this指向并执行，仅本次调用,第一个参数是改变后的this指向，第二个参数以后都是要传的参数
* fn.apply():改变this指向并执行，仅本次调用,第一个参数是改变后的this指向，第二个参数是以数组的形式传参
* fn.bind():改变this指向，不执行

#### 构造函数和原型

```js
function Human(name,age){
  this.name = name;
  this.age = age;
  // this.sayName = function(){
  // 	console.log('my name is '+this.name)
  // };
  // this.sayAge = function(){
  // 	console.log('I am '+this.age)
  // }
}
Human.prototype.sayName = function(){
  console.log('my name is '+this.name)
}
Human.prototype.sayAge = function(){
  console.log('I am '+this.age)
}
var h1 = new Human('李四',12);
var h2 = new Human('张三',11);

//实例对象的__proto__指向构造函数的原型
console.log(h1.__proto__==Human.prototype);//true
console.log(h2.__proto__==Human.prototype);//true
console.log(h1.sayName==h2.sayName);//true
console.log(h1.sayAge==h2.sayAge);//true

//实例对象的__proto__上的所有属性和方法都可以被实例对象直接使用
h1.sayName();

// console.dir(Human);
```

#### 原型

```js
function Human(name,age){
  this.name = name;
  this.age = age;
}

//构造函数的天生原型上有一个coustructor属性,指向该构造函数
console.log(Human.prototype.constructor==Human);
Human.prototype.sayName = function(){
  console.log(this);
}
//实例对象
var h1 = new Human('lisi',12)
var h2 = new Human('zhangsan',23)
//实例对象的__proto__指向其构造函数的原型
console.log(h1.__proto__==Human.prototype);//true
console.log(Human.prototype==h2.__proto__);//true
//实例对象的__proto__上的键值对都是实例对象的
h1.sayName();

//系统定义的构造函数有:Array,Function,Object,RegExp,Promise,Set,Date
console.log(Human.prototype.__proto__==Object.prototype);//true
console.log(Object.prototype);
//我来写一个链条,箭头的含义是__proto__,这个就是原型链
//h1---->Human.prototype---->Object.prototype---->null
```

#### 原型链

```js
var arr = [1,3,3,2,3];
//arr的原型链
//arr--->Array.prototype--->Object.prototype--->null
console.log(arr.__proto__==Array.prototype);//true
console.log(Array.prototype.__proto__==Object.prototype);//true
console.log(Object.prototype.__proto__);//null

var date = new Date();
console.dir(date)
//date的原型链
//date --->Date.prototype--->Object.prototype--->null

console.log(arr.toString());
console.log(typeof arr);//object
console.log(Object.prototype.toString.call(date));//[object Date] 精确判断数据类型
```

#### 通过原型链实现继承

```js
//arr--->Array.prototype--->Object.prototype---->null
//str--->String.prototype--->Object.prototype---->null
//date--->Date.prototype--->Object.prototype---->null
//regExp--->RegExp.prototype--->Object.prototype---->null

function Human(name,age){
  this.name = name;
  this.age = age;
}
Human.prototype.sayAge = function(){
  console.log(this.age)
}
var h1 = new Human('lisi',12);
//h1-->Human.prototype--->Object.prototype-->null
console.dir(h1)

function Student(banji,score){
  this.banji = banji;
  this.score = score;
}
Student.prototype = h1;
Student.prototype.sayScore = function(){
  console.log(this.score)
}

var s1 = new Student('1916',80);
var s2 = new Student('1917',90);
//通过原型链实现了继承:我现在有四个属性:banji,score,name,age
//s1--->h1--->Human.prototype--->Object.prototype--->null
console.log(s1)
console.log(s2)
```

#### 借用构造函数

```js
function Human(name,age){
  this.name = name;
  this.age = age;
}
Human.prototype.sayAge = function(){
  console.log(this.age)
}

function Student(banji,score,name,age){
  Human.call(this,name,age)
  this.banji = banji;
  this.score = score;
}	
Student.prototype.sayScore = function(){
  console.log(this.score)
}

var s1 = new Student('1916',50,'李四',34);
console.dir(s1)
```

#### 组合继承

```js
function Human(name,age){
  this.name = name;
  this.age = age;
}
Human.prototype.sayAge = function(){
  console.log(this.age)
}
var h1 = new Human('lisi',12);

function Student(banji,score,name,age){
  Human.call(this,name,age)
  this.banji = banji;
  this.score = score;
}
Student.prototype = h1;
Student.prototype.sayScore = function(){
  console.log(this.score)
}

var s1 = new Student('1916',80,'zhangsan',12);
console.dir(s1);//原型prototype给开发者编程使用
```

#### es6继承语法

```js
class Human{
  constructor(name,age){
    this.name = name;
    this.age = age;
  }
  sayAge(){
    console.log(this.age)
  }
}

class Student extends Human{
  constructor(banji,score,name,age){
    super(name,age)
    this.banji = banji;
    this.score = score;
  }
  sayScore(){
    console.log(this.score)
  }
}
var s1 = new Student('1917',23,'wangwu',45)
console.dir(s1)
```

#### status

```js
//改变浏览器状态栏
window.status = "hello";
```

## day27

## day28

#### 属性判断

```js
function Human(name,age){
  this.name = name;
  this.age = age;
}
var h1 = new Human('lisi',34)
function Student(banji,score){
  this.banji = banji;
  this.score = score;
}
Student.prototype = h1;
var s1 = new Student('1916',78);
//s1-->h1--->Human.prototype--->Object.prototype--->null
console.dir(s1);
//属性判断
//方法一:in
console.log('banji' in s1);//banji是否是s1对象的属性 true
console.log('age' in s1);//age是否是s1对象的属性 true
console.log('hasOwnProperty' in s1);//hasOwnProperty是否是s1对象的属性 true
//方法二:hasOwnProperty
console.log(s1.hasOwnProperty('age'))//判断age是否是s1本身的属性 false
console.log(s1.hasOwnProperty('banji'))//判断banji是否是s1本身的属性 true
//区别:in判断的属性不管是自己身上还是原型链身上都算true,hasOwnProperty只有等属性是对象本身上的才是true

//需求:封装一个方法,判断某个属性是否是某个对象的原型链上的属性
function isProperty(attr,obj){
  if((attr in obj)&&(!obj.hasOwnProperty(attr))){
    console.log(attr+"是原型链上的属性")
    return true
  }
  console.log(attr+"不是原型链上的属性")
  return false;
  
}
isProperty('age',s1)
```

#### 实例判断

```js
function Human(name,age){
  this.name = name;
  this.age = age;
}
var h1 = new Human('lisi',34)
function Student(banji,score){
  //借用构造函数继承:call,apply,bind		
  this.banji = banji;
  this.score = score;
}
Student.prototype = h1;
var s1 = new Student('1916',78);
//s1-->h1--->Human.prototype--->Object.prototype--->null
console.log(s1 instanceof Student);//true
console.log(s1 instanceof Human);//true
console.log(s1 instanceof Object);//true


var arr = [132,3,4,4,2,3];
console.log("================数组的原型链================")
//arr--->Array.prototype--->Object.prototype--->null
console.log(arr instanceof Array);//true
console.log(arr instanceof Object);//true
console.log(arr instanceof Function);//false
console.log(arr instanceof Human);//false

console.log("===============函数的原型链================")
//Human---->Function.prototype---->Object.prototype---->null
console.log(Human instanceof Object);//true
console.log(Human instanceof Student);//false
console.log(Human instanceof Function);//true
```

#### defineProperty

```js
var obj = {
  a:1,
  b:2
};

//obj--->Object.prototype---->null
console.dir(obj);
// Object.defineProperty:定义对象的属性
// Object.defineProperty(obj,'c',{		
// 	value:5,
// 	writable:true
// })
Object.defineProperty(obj,'c',{
  get:function(){
    //观察者模式,观测获取值
    console.log('你获取了值')
    return 6;
  },
  set:function(){
    //观察者模式,观测设置值
    console.log("你设置了值")
  }
})
obj.c = 4;
console.log(obj.c)
//遍历对象
// for(var key in obj){
// 	console.log(key)
// }
```

#### Object.assign

```js
var obj1 = {
  a:[1],
  b:2
}
var obj2 = {
  c:4,
  a:[2]
}
// var obj = {...obj1,...obj2};
var obj = Object.assign(obj2,obj1)//获取两个对象合并后的对象，键有重复则后者覆盖前者

console.log(obj);
```

## day29-day30 JQuery

## day31 echarts swiper template-web

## day32 nodejs

## day33 gulp AMD commonjs es6module

## day34 sass 百度地图

## day35 git

