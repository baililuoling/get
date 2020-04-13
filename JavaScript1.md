# JavaScript

## day01

#### js输出

```js
window.alert("这是弹窗");
console.log("这是在控制台输出的普通内容");
console.warn("这是在控制台输出的警告内容");
console.error("这是在控制台输出的错误内容");
document.write("<p>hello,world</p>","这是文档输出")
```

#### js的组成

* html5:
* css3:
* js的组成:
* ecmascript
* BOM:浏览器对象模型
* DOM:文档对象模型

#### BOM体验

```js
window.alert(1);     //弹窗
window.location.href = "https://www.baidu.com";   //将网页跳转到百度
```

#### 变量的概念

```js
//声明一个变量,用关键字var 空格 变量名=变量值;
var pai = 3.1415926;
var a = 2;
//声明一个变量b
var b;
//该变量b赋值
b = 3;
//在控制台输出
console.log(b)
```

#### 变量的定义

```js
//变量的声明
var a;
//变量的赋值
a = 2;
//变量声明同时赋值
var b = 3;
//同时声明多个变量
// var c;
// var d;
// var e;
var c,d,e;
//同时声明多个变量并赋值
// var c;
// var d = 2;
// var e = 4;
var c,d=2,e=4;
//如何取变量名
/*
规则(必须遵守,不遵守就会报错):
  1 不能使用系统的关键字和保留字
  2 包含字母,数字,下划线_,$,不能以数字开头
  3 区分大小写
规范(最好遵守):
  1 驼峰命名
  2 尽量语义化
*/
var name = 1;
console.log(name)
```

#### 数值类型

```js
//强类型语言 java
//弱类型语言 javascript	
//数值型:Number类型
var container = 1;//字面量是数字,十进制
console.log(container);//数字类型一般是蓝色
//十进制,十六进制,八进制
var num1 = 0x1D;//该数字是十六进制
// 0 1 2 3 4 5 6 7 8 9 A B C D E F
console.log(num1);
var num2 = 012;
console.log(num2);
```

#### 字符串类型

```js
//字符串类型:"",'',控制台输出黑色
var str = "hello,world";
var str1 = 'hello';
//我是一个"正直"的人 
var str2 = '我是一个\"正直\"的人';
//我很喜欢"千峰'程序猿'",转义就是前面加\
var str3 = '我很喜欢\"千峰\'程序猿\'\"';
var str4 = '4';
console.log(str.length);//字符串变量.length,可以得到字符串的长度
```

#### 布尔类型

```js
var bool = true;
var bool2 = false;
```

#### undefined和null

```js
var a; //一个变量声明了,但是没有赋值,就是undefined类型
console.log(a);

var b = null;//空
console.log(b);


//简单数据类型:
//1 字符串string类型:字母量有引号包裹
//2 数值number类型:字面量是数字
//3 布尔boolean类型:字母量是true或false
//4 未定义undefined类型:一个变量声明了,但是没有赋值
//5 null类型:字面量为null
```

#### 获取数据类型

```js
var a = 132;
var b = "34";
var c = true;
var d = null;
var e;
console.log(typeof a);  //number
console.log(typeof b);  //string
console.log(typeof c);  //boolean
console.log(typeof d);  //object
console.log(typeof e);  //undefined
```

#### 转成字符串类型

```js
var a = 15;
//方法一:变量.toString(),不适用于undefined和null
console.log(a.toString());  //15
//toString()内可以写数字来转进制,例
console.log(a.toString(16));  //转成16进制输出e
//方法二:String(),适用于undefined和null
console.log(String(a));    //15
//方法三:隐式
var d = a+"";//+一方只要有一个是字符串就是拼接的意思
console.log(d)
```

#### 转成数值类型

```js
var a;
var b = null;
var c = "132.12abc";
var d = "123"
var e = true;
console.log("=========方法一Number=======")
//方法一:Number():可以把任意的数据类型转成number类型;null转成0,true转成1,false转成0,要转的内容中只要有一个是非数字,就会转成NaN	
console.log(Number(a));//NaN
console.log(Number(b));//0
console.log(Number(c));//NaN
console.log(Number(d));//123
console.log(Number(e));//1
console.log("=========方法二parseInt=======")
//方法二:parseInt():可以把任意的数据类型转成number的整数类型:从第一个数字开始转,一直到第一个非数字的整数
console.log(parseInt(a));//NaN
console.log(parseInt(b));//NaN
console.log(parseInt(c));//132
console.log(parseInt(d));//123
console.log(parseInt(e));//NaN
console.log("=========方法三parseFloat=======")
//方法三:parseFloat()可以把任意的数据类型转成number的小数类型:从第一个数字开始转,一直到第一个非数字的整数
console.log(parseFloat(a));//NaN
console.log(parseFloat(b));//NaN
console.log(parseFloat(c));//132.12
console.log(parseFloat(d));//123
console.log(parseFloat(e));//NaN
//方法四:隐式
console.log("=========方法四隐式=======")
var num = -(-d);
num = +d;
num = d*1;
num = d/1;
console.log(num)
```

#### 转布尔类型

```js
var a=NaN,b="",c,d=null,e=0;
//转布尔类型Boolean():true,false
console.log(Boolean(a));//a = NaN,结果是false
console.log(Boolean(b));//b = "",结果是false
console.log(Boolean(c));//c = undefined,结果是false
console.log(Boolean(d));//d = null,结果是false
console.log(Boolean(e));//e = 0,结果是false
//false:0,undefined,null,"",false,NaN
console.log(Boolean('0'));//true
```

#### 表达式

```js
//js不擅长小数操作
var a=3,b=34;
//表达式:操作数和操作符(运算符),一定会有一个结果
console.log(a+b);//+:可能是正号,加法或者拼接
console.log(a-b);//-:可能是负号或者减法
console.log(a*b)
console.log(b/a);
console.log(b%a);//b除以a的余数
```

#### 比较运算符

```js
//比较运算符的结果是布尔值
console.log("34">34);//false
console.log("34">=34);//true
console.log("34"<34);//false
console.log("34"<=34);//true
console.log("34"==34);//true,只判断值
console.log("34"!=34);//false,只判断值
console.log("34"===34);//false,既判断值也判断数据类型
console.log("34"!==34);//true,既判断值也判断数据类型
console.log("==============");
console.log(0==false);//true
console.log(0===false);//false
console.log(1==true)//true
console.log(1===true)//false
console.log(NaN===NaN)//false
console.log(NaN==NaN)//false
console.log(NaN<=NaN)//false
console.log(NaN>=NaN)//false
console.log(NaN!=NaN)//true
```

#### 赋值运算符

```js
var a = 1;
//一个等号是赋值
// a = a +3等价于a += 3;
// a = a * 5等价于a *= 5;
// a = a-10等价于a -=10;
// a = a/10等价于a /=10;
```

#### 一元运算符

```js
var a = 20;
// a++;//就是在a的基础上加1
// ++a;//就是在a的基础上加1
// a--;//就是在a的基础上减1
// --a;//就是在a的基础上减1
console.log(a--); //20
//先获取打印a的值,然后a在a的基础上加1  20  a++
//现在a的基础上加1,再获取a的值进行打印 21  ++a
var a = 1; var b = ++a + ++a; console.log(b); //2 + 3 = 5
var a = 1; var b = a++ + ++a; console.log(b); //1 + 3 = 4
var a = 1; var b = a++ + a++; console.log(b); //1 + 2 = 3
var a = 1; var b = ++a + a++; console.log(b); //2 + 2 = 4
```

#### 逻辑运算符

```js
//与&& 两个条件同时满足,才为真,一假全假
//或|| 满足任意一个条件,即为真,一真全真
//非! 取反,答案一定是布尔值

console.log(11<12&&23>12);//true
console.log(11>12||23>12);//true
console.log(!9);//false
```

#### 保留小数

```js
var a = 26.66666666
//保留3位小数
//方法一
console.log(parseInt(a*1000)/1000)  //26.666
//方法二
console.log(a.toFixed(3))  //26.667
```

## day02

#### 运算符的优先级

```js
/*
	优先级从高到底
    1. ()  优先级最高
    2. 一元运算符  ++   --   !
    3. 算数运算符  先*  /  %   后 +   -
    4. 关系运算符  >   >=   <   <=
    5. 相等运算符   ==   !=    ===    !==
    6. 逻辑运算符 先&&   后||
    7. 赋值运算符
*/

console.log(4 >= 6 || '人' != '阿凡达' && !(12 * 2 == 144) && true) //true
console.log(5 == 10 / 2 && (2 + 2 * 10).toString() === '22') //true
```

#### 逻辑运算符

```js
//&&  
//如果全为真,就取最后一个为真的
//如果有一个为假,就去第一个为假的值
console.log(1>0&&2<1);//false
console.log(1&&2);//2
console.log(3&&1>0);//true
console.log(3&&1<0);//false
console.log(1&&"");//""
console.log(1&&NaN);//NaN
console.log(NaN&&null);//NaN
console.log("0"&&undefined);//undefined
console.log("=================================")
//||
//如果有一个为真,就取第一个为真的
//如果都为假,就取最后一个为假的
console.log(1>0||2<1);//true
console.log(1||2);//1
console.log(3||1>0);//3
console.log(3||1<0);//3
console.log(1||"");//1
console.log(1||NaN);//1
console.log(NaN||null);//null
console.log("0"||undefined);//"0"
```

#### 语句

```js
//表达式:一定返回值
//语句:行为
//程序由语句构成:
//结构:自上而下顺序执行
var a = 1;
var b = 2;
```

#### if语句

```js
if(/*判断条件1*/){
  /*如果条件1为真,就执行此处*/
}else if(/*判断条件2*/){
  /*如果条件2为真,就执行此处*/
}else{
  /*如果条件2为假,就执行此处*/
}
```

#### 三元运算符

```js
var res1 = true?'正确':'错误';
var res2 = false?'正确':'错误';
console.log(res1,res2) //正确,错误
```

#### switch语句

```js
//每一个条件都是判断是否等于某个具体的值,并且有多个条件,就可以用switch
//给你一个数字,你告诉我是星期几
var week = 4;
switch(week){
  case 1:
    console.log('星期一');
    break;
  case 2:
    console.log('星期二');
    break;	
  case 3:
    console.log('星期三');
    break;
  case 4:
    console.log('星期四');
    break;
  case 5:
    console.log('星期五');
    break;
  case 6:
    console.log('星期六');
    break;
  case 7:
    console.log('星期日');
    break;
  default:
    console.log('没有这一天');
    break;
}
//如果不加break停止,判断结束后会一直执行到底,直到遇到break或return
```

#### while语句

```js
//计算1-100的累加和
var num = 0;
var sum = 0;//使用一个变量sum记录当前的累加和;
while(num<100){
 	num++;
 	sum = sum+num;
}
```

#### dowhile语句

```js
//do...while...
//先执行do后面的代码,然后判断条件,条件为真,再次执行do后面的代码,然后判断条件,条件位置,再次执行do后面的代码,一直到条件为假,退出循环
//使用do-while循环：输出询问“我爱你，嫁给我吧？”，选择“你喜欢我吗？(y/n):"，如果输入为y则打印”亲亲我的宝贝“，若输入为n,则继续询问 
do{
  var result = prompt('我爱你，嫁给我吧？','你喜欢我吗？(y/n)');		
}while(result!="y");
console.log("亲亲我的宝贝");
```

#### for循环

```js
for(1 初始化条件只执行一次;2 循环条件;4 要循环的代码执行完成后执行的代码){
  3 要循环的代码
}
for循环代码顺序为:1234-234-234-......
//1-100的累加和
for(var num=1,sum=0;num<=100;num++){
	sum = sum + num;
}
console.log(sum);//5050
console.log(num);//101
```

## day03

#### continue和break

```js
//循环输出1-100.碰到50退出整个循环
for(var i=1;i<101;i++){
	//退出整个for循环:break
	if(i==50){
		break;
	}
	console.log(i)
}

//循环输出1-100.但是不输出10的倍数
for(var i=1;i<101;i++){
	if(i%10==0){
		continue;//退出本次循环
	}
	console.log(i)
}
```

#### 数组的定义和遍历

```js
//简单数据类型:number(1),string('我'),boolean(true),undefined,null
//复杂数据类型:array
//想存储全班所有同学的姓名
//数组:数据以一定的顺序存储在一起的集合,这个集合就叫数组
var totalName = ['周翔','叶满香','吴少辉',178,'45kg',['写代码','交朋友','旅游','打游戏']];//数组array
console.log(totalName);
console.log(totalName.length);//可以获取数组内元素的个数
console.log(totalName[0]);//获取数组中的第一个元素
console.log(totalName[totalName.length-1])//获取数组中的第一个元素
//遍历数组:把数组中的每个元素去取出一遍
for(var i=0;i<totalName.length;i++){
  console.log(totalName[i]);//i=0,1,2,3,....totalName.length-1
}
```

#### 数组新增元素

```js
var arr = [34,123,"hello",34,"fdsf"];//索引从0到arr.length-1
arr[arr.length] = "中国";
arr[arr.length] = "先";
console.log(arr);//[34, 123, "hello", 34, "fdsf", "中国", "先"]
```

## day04

#### 函数

```js
//对于经常要重复使用的代码段,我就把这个代码段放到一个盒子里面,然后给盒子取一个名字,要用的时候就通过盒子名字来使用:函数
//fn:函数名
//函数的关键字:function
//{}里面是要执行的代码块
//定义函数的时候是不执行代码块的

var fn = function(){
  //计算1-100的累加和
  for(var i=1,sum=0;i<101;i++){
    sum+=i;
  }
  console.log(sum)
}

//要执行函数的时候:函数名()
fn()
```

#### 函数的定义和特点 

```js
//函数的定义方式
//函数声明
function fn(){
  //函数体:函数要执行的代码块
  //fn函数如果执行可以计算5的阶乘,并打印结果
  for(var i=1,ji=1;i<6;i++){
    ji *= i;
  }
  console.log(ji)
};	

//变量
var fn1 = function(){
  //函数体:函数要执行的代码块
  //输出1-100之间的奇数
  for(var i=1;i<101;i++){
    if(i%2==1){
      console.log(i)
    }
  }
};

(function(){
  console.log(1)
})()
//函数的特点:
//1 函数定义的时候,不会执行
//2 通过在函数名后面加(),可以调用函数:函数名()
//3 函数不调用不执行
//4 函数名代表函数体
//5 没有名字的函数叫匿名函数,匿名函数后面加括号可以调用
//6 可以节约变量名
```

#### 函数的参数

```js
function fn(start,end){
  //start,end:形参,主要用于占位置
  //可以计算任意两个数之间的数字的累加和
  for(var i=start,sum=0;i<=end;i++){
    sum+=i;
  }
  console.log(sum)
}
fn(1,100);//1和100是真正参与运算的,叫做实参
//实参个数如果多于形参个数:多余的不影响结果
//实参个数如果少于形参个数:多于的形参具体值为undefined
```

#### 函数返回值

```js
//return的作用
//1 返回值函数执行的结果return 值
//2 如果return后面没有值,那么返回值就是undefined
//3 return可以结束函数
function fn(a){
  a++;
  return a;
}
console.log(fn(5)) //6
//结束函数:return;
//结束循环:结束本次循环continue  结束整个循环break
```

#### arguments

```js
function fn(){
  //对于实参个数不确定的情况,可以使用函数内容的一个对象:arguments
  console.log(arguments);
  // 如何获取每一个实参
  // console.log(arguments[0])
  // console.log(arguments[1])
  // console.log(arguments[2])
  for(var i=0;i<arguments.length;i++){
    console.log(arguments[i])
  }
  console.log(arguments.callee);//当前的函数体

}
fn("hello",2,"china",3434,"0000");//arguments长度是5
// fn(["hello",2,"china",3434,"0000"]);//arguments长度是1
```

## day05

#### 变量的作用域

```
作用域:变量的起作用范围
全局作用域:在代码的全局范围都能使用的变量
局部作用域:在函数范围内起作用的变量	
块级作用域:在一个代码块内起作用的变量,js中原来没有块级作用域,在es6语法中,开始有块级作用域
```

#### 词法作用域

```js
//词法作用域: 不用通过代码运行,就能够通过代码语法判断出的作用域,静态作用域
//js作用域规范:
//函数外部不能访问函数内部的变量
//函数内部可以访问函数外部定义的全局变量
//函数内部如果声明了一个和全局变量同名的变量,函数运行时使用函数内部的(就近原则)
//函数内部通过var声明的变量是函数作用域,没有用var声明的变量是全局作用域

// var a = 1;
function fn(){
  // var a = 3;
  // var a = 6;
  a = 5;//赋值运算符
  //函数内部通过var声明的变量是函数作用域
  //函数内部没有用var声明的变量是全局作用域
  console.log(a);  //5

}
fn()
console.log(a);  //5
```

#### 预解析

```js
//预解析:在代码执行之前先进行代码解析
//函数声明和变量声明提升,只提升变量名,不提升变量值	

// var a = 1;
// function a(){
// 	console.log(b)
// 	var b = 34;
// 	var b = function(){
// 		console.log("我是函数")
// 	}
// 	console.log(b)
// }

// a();//报错

var b = 34;
var b = function(){
  console.log("我是函数")
}
b();
```

#### 获取DOM节点

```js
//1 获取事件源(引发后续事件的元素)
var box = document.getElementById('box');//获取id为box的标签
var width = box.style.width  //获取节点的属性
var box = document.getElementByTagName('div');获取所有div标签,是一个集合
```

#### 事件

```js
//onclick,鼠标单击
box.onclick = function(){
  
}
//ondblclick,鼠标双击
box.ondblclick = function(){
  
}
//onkeydown,按下按键时触发
box.onkeydown = function(){
  
}
//onkeyup,按下后松开按键时触发
box.onkeyup = function(){
  
}
//onchange,文本内容或下拉菜单改变时触发
box.onchange = function(){
  
}
//onfocus,文本框获得焦点时触发
box.onfocus = function(){
  
}
//onblur,文本框失去焦点时触发
box.onblur = function(){
  
}
//onmouseover,鼠标移入时触发
box.onmouseover = function(){
  
}
//onmouseout,鼠标移出时触发
box.onmouseout = function(){
  
}
//onload,页面加载完成后会触发该事件,只能书写一次
window.onload = function(){
  
}
//onunload,页面加载完成后会触发该事件,只能书写一次
window.onunload = function(){
  
}
//onsubmit,form表单提交事件,当返回true时,点击submit按钮才会跳转
box.onsubmit = function(){
  
}
//onreset,重置表单时
box.onreset = function(){
  
}
```

#### 小方法

```js
//去除字符串前后空格:trim()
console.log('   aaa    '.trim())//'aaa'
//isNaN(num),判断num是否是NaN
var num=Number('aaa')
console.log(isNaN(num))//true
```

#### 对象

```js
//创建对象的方法:字面量
var obj = {
  height:"184cm",
  weight:"60kg",
  "star":"狮子座",
  "love":"rap",
  "sex":"男",
  "age":19
}
//对象:一组无序的键值对的集合,属性如果没有特殊说明,都是字符串
console.log(obj)

//通过构造函数创建对象
```

#### Math对象

```js
//取随机数
console.log(Math.random());//可以生成一个0-1之间的随机,不能取到1
console.log(Math.floor(3.6));//向下取整
console.log(Math.ceil(3.3));//向上取整
console.log(Math.round(3.6));//四舍五入取整
console.log(Math.abs(-100));//取绝对值
//取0-4之前的随机整数
console.log(Math.floor(Math.random()*5));//0-5
//取6-100之间的随机整数
//6+0  6+1 6+2 6+3  6+94
console.log(6+Math.floor(Math.random()*(100-6+1)))
//封装一个函数可以获取min到max之间的随机数
function rand(min,max){
  return min+Math.floor(Math.random()*(max-min+1))
}
//使用上面的函数得到一个1-16之间的随机数,并转成16进制
var str = rand(1,16).toString(16);
console.log(str)
var str = rand(1,16).toString(16);
console.log(str)
```

## day06

#### 小知识

```js
//系统内置对象
console.log(window)
console.log(window.location);//BOM对象
console.log(Math)
//特殊标签获取方法
console.log(document.body);//body标签
console.log(document.head);//head标签
console.log(document.title);//直接获取title中的内容
document.title = "11111111111";
console.log(document.documentElement);//html标签
```

#### 数组的定义方法

```js
//通过字面量定义数组
var arr = [1,3,54,"hello"];
//通过构造函数定义数组
var arr1 = Array(1,3,54,"hello");//Array如果有多个参数,参数就是数组中的元素
var arr2 = Array();//空数组
var arr3 = Array(10);//如果只有一个参数,且参数是number类型,表示数组的长度
var arr4 = Array("10");
console.log(arr4)
```

#### 数组的常用方法一

```js
var  arr = Array(1,3,"helo",'蕾蕾',"lucy");
//unshift:给数组前面增加元素,返回值是数组的长度,在原数组上修改,不生成新数组
console.log(arr.unshift('我在最前面吗'));
// console.log(arr)
//push:给数组后面增加元素,返回值是数组的长度,在原数组上修改,不生成新数组
console.log(arr.push('我在最后面吗'))
// console.log(arr)
//shift:删除数组最前面的一个,在原数组上修改,返回值是被删除的元素
console.log(arr.shift());
// console.log(arr)
//pop:删除数组最后面的一个,在原数组上修改,返回值是被删除的元素
console.log(arr.pop());
// console.log(arr)
```

#### 数组的常用方法二

```js
var arr = new Array(3,4,65,"zhangguo");
//splice:删除 新增
//1 两个参数:第几位开始 删除几位	返回值是被删除元素的数组集合,在原数组删除数据
// console.log(arr.splice(1,2));
// console.log(arr)
//2 三个参数:第几位开始 删除几位  替换的新元素  返回值是被删除元素的数组集合
console.log(arr.splice(1,0,[2,2,2,2,2]));
console.log(arr)

//concat:连接多个数组
//返回值是连接成功的新数组,原数组不变
var arr1 = [1,1,1,1,1,1];
var arr2 = [2,2,2,2,2,2];
var arr3 = [3,3,3,3,3,3];
console.log(arr1.concat(arr2,arr3));
console.log(arr1)
console.log(arr2)

//join:把数组变成字符串
console.log(arr1.join());//如果不加参数,默认使用"逗号"为分隔符
console.log(arr1.join(""));
console.log(arr1.join("-"));
//split:把字符串变成数组
var str = "hello1-hello2-hello3";
console.log(str.split());//如果不指定分隔符,就整个字符串是数组中的一个元素
console.log(str.split("-"))
console.log(str.split(""))

//reverse:翻转数组,返回值是翻转后的数组,翻转是在原数组操作,不会产生新数组
var arr4 = ["world","hello","lucy"];
console.log(arr4.reverse());
console.log(arr4);
```

#### sort

```js
//sort:对数组进行排序
//参数:是一个函数,该函数有两个形参a,b
var arr = [12,442,23,232,432,3,3,42,43,2];
arr.sort(function(a,b){
  //a,b指代的是数组中的某个元素
  //若 a 小于 b，a 应该出现在 b 之前
  /*
  if(a<b){
    return -1;//return a-b
  }
  if(a==b){
    return 0;//reurn a-b
  }
  if(a>b){
    return 1;//return a-b
  }
  */
  return a-b;//从小到大
  //若 a 小于 b，a 应该出现在 b 之后
  /*
  if(a<b){
    return 1;//return b-a
  }
  if(a==b){
    return 0;//return b-a
  }
  if(a>b){
    return -1;//return b-a
  }
  */
  //return b-a; 从大到小
});
console.log(arr)
```

#### indexOf和lastIndexOf

```js
//indexOf:查找元素的位置,从前往后
//第一个参数是:要查找的数据
//第二个参数是:从什么位置开始查找,默认是从0开始查找
//返回值:查找到的第一个符合条件的元素的索引,如果没有符合条件的,返回-1

//lastIndexOf:查找元素的位置,从后往前
//第一个参数是:要查找的数据
//第二个参数是:从什么位置开始查找,默认是从0开始查找
//返回值:查找到的第一个符合条件的元素的索引,如果没有符合条件的,返回-1

//需求:["c", "a", "z", "a", "x", "a"]找到数组中每一个a出现的位置
var arr = ["c", "a", "z", "a", "x", "a"];
var index1 = arr.indexOf('a',0);//从index=0开始查找,找到的a的index = 1
var index2 = arr.indexOf('a',index1+1);//从index=2开始查找,找到的a的index = 3;
var index3 = arr.indexOf('a',index2+1);//从index=4开始查找,找到的a的index = 5;
var index4 = arr.indexOf('a',index3+1);//-1
console.log(arr.lastIndexOf('a',4))//3
```

#### 数组的遍历

```js
var salaryArr = [1500, 1200, 2000, 2100, 1800];	
//for循环
console.log("=============for循环===============")
for(var i=0;i<salaryArr.length;i++){
  console.log("第"+i+"个元素的值是"+salaryArr[i])
}
//for in循环
console.log("=============for  in循环===============")
for(var index in salaryArr){
  console.log("第"+index+"个元素的值是"+salaryArr[index])
}
//forEach遍历数组
console.log("=============forEach遍历数组===============")
salaryArr.forEach(function(value,index,arr){//参数对应 元素 下标 数组本身
  //每遍历一个数组元素,就执行一次函数
  console.log("第"+index+"个元素的值是"+value)
})
//map遍历数组
console.log("=============map遍历数组===============")
var newArr = salaryArr.map(function(value,index,arr){//参数对应 元素 下标 数组本身
  //每遍历一个数组元素,就执行一次函数
  console.log("第"+index+"个元素的值是"+value);
  //如果设置了返回值,那么每次循环的返回值会组成一个新数组,就是map的返回值
  return index*3;
})
console.log(salaryArr)
console.log(newArr)

//filter遍历数组
console.log("=============filter遍历数组===============")
var filterArr = salaryArr.filter(function(value,index,arr){//参数对应 元素 下标 数组本身
  //每遍历一个数组元素,就执行一次函数
  console.log("第"+index+"个元素的值是"+value);
  //如果遍历到的数组元素执行函数后,返回值是false,那么这个数组元素就不会进入新数组
  //如果遍历到的数组元素执行函数后,返回值是true,那么这个数组元素就会进入新数组
  //新数组就是filter执行后的返回值
  if(value<2000){
    return true;
  }else{
    return false;
  }
      
})
console.log(filterArr)
```

## day07

#### 对象

```js
//无序的键值对的集合,可以描述一种事物
var cxk = {
  height:178,
  weight:'64kg',
  love:'rap'
}
//对象通过字面量来定义
var zhangsan = {
  //特征,属性
  name:"张三",
  height:179,
  love:'coding',
  //行为,方法
  song:function(){
    console.log("张三喜欢带大家唱甜蜜蜜")
  }
}
//获取对象的属性值:变量名.属性名
console.log(zhangsan.height)
console.log(zhangsan.song)
//执行对象中的方法
zhangsan.song()
//给对象中的属性赋值:变量名.属性名 = 属性值
zhangsan.son = "小张三";
zhangsan.name = "老张";
zhangsan.song = "吉祥三宝";
console.log(zhangsan)

//对象通过构造函数来定义
var lisi = new Object();	
```

#### 对象注意点

```js
var height = "hh";
var obj = {
  height:178,
  hh:56
}
var boy = {
  height:178,//如果对象的属性名,用[]括起来,表明[]里面的内容按照正常的js语法解析
  cc:45
}
console.log(obj.height);//height是字符串
console.log(boy)
console.log(obj[height]);//56
```

#### 数据类型

```js
//简单数据类型:number,string,boolean,undefined,null 动产(饮料,笔记本,现金)
//复杂数据类型:object,array,function 不动产(房屋)

var num = 10;//num里面存的是真正的值
var num2 = 10;
var arr = [3,4,5,6];//arr里面存的是地址
var arr2 = [3,4,5,6];	

console.log(num==num2);//true,比较的num中的值
console.log(arr==arr2);//false,比较的是地址

var num3 = num2;//把num2的值赋给num3;
console.log(num2==num3);//true,比较的值

var arr3 = arr2;
console.log(arr3==arr2);//true

function fn(a){
  a = a+ 10;
}

fn(num);//把num的值传入函数fn,a = 10,a = a+10
console.log(num);//10

function fn2(a){
  a.push("hello");
}
fn2(arr);//把arr的地址传入函数fn2  a = arr;  a.push('hello')
console.log(arr);//[3,4,5,6,"hello"]
```

#### 字符串常用方法一

```js
//字符串的定义
var str = "hello world";//通过字面量定义
var str1 = new String('hello world');//通过构造函数定义
console.log(str)
console.log(str1)
//字符串的常用方法
//1 字符串变数组str.split(),参数是分隔符,返回值是分割好的数组
var arr = str.split(" ");
console.log(arr)
//2 查找字符串中的内容indexOf,lastIndexOf,如果找不到返回-1,如果找到返回响应字符的索引
console.log(str.indexOf('le'));//2
console.log(str.lastIndexOf('l'))//9
//3 给定索引,查找该索引对应的字符:参数是索引,返回值是该索引对应的字符,如果没有,返回空字符串
console.log(str.charAt(100))
//4 给定索引,查找该索引对应的字符的编码:参数是索引,返回值是该索引对应的字符编码,如果没有,返回NaN
console.log(str.charCodeAt(100))

//案例:检测字符串中有没有数字
var stringValue = "hello zhangsan";
 
//需要知道字符串有几个:stringValue.length
for(var i=0;i<stringValue.length;i++){
  var currentChar = stringValue.charCodeAt(i);//获取索引是i的字符编码
  if(currentChar>=48&&currentChar<=57){
    console.log('字符串中有数字');
    break;
  }
}

if(i>=stringValue.length){
  //如果循环没有中途退出,i=stringValue.length
  console.log('字符串中没有数字');
}
```

#### 字符串的常用方法二

```js
//1 字符串连接:str.concat(),参数是要拼接的字符串,返回值是新的拼接好的字符串,一般会用"+"做字符串拼接
var str = "hello"
var str2 = "world"
var str = str.concat(str2);
// var str = str +str2;
console.log(str);

var stringValue = "zhangsanlisiwangwu"
//2 字符串的截取:
console.log("===============stringValue.slice=================")
//stringValue.slice(截取开始的索引,截取结束的索引);包前不包后
console.log(stringValue.slice(0,8))
console.log(stringValue.slice(0));//表示从0到末尾
console.log(stringValue.slice(0,-1));//-1表示倒数第1个
console.log(stringValue.slice(-3))//表示倒数第3个到最后
console.log(stringValue.slice(8,0));//答案为空字符串,不能前大后小

console.log("===============stringValue.substr=================")
//stringValue.substr(截取开始的索引,截取的长度);
console.log(stringValue.substr(0,8));//从0开始,截取8个
console.log(stringValue.substr(0));//从0到末尾
console.log(stringValue.substr(-3));//倒数第三个到末尾	

console.log("===============stringValue.substring=================")
//stringValue.substring(截取开始的索引,截取结束的索引)
console.log(stringValue.substring(0,8));//张三
console.log(stringValue.substring(0));//表示从0到末尾
console.log(stringValue.substring(-3))//负数标签全部
console.log(stringValue.substring(8,0));//答案为空字符串,不能前大后小
```

#### 严格模式

```js
//严格模式
"use strict";
var a = 1;

function fn(a,b){
  console.log(a+b)
}
fn(1,3)

function fn1(){
  console.log(this);//undefined
}
fn1()
var btn = document.getElementsByTagName('input')[0];
btn.onclick = function(){
  //在事件函数中,this指的是事件源
  console.log(this)
}
```

## day08

#### 对象键值对的遍历

```js
var obj = {
  //对象中的属性
  name:"张三",
  age:12,
  love:"eating",
  //对象中的方法
  song:function(){
    console.log('sing this song')
    console.log(this)
  }
}

//使用for in循环遍历对象,注意因为key是变量名,所以要加[]
for(var key in obj){
  console.log("本次遍历到的键是"+key+"值是"+obj[key])
}
//调用对象中的方法
obj.song();//对象的方法中的this指的是对象(方法的调用者)
```

#### string大小写转换

```js
var str = "heLLo WorLD";
//统一转小写
console.log(str.toLowerCase())
//统一转大写
console.log(str.toUpperCase())
```

Math对象

```js
console.log(String.fromCharCode(50)) //2,输入编码,返回字符串
```

#### Math对象

```js
console.log(Math.random());//0-1的随机数,不包含1
console.log(Math.round(4.4));//四舍五入取整
console.log(Math.floor(4.4));//向下取整
console.log(Math.ceil(4.4));//向上取整
console.log(Math.abs(-9));//取绝对值
console.log(Math.max(45,2,4,2,42,4,432,67));//取最大值
console.log(Math.min(45,2,4,2,42,4,432,67));//取最小值
console.log(Math.PI);//圆周率
console.log(Math.pow(4,3));//求4的2次方

//数字转字符串
var num = 10;
console.log(num.toString());//10,默认十进制
console.log(num.toString(8))//12
console.log(num.toString(16))//a

//字符串转数字
var str = "a";
console.log(parseInt(str));//NaN,默认十进制
console.log(parseInt(str,16));//10
```

#### Date对象

```js
//data:数据
//date:日期
var date1 = new Date("2019 1 1 1:1:1");//加引号,月份就是1月到12月
var date2 = new Date(2019,1,1,1,1,1);//月份从0-11
var date3 = new Date(0);//距离1970年1月1日午夜0点的毫秒数
console.log(date1);
console.log(date2);
console.log(date3);

//Date对象的常用方法
var date = new Date();//不加参数,表示当前时间
//获取年份
console.log(date.getFullYear())
//获取月份
console.log(date.getMonth());//月份0-11
//获取天数
console.log(date.getDate());
//获取星期
console.log(date.getDay());//周日开始到周六,从0-6
//获取小时
console.log(date.getHours())
//获取分钟
console.log(date.getMinutes())
//获取秒数
console.log(date.getSeconds())
//获取当前时间到1970年1月1日午夜的毫秒数
console.log(date.getTime())
```

#### 定时器

```js
//循环定时器
var timer = setInterval(function(){
  到了时间要执行的代码块  
},时间间隔单位是毫秒)
//清除定时器
clearInterval(timer)
//执行一次的定时器
var timer = setTimeout(function(){
  到了时间要执行的代码块  
},时间间隔单位是毫秒)
//清除定时器
clearTimeout(timer)
```

#### 当前时间距离1970.1.1的毫秒数

```js
//方法一:
console.log(Date.now());
//方法二:
console.log(+new Date());
//方法三:
console.log(new Date().getTime())
//方法四:
console.log(new Date().valueOf())
```

#### 通过类名获取元素

```js
//有兼容性
var oneArr = document.getElementsByClassName('one');
//封装一个解决兼容性的方法获取类名节点
function getElements(className){
  //定义一个数组,用于存放符合条件的DOM节点
  var result = [];
  //第一步:获取页面上的所有标签
  var all = document.getElementsByTagName('*');
  //第二步:筛选其中类名叫one的元素
  for(var i=0;i<all.length;i++){
    if(all[i].className==className){
      //如果循环到的标签的类名和传入的类名一致,说明这个标签就是符合条件的
      result.push(all[i])
    }
  }
  return result;
}
```

## day09

#### BOM对象

```js
// BOM是核心
alert()//弹窗
// window对象
console.dir(window);//详细打印

// confirm,close,open方法
var result = confirm("确定要关闭吗?");//确认弹窗,返回值boolean
if(result){
	window.close();//关闭当前页
}else{
	window.open("https://www.baidu.com");//跳转到新页面
}

// history对象
history.back()//页面历史记录回退1页
history.forward()//页面历史记录前进1页
history.go(2)//前进2页,若为-2则回退2页

// location对象
location.href="https://www.baidu.com";//如果赋值和当前页面同地址,表示刷新
location.reload();//重新加载

//navigator
console.log(navigator)
```

#### 窗口宽高

```js
//ie9及其以上的版本
console.log("窗口宽度是"+window.innerWidth);//(包含滚动条)
console.log("窗口高度是"+window.innerHeight);//(包含滚动条)
//标准模式,一般是ie9以上
console.log("html高度是"+document.documentElement.clientHeight);
console.log("html宽度是"+document.documentElement.clientWidth);
//怪异模式,一般是ie9以下
console.log("body高度是"+document.body.clientHeight);
console.log("body宽度是"+document.body.clientWidth);
//模式判断
console.log(document.compatMode)//CSS1Compat表示标准模式
//函数封装
function getClient(){
	if(window.innerWidth!=undefined){
		return {
			width: window.innerWidth,
			height:window.innerHeight
		};
	}else if(document.compatMode=="CSS1Compat"){
		return {
			width:document.documentElement.clientWidth,
			height:document.documentElement.clientHeight
		};
	}else{
		return {
			width:document.body.clientWidth,
			height:document.body.clientHeight
		};
	}
}
```

#### scroll滚动事件

```js
window.onscroll = function(){
  //计算页面被卷曲的部分的宽度/高度
  // console.log("======window.pageXOffset=====")
  // console.log("被卷曲的宽度是"+window.pageXOffset);//支持IE9+
  // console.log("被卷曲的高度是"+window.pageYOffset);//支持IE9+
  // console.log("======documentElement=====")
  // console.log(document.documentElement.scrollTop)
  // console.log("======body=====")
  // console.log(document.body.scrollTop)
  console.log(scroll().top)
}
//函数封装
function scroll(){
	return {
		left:document.documentElement.scrollLeft||document.body.scrollLeft,
		top:document.documentElement.scrollTop||document.body.scrollTop
	}
}
```

#### DOM基础操作

```js
//通过id选择DOM
var header = document.getElementById('header');
//通过标签名选择DOM
var header = document.getElementsByTagName('p')[0];
//通过类名获取
var header = document.getElementsByClassName('header')[0];

//2 获取和设置元素的内容
console.log(header.innerHTML);
console.log(header.innerText)

header.innerHTML = "<h1>header</h1>";//认识标签
header.innerText = "<h1>header</h1>";//不认识标签

//3 获取标签名
console.log(header.tagName);//都是大写

//4 获取和设置标签属性
// console.log(header.id);//该方法只能是系统定义的属性
// console.log(header.className);//该方法只能是系统定义的属性

// console.log(header.index);//该方法不能获取自定义属性值
// header.index = "111";//该方法设置以后,不能显示在页面标签上
// console.dir(header)
header.setAttribute('index','111');//设置节点的index属性值为111
console.log(header.getAttribute('index'))//获取节点属性值
header.removeAttribute('index');//移除节点属性
```

## day10

#### DOM节点种类

* nodeType:节点种类，返回值是数字；
  * 1：元素节点（Element）
  * 2：属性节点（Attr）
  * 3：文本节点（Text）
  * 8：注释节点（Element）
  * 9：文档节点（Document）
  * 10：文档类型节点（DocumentType）
  * 11：文档片段节点（DocumentFragment）
* nodeValue: 获取（文字）节点的文本内容；不会进行解析，会将标签名转译成字符串，直接输出
* nodeName：返回node节点名称（#text，注释， 标签….）；
* tagName：返回node节点名称，元素节点特有，也可以用nodeName，
* attributes属性
  *  document.getElementById('box').attributes 获取所有，该节点的属性信息
  *  document.getElementById('box').attributes.length 返回属性节点个数
  *  document.getElementById('box').attributes[0]返回第一个属性节点
  *  document.getElementById('box').attributes[0].nodeType属性
  *  document.getElementById('box').attributes[0].nodeValue属性值
  *  document.getElementById('box').attributes['id']返回属性为 id 的节点
* childNodes：获取当前元素的所有子节点；
* 请注意子节点只算第一层的，孙子节点不在子节点的范畴内
* children:获取当前元素的所有元素节点
* parentNode:获取元素的父节点
* nextElementSibling:获取元素的下面一个兄弟元素节点 (678不支持)
* previousElementSibling:获取元素的上面一个兄弟元素节点 (678不支持)
* firstElementChild:获取元素的第一个子元素节点
* lastElementChild:获取元素的最后一个子元素节点

```html
<body>
	<div>
		hello,world
		<ul>
			<li>1</li>
			<li>1</li>
			<li>1</li>
			<li>1</li>
		</ul><span>zhangsan,lisi,wangwu</span>
		<!-- 这是注释 -->
		<img src="./01.jpg">
		end
	</div>
<script type="text/javascript">
	var div = document.getElementsByTagName('div')[0];
	console.dir(div.nodeType);//nodeType:1 元素节点
	//子节点
	var divChild = div.childNodes;//获取当前元素的所有子节点
	//文本节点
	console.log("======文本节点=======")//3
	console.log(divChild[0]);//hello,world
	console.log(divChild[0].nodeType);//3
	console.log(divChild[0].nodeName);//#text
	console.log(divChild[0].nodeValue);//hello,world

	//元素节点
	console.log("======元素节点=======")//1
	console.log(divChild[6]);//<img src='...' />
	console.log(divChild[6].nodeType);//1
	console.log(divChild[6].nodeName);//IMG
	console.log(divChild[6].tagName);//IMG
	console.log(divChild[6].nodeValue);//NULL,他使用innerHTML或者innerText

	//属性节点
	console.log("======属性节点=======");//2
  console.dir(divChild[6].attributes.nodeType);//2
	console.dir(divChild[6].attributes[0]);//src属性

	//注释节点
	console.log("======注释节点=======")//8
	console.log(divChild[4]);//<!-- 这是注释 -->
	console.log(divChild[4].nodeType)//8
	console.log(divChild[4].nodeName)//#comment
	console.log(divChild[4].nodeValue)//这是注释

	//文档节点document 
	console.dir(document.nodeType);//9
  
  //文档类型节点
  console.dir(document.doctype);//<!DOCTYPE html>
  console.dir(document.doctype.nodeType);//10
  
  //文档碎片节点
  console.dir(document.createDocumentFragment());//#document-fragment
  console.dir(document.createDocumentFragment().nodeType);//11
  
  //通过节点关系获取元素
  //子
  console.log(div.children);//集合,所有子元素节点
  console.log(div.firstElementChild);//ul,第一个子元素节点
  console.log(div.lastElementChild);//img,最后一个子元素节点
  //父元素
  console.log(div.parentNode);//body,父元素节点
  //兄弟节点
  console.log(div.previousElementSibling);//h1,上面一个元素节点
  console.log(div.nextElementSibling);//h2,下面一个元素节点
</script>
</body>
```

#### 节点操作

```js
//创建li标签
var newLi = document.createElement('li');
//插入内容
newLi.innerHTML = "我是第一个li";
// 在父元素中插入一个节点
var ul = document.getElementsByTagName('ul')[0];
//appendChild在父元素的最后插入一个子元素
ul.appendChild(newLi);
//insertBefore在ul.children[0]之前插入newLi，第一个参数是要插入的子节点，第二个参数是参照节点
ul.insertBefore(newLi,ul.children[0]);
//删除节点
ul.remove();//自杀
ul.removeChild(ul.children[0]);//父杀子
```

#### 文档碎片

```js
// 需求:在ul中插入4个li
var ul = document.getElementsByTagName('ul')[0];
//先创建一个文档碎片
var content = document.createDocumentFragment();
//用于存放四个li
for(var i=0;i<4;i++){
  var newLi = document.createElement('li');
  newLi.innerHTML = 1;
  content.appendChild(newLi);
}
ul.appendChild(content)
```

#### 获取元素的样式

```html
<style type="text/css">
  div{
    width:200px;
    height:300px;
    background:red;
    padding:50px;
  }
  div::before{
    content:"";
    color:blue;
  }
</style>
<body>
<div>
	
</div>
<script type="text/javascript">
	var div = document.getElementsByTagName('div')[0];
	//获取元素宽高
	// console.log(div.offsetHeight)
	// console.log(div.offsetWidth)

	//只能获取行内式的样式
	// console.log(div.style.width)
	// console.log(div.style.height)
	// console.log(div.style.background)

	// 获取元素的所有样式	
	// console.log(window.getComputedStyle(div,"before").color);//第一个参数是要获取样式的元素,第二个参数是伪元素
	// console.log(window.getComputedStyle(div,null).height);//第一个参数是要获取样式的元素
	// console.log(window.getComputedStyle(div,null).backgroundColor);//第一个参数是要获取样式的元素

	// console.log(div.currentStyle["width"])
	// console.log(div.currentStyle.height)
	// console.log(div.currentStyle.backgroundColor)


	//封装一个getStyle方法用于获取元素的样式
	function getStyle(element,attr){

		if(window.getComputedStyle){
			return window.getComputedStyle(element,null)[attr];
		}else{
			return element.currentStyle[attr];
		}

	}
	console.log(getStyle(div,'width'))

</script>
</body>
```

#### 自定义属性-html5新api

```js
//修改前<div data-index-aa="1"></div>
var div = document.getElementsByTagName('div')[0];
//以前,设置用setAttribute   获取用getAttribute  但属性不会显示在标签上
console.dir(div.dataset['indexAa'])
div.dataset['indexAa'] = 23
div.dataset["abv"]=15
console.log(div.dataset["abv"])
//修改后标签变为<div data-index-aa="23" data-abv="15"></div>
```

## day11

#### 同步和异步

```js
//代码是自上而下执行的
console.log(1)
console.log(2)

for(var i=0;i<11;i++){
  document.body.onclick = function(){
    //事件函数异步执行
    console.log(i);//11
  }
}
setTimeout(function(){
  //定时函数异步执行
  console.log('时间到了')
},0)
console.log(3);
```

#### event事件对象

* event.clientX/clientY:鼠标距离浏览器可视区域的距离
* event.pageX/pageY:鼠标距离页面的距离(ie无)

```js
var mask = getElements('mask')[0];//盒子
//添加事件
mask.onclick = function(e){
  //回忆前面学过的元素的宽度和高度
  //this.innerHTML = "mask的宽度是"+this.offsetWidth+"mask的高度是"+this.offsetHeight;
    
  //事件对象的兼容写法
  var event = window.event||e;
  console.log(event)

  //clientX/clientY:鼠标距离浏览器可视区域的距离
  this.innerHTML = "距离屏幕可视区域左边是"+event.clientX+"<br>距离屏幕可视区域上部是"+event.clientY

  //pageX/pageY:鼠标距离页面的距离(ie无)
  this.innerHTML += "<BR>距离页面顶部是"+ event.pageY
  
  //由于兼容性问题pageY不能直接使用
  //在页面位置就等于 = 看得见的+看不见的
  //pageY/pageX=event.clientY/clientX+scroll().top/scroll().left
  var pageY = event.clientY + scroll().top;
  
  //需求:在mask中显示鼠标相对mask的坐标
  //技术点:在mask中显示鼠标相对mask的坐标 = 鼠标距离页面顶部距离-mask距离页面顶部距离
  var mask = getElements('mask')[0];//盒子
  //元素距离最近的有定位的父元素的距离,如果父元素都没有定位,相对body计算距离
  console.log('mask距离页面左侧'+mask.offsetLeft)
  //元素距离最近的有定位的父元素的距离,如果父元素都没有定位,相对body计算距离
  console.log('mask距离顶部距离'+mask.offsetTop)
  //添加事件
  mask.onclick = function(e){
  	//事件对象的兼容写法
  	var event = window.event||e;
  	//鼠标距离页面距离
  	var pageX = event.clientX + scroll().left;
  	var pageY = event.clientY +scroll().top;
  	//mask距离页面距离mask.offsetTop/mask.offsetLeft
  	//求坐标
  	var x = pageX - mask.offsetLeft;
  	var y = pageY - mask.offsetTop;
  	mask.innerHTML = "x:"+x+"<br>"+"y:"+y	
}
```

#### offset和screen

* event.offsetX/layerX(火狐):鼠标距离鼠标所在元素的距离
* event.screenX/screenY:鼠标距离屏幕的距离(即显示屏的距离)

```js
var mask = getElements('mask')[0];
var star = getElements('star')[0];
mask.onmousemove = function(e){
  var event = window.event||e;
  //鼠标在mask中的坐标 = 鼠标距离页面的距离 - mask元素距离页面的距离
  var x = event.offsetX||event.layerX;//不建议使用
  var y = event.offsetY||event.layerY;//不建议使用		

  //鼠标距离屏幕的距离
  star.innerHTML = "鼠标在屏幕上的X坐标:"+event.screenX+"<br>鼠标在屏幕上的Y坐标:"+event.screenY;
}
```

#### 鼠标事件

```js
//onmouseover(onmouseenter),onmouseout(onmouseleave),onmousemove
//onclick:单击,ondblclick:双击
//onmousedown鼠标按下时触发,onmouseup鼠标按下后松开时触发
document.body.onmousedown = function(e){
  var event = window.event ||e;
  console.log(event.button);	
  //event.button:鼠标的按键,左键是0,中间键是1,右键是2
}
```

#### 键盘事件

```js
//onkeydown,onkeyup
var inp = $id('text');
//绑定事件
inp.onkeyup = function(e){
  var event = window.event||e;
  console.log(event)
  //获取按下的字符的编码
  var code = event.keyCode||event.which;
  //如果按下的是a就变色
  if(code==65){			
    inp.style.background = getColor();
  }
  console.log("你按下的是"+String.fromCharCode(code));
}
```

#### 组合按键

```js
document.body.onkeydown = function(e){
  var event = window.event||e;
  console.log(event);
  //如果同时按下ctrl+j就弹出对话框
  if(event.keyCode==74&&event.ctrlKey){
    alert("你按下了crtl+j键")
    // window.close()
  }
}
```

#### 绑定事件的方法

```js
var div = document.getElementsByTagName('div')[0];
// div.onclick = function(){
// 	alert(1)
// }
// div.onclick = function(){
// 	alert(2)
// }
//事件监听器:addEventListener IE8以下不支持
// div.addEventListener('click',function(){
// 	console.log(1)
// },false)
// div.addEventListener('click',function(){
// 	console.log(2)
// },false)


// div.attachEvent('onclick',function(){
// 	console.log(1)
// })
// div.attachEvent('onclick',function(){
// 	console.log(2)
// })

function addEvent(dom,type,fn){
  if(dom.addEventListener){
    dom.addEventListener(type,fn,false)
  }else{
    dom.attachEvent("on"+type,fn)
  }
}

addEvent(div,'click',function(){
  console.log(1)
})
addEvent(div,'click',function(){
  console.log(2)
})
```

#### 事件机制

```js
//事件机制
//div的子元素有mask和son,其中son又是mask的子元素
var mask = getElements('mask')[0]
var son = getElements('son')[0]
//事件绑定方法addEventListener	
//事件冒泡:子元素发生的事件,会冒泡到父元素上,并会一直往上冒,方向是由目标元素往上级
//事件捕获:事件从顶端向最小的元素捕获

//事件分为三个阶段:捕获 目标元素 冒泡,你可以选择在冒泡阶段发生,也可以选择在捕获阶段发生
document.body.addEventListener('click',function(){
  console.log('body被点击了')
},false)
//第三个参数:是否捕获
son.addEventListener('click',function(){
  console.log('son被点击了')
},false)	
mask.addEventListener('click',function(){
  console.log('mask被点击了')
},true) 
```

#### 阻止冒泡

```js
//事件对象
var event = window.event||e;
//阻止冒泡
if(event.stopPropagation){
  event.stopPropagation()
}else{
  event.cancelBubble = true;
}
```

## day12

#### 浏览器默认行为

```js
//阻止a标签默认的跳转动作
var a = document.body.children[0];
a.onclick = function(e){
  var event = window.event||e;
  //阻止浏览器默认动作
  if(event.preventDefault){
    event.preventDefault()
  }else{
    return false;
  }		
}
//阻止默认动作不会阻止冒泡
document.body.onclick = function(){
  alert('body');
}
```

#### 自定义菜单

```js
//<div>		
//  <ul>
//    <li>下载</li>
//    <li>分享</li>
//    <li>删除</li>
//  </ul>
//</div>
var div = document.body.children[0];//盒子
var menu = div.children[0];//菜单
var liArr = menu.children;//子菜单
//1 点击div,出现自定义菜单ul
div.oncontextmenu = function(e){
  //事件对象
  var event = window.event||e;
  //不希望出现浏览器自带的快捷菜单,就要阻止浏览器的默认动作
  if(event.preventDefault){
    event.preventDefault()
  }else{
    return false;
  }
  //显示自定义菜单
  menu.style.display = "block";
  //确定鼠标在div中的坐标
  var pageX = event.clientX + scroll().left;
  var pageY = event.clientY + scroll().top;
  var x = pageX - div.offsetLeft;
  var y = pageY - div.offsetTop;
  //定位menu
  menu.style.top = y+"px";
  menu.style.left = x+"px";		
}
//2 点击ul中具体的菜单项,做具体的操作,因为li是ul的子元素,li的事件会冒泡到ul上,所以可以把li的事件绑定在ul上,叫事件委托
menu.onclick = function(e){
  // console.log(this);//this是事件源,就是menu
  var event = window.event||e;
  // console.log(event);
  //获取触发事件的那个li
  var target = event.target||event.srcElement;
  console.log(target.innerHTML)
  //阻止冒泡
  if(event.stopPropagation){
    event.stopPropagation();
  }else{
    event.cancelBubble = true;
  }
}
//3 点击menu以外的地方,隐藏菜单
document.body.onclick = function(){
  menu.style.display = "none";
}
```

#### oninput事件

```js
//oninput:文本框中增加或减少哪怕一个字符也会触发该事件,ie9+
//onpropertychange:ie9以下
var inp = document.body.children[0];
inp.oninput = inp.onpropertychange = function(){
  console.log(inp.value)
}
```

#### es6模板字符串

```js
var a = "zhangsan";
var age = 132;
var love = "lucy";
console.log("我的名字是"+a+",我的年龄是"+age+",我喜欢"+love);
//es6 模板字符串
console.log(`我的名字是${a},我的年龄是${age},我喜欢${love}`);
```

## day13

#### beforeunload事件

```js
//只能监听用户通过互动来关闭时触发的函数
document.onclick = function(){
  window.close();
}
window.onbeforeunload = function(){
  return confirm('你确定要退出吗?')
}
```

#### 正则表达式定义

```js
//正则表达式,一种规则的描述,规则表达式
var a = "hello"
//构造函数定义正则表达式
var reg1 = new RegExp(a,"i");
//字面量定义正则表达式:/正则表达式主体/修饰符
//i:不区分大小写
var reg2 = /h/i;
//.test(),可以检测test参数是否符合正则表达式
console.log(reg1.test('hello'));//true
console.log(reg1.test('hellooooo'));//true
console.log(reg1.test('324234hllo'));//false
console.log(reg1.test('hELo'));//false

console.log(reg2.test('h'));//true
console.log(reg2.test('fsdf'));//true
console.log(reg2.test('H'));//false
console.log(reg2.test('OO'));//false
```

#### 正则表达式预定义类

```js
//主要用于表单验证
//\d  数字0-9 [0-9]
//\D  非数字  非[0-9]
//\s  空格
//\S  非空格
//\w  字母数字下划线  [a-zA-Z0-9_]
//\W  非字母数字下划线
//\.   除换行和回车以外的任意字符
//\   转义符
//[\u4E00-\u9FA5]  汉字的正则判断
//修饰符g表示全局匹配

var str = "张三1234";
console.log(/\D/.test(str))//true
console.log(/\s/.test("李四   1234"));//true
console.log(/\W/.test(" "));//true
//match()能找出符合的字符串并返回一个数组
var str1 = "no body an apple on oonn the tree";
console.log(str1.match(/.n/g));//["an", "on", "on"]

var str = "i am at .the /tree";
console.log(str);
console.log(str.match(/\.t/g))//[".t"]
console.log(str.match(/\/t/g))//["/t"]
```

#### 量词

```js
//? 可有可无
var reg1 = /a?/
console.log(reg1.test('aa'))//true
//*至少出现0次
var reg2 = /a*/
console.log(reg2.test('张三a李四a'))//true
//+至少出现1次
var reg3 = /a+/
console.log(reg3.test('张三aaaa'))//true
//{n}表示重复出现n次
var reg4 = /a{3}/
console.log(reg4.test('张三aa'));//false
//{1,4}表示重复1到4次
var reg5 = /a{3,5}/
console.log(reg4.test('张三aa'));//false
//{4,}表示重复4次以上
var reg6 = /\d{4,}/g;
var str = "21412了假立刻1件回家32432.尼56玛332假列432加32加4563421";
console.log(str.match(reg6));//["21412", "32432", "4563421"]
```

#### 边界

```js
var str = "heoheo";
var reg1 = /he/;	
console.log(reg1.test(str));//true
//^ 开始
//$ 结束
//^$ 精确匹配
var reg2 = /^he/;
console.log(reg2.test(str))//true

var reg3 = /he$/;
console.log(reg3.test(str))//false

var reg4 = /^heo$/;//必须是heo
console.log(reg4.test(str))//false

//写一个规则,判断是否是邮编 343000
var reg5 = /^\d{6}$/
```

#### 范围类和负向类

```js
var reg1 = /^(0|1|2|3|4|5|6|7|8|9)$/;// |表示或者   
console.log(reg1.test("5"));//true

var reg2 = /^\d$/
console.log(reg2.test("6"));//true

var reg3 = /^[1-24-9a-zA-Z]$/;
console.log(reg3.test("A"));//true

var reg4 = /^[^1-24-9a-zA-Z]$/;//如果^在[]里面,表示取反
console.log(reg4.test("_"));//true
```

#### 字符串的常用方法

```js
//match
//str.match(正则表达式) 找到返回数组，没有返回null
var str1 = "pc端千锋PC端学员PC端";	
console.log(str1.match(/PC端/gi));

//replace
//str.replace(正则表达式,替换成的字符串) 返回替换后的字符串
var str2 ="tmd你好tnnd真的吗tmd";
var result = str2.replace(/tmd/g,"***");
console.log(result);
result = result.replace(/tnnd/g,"****")
console.log(result);

//search
//str.search(正则表达式);忽略g 匹配成功，返回位置，不成功返回-1
var str3 = "pc端千锋PC端学员PC端";
console.log(str3.search(/PC端/i))//0
```

#### cloneNode克隆节点

```js
//克隆节点
var div = document.getElementById('div')
var newDiv = div.cloneNode(true);//true表示克隆包含子元素
```

#### 判断文件类型

```js
//<label for="photo">+</label>
//<input type="file" id="photo">
//在文件域中选择一个图片,如果选择的不是图片,弹出错误提示
var photoInp = document.getElementById('photo');
photoInp.onchange = function(){
  //获取文件的文件名
  var fileName = photoInp.files[0].name;
  //文件名的后缀必须是:.jpg.gif.jpeg.webp.png
  var reg = /\.(jpg|gif|jpeg|webp|png)$/;
  //判断文件名是否符合正则,符合就是图片,不符合就不是图片
  if(reg.test(fileName)){
    alert('你选择的是图片,可以上传')
  }else{
    alert('你选择的不是图片,请重新选择')
  }
  //FileReader
}
```

## day14

#### json的转换

```js
//把类似json的字符串转成json
var json = JSON.parse(str);
//把json转字符串
var str = JSON.stringify(json);
```

#### let

```js
// console.log(a)
var a = 1;//全局变量
var a = 1;
function fn(){
  var b = 2;//局部变量
}

{
  var c = 3;//全局变量
  let cc = 45;
}
// let:定义的是块级作用域,不能重复定义变量,不存在变量声明提升
// console.log(aa);//会报错,let没有变量声明提升Cannot access 'aa' before initialization
let aa = 2;
// let aa = 2;//会报错,let定义的变量不能重复声明Uncaught SyntaxError: Identifier 'aa' has already been declared
aa = 3;
function fn1(){
  let bb = 22;
  console.log(aa)
}
// fn1();
// console.log(cc)
// console.log(aa)

for(let i=0;i<5;i++){	
  
  function fn(){
    console.log(i)
  }
}
fn();
// console.log(i)
```

#### const

```js
//const:块级作用域
{
  // console.log(a);//报错:Cannot access 'a' before initialization
  const a = {};//报错:Missing initializer in const declaration,const定义变量同时要赋值
  // const a = 23;//报错:Identifier 'a' has already been declared,不能重复声明
  // a = 13;//报错:Assignment to constant variable,不能重复赋值
  a.name = "张三";
}
// console.log(a);//报错:ReferenceError: a is not defined
```

#### 箭头函数

```js
var fn = function(a,b){		
  console.log(a);
  console.log(b);
}
//箭头函数
var fn1 = (a,b)=>{		
  console.log(a);
  console.log(b);
  return a+b;
}
console.log(fn1(34,43));

//箭头函数的简写方法
//如果只有一个形参,可以省略()
var fn2 = a=>{		
  console.log(a);	
}
fn2(2222);
//如果函数主体里面只有一句话,可以省略{}
var fn3 = a=>console.log(a);
fn3(2222);
//如果函数主体里面只有一句话,并且这句话是return ,可以省略{}和return
var fn4 = a=>a;
console.log(fn4(44444));
```

#### this指向

```js
//给div添加点击事件
var div = document.getElementsByTagName('div')[0]
//this的指向
console.log(this);//window
function fn(){
  console.log(this);//window
}
div.onclick = function(){
  console.log(this);//div
  setTimeout(()=>{
    console.log(this);//div
  },2000)
}
var obj = {
  name:"zhangsan",
  callFn:function(){
    console.log(this);//obj
  }
}
// setTimeout(function(){
// 	console.log(this);//window
// },2000)
```

#### 参数打包

```js
var fn = function(){
  console.log(arguments);
  //计算参数累加和
  for(var i=0,sum=0;i<arguments.length;i++){
    sum+=arguments[i]
  }
  console.log(sum)
}
fn(1,3,43,4,5,5,5);

var fn1 = (...arr)=>{
  // console.log(arguments);
  // 报错:Uncaught ReferenceError: arguments is not defined,箭头函数中没有arguments对象
  // 计算参数累加和
  // for(var i=0,sum=0;i<arguments.length;i++){
  // 	sum+=arguments[i]
  // }
  // console.log(sum)
  console.log(arr);
  for(var i=0,sum=0;i<arr.length;i++){
    sum+=arr[i]
  }
  console.log(sum)
}
//参数打包
fn1(1,3,43,4,5,5,5);
```

#### 参数默认值

```js
// function render(dom,value){
// 	//设置函数默认参数值
// 	var dom = dom||document.body;
// 	var value = value||'请传入要渲染的内容';
// 	dom.innerHTML = value;
// }
function render(dom=document.body,value='请传入要渲染的内容'){
  
  dom.innerHTML = value;
}
// render();
render(document.getElementsByTagName('p')[0],0);
```

#### 解构赋值

```js
// 数组
var arr = [11,22,33,44,55,{a:"张三",g:12},77];
// let a = arr[0];
// let b = arr[1];
// let c = arr[2];
// let d = arr[3];
// let e = arr[4];
// let f = arr[5];
// let g = arr[6];
// let [a,b,c,d,e,f,g] = arr;
let [a,b,c,d,e,...obj] = arr;
// let [...obj,a,b,c,d,e] = arr;//报错:Uncaught SyntaxError: Rest element must be last element
console.log(a,b,c,d,e);
console.log(obj);

let arr1 = [a,b,c];
console.log(arr1)

//对象
var people = {
  "xingming":"张三",
  "age":13,
  "love":"lucy"
}
// var xingming = obj.xingming;
// var age = obj.age
// var love = obj.love;
let {xingming,age,love} = people;
console.log(xingming,age,love);

var name = "lisi";
var like = "lili";
// var lisi = {		
// 	name:name,
// 	like:like
// }
var lisi = {
  name,like
}
console.log(lisi)

// function fn4({a,b}){
// 	var {a,b} = {a:34,b:56}
// 	console.log(a,b)
// }
// fn4({a:34,b:56})
```

#### ...

```js
var obj1 = {
  name:"lisi",
  age:12,
  sex:"nan"
}
var obj2 = {		
  ...obj1,
  name:"lucy",
  money:100,
  city:"深圳"
}
// var obj = {
// 	name:"lisi",
// 	age:12,
// 	sex:"nan",
// 	love:"lucy",
// 	money:100,
// 	city:"深圳"
// }

// var obj = {...obj1,...obj2};

console.log(obj2);

var arr1 = [1,2,3,4,2,3,5];
var arr2 = [34,2,23,...arr1,...arr1];
console.log(arr2)
```

#### 模板字符串和for of

```js
var str = "hello";
var a = 34;
var newStr = str+a

//模板字符串语法``也表示字符串

var str1 = `hello${a}world`;
var str2 = "hello"+a+"world"
console.log(str1);

//for of，数组可用，对象不可用
var arr = [11,22,33,44,55];
for(var value of arr){
  console.log(value)
}
for(var index in arr){
  console.log(arr[index])
}

var obj = {
  name:"张三",
  age:12
}
for(var key in obj){
  console.log(obj[key])
}
// for(var val of obj){
// 	console.log(val)
// };//报错:Uncaught TypeError: obj is not iterable
```

#### Array.from

```js
//获取所有的li
var liArr = document.getElementsByTagName('li');//集合

// liArr.forEach(function(dom){
// 	console.log(dom)
// });//报错,forEach是数组的方法,但是liArr不是数组

//Array.from可以把长得像数组的对象变成真正的数组
liArr = Array.from(liArr);
console.log(liArr);
liArr.forEach(function(dom){
  console.log(dom)
});

function fn(){
  console.log(Array.from(arguments))
}
fn(34,32,41,45,432,43);
//面试题 ： 定义一个函数，功能实现 生成m个n的数组   要求： 不利用循环
function fn2(m,n){
  return Array.from({length:m},()=>n)
}
console.log(fn2(5,7))
```

#### set类型(类似数组)

```js
var set1 = new Set([34,2,3,2,1,3,2,3,23,45,3,32]);
console.log(set1);

//题目:数组去重
var arr = [4321,43214,421,3,43,432,45,3,543,3,2,2,2,2,34,213,45,23];
var set2 = new Set(arr);
// var result = [...set2];
var result = Array.from(set2)
console.log(result);

//set的常用和属性
console.log(set2.size);//返回Set实例的成员总数
set2.add(46).add(47).add(48);//返回值就是添加成功以后的set数据
console.log(set2);
set2.delete(45);//返回值为布尔值
console.log(set2.has(466));//判断set中是否含有某个值,有返回true,没有就是false
set2.clear();//清除所有set数据，没有返回值
console.log(set2);

var arr3 = [{a:1},{a:1}];//复杂数据类型比的是地址
var set3 = new Set(arr3);
console.log(set3)
```

#### Symbol类型

```js
//隐藏对象中的键值对:Symbol
var obj = {
  name:"zhangsan",
  age:12,
  love:"lucy"
};
var attr = Symbol();
obj[attr] = "王五";
var attr1 = Symbol();
obj[attr1] = "10000"
console.log(obj);
for(var key in obj){
  //通过Symbol添加的键值无法遍历出来
  //可以通过console.log(obj[attr])打印出"王五"
  console.log(obj[key])
}
```

## day15

#### offset家族

* offsetWidth: width+padding+border
* offsetHeight: height+padding+border
* offsetLeft: 距离最近的有定位的父元素的距离
* offsetTop: 距离最近的有定位的父元素的距离
* 以上都是不带单位的
* offsetParent: 距离最近的有定位的父元素节点

#### offsetLeft和left的区别

* offsetLeft: 获取div距离最近的有定位的父元素的距离,不带单位,不能赋值,会取整,Number类型
* left: 带单位,可以赋值,可以是小数,字符串类型
* 其它同理

#### client家族

* 获取屏幕可视区域的宽高
  * window.innerWidth/innerHeight:  IE9+
  * document.documentElement.clientWidth/clientHeight: 标准模式
  * document.body.clientWidth/clientHeight: 怪异模式
* 获取元素的宽度和高度
  * offsetWidth = width + padding + border
  * clientWidth = width + padding

#### scroll家族

* scrollWidth/scrollHieght: 元素里面内容的宽高,不能小于盒子的宽高,IE67可以小于盒子宽高
* scrollTop/scrollLeft: 页面被卷曲的距离
  * document.documentElement.scrollTop/scrollLeft: 标准模式
  * document.body.scrollTop/scrollLeft: 怪异模式

#### 模拟滚动条小知识

```js
//当拖动滚动条时易选中文字，以下代码可以禁止选中文字
window.getSelection ? window.getSelection().removeAllRanges() : document.selection.empty();
```

## day16-day18运动

## day18

#### 面向对象的语法

```js
//函数
function People(name){
  this.name = name;
  // console.log(this);
  this.sayName = function(){
    //实例对象的方法中的this是实例对象
    console.log(this.name)
  }
}	

//es6新增了一个类的写法
// class People{
// 	constructor(name){
// 		this.name = name;
// 	}
// 	sayName(){
// 		console.log(this.name)
// 	}
// }	

//如何判断一个函数当前是普通函数还是构造函数

//在调用函数的时候确定函数的角色
// console.log(People());
//普通函数中this是window
var obj = new People("张胜男");
//构造函数中的this是实例化对象,默认返回值是this,如果人为设定返回值,返回值是简单数据类型,没用,如果是复杂数据类型,则返回该复杂数据类型
var obj1 = new People("李四");
var obj2 = new People('王五');
var obj3 = new People('旺财');
var obj4 = new People('小强');
// console.log(obj)
// console.log(obj1)
// console.log(obj2)
// console.log(obj3)
// console.log(obj4)
obj.sayName()
obj1.sayName()
obj2.sayName()
obj3.sayName()
obj4.sayName()
//new 做了什么
//new 开辟一块内存空间
//空间地址赋给this
//给this添加属性和方法
//把this返回
```

#### 面向对象案例

```js
//<input type="button" value="隐藏/显示" id="oneinp">
//<div id="onediv"></div>
//<input type="button" value="隐藏/显示" id="twoinp">
//<div id="twodiv"></div>
//面向对象案例
class ShowDiv{
  constructor(btn,div){
    this.btn = document.getElementById(btn);
    this.div = document.getElementById(div);
    this.flag = 1;
  }
  init(){
    var that = this;
    this.btn.onclick = function(){
      if(that.flag){
        animate(that.div,{opacity:0})					
        that.flag = 0;
      }else{
        animate(that.div,{opacity:100})
        that.flag = 1;
      }
    }
  }
}

//初始化对象
var show1 = new ShowDiv("oneinp","onediv");
show1.init()
var show2 = new ShowDiv("twoinp","twodiv");
show2.init()

//构造函数:抽象的
function Human(name,age,sex){
  //构造函数中的this是实例对象
  this.name = name;
  this.age = age;
  this.sex = sex;
  this.guoji = "china";

  this.walk = function(){
    console.log(this.name+"会走路")
  }
  this.born = function(){
    console.log(this.name+"已经出生"+this.age+"年了")
  }
  this.die = function(){
    console.log('有的人活着他已经死了,有的人死了他还活着')
  }

}
// class Human{
// 	constructor(name,age,sex){
// 		this.name = name;
// 		this.age = age;
// 		this.sex = sex;
// 		this.guoji = "china";
// 	}
// 	walk(){
// 		console.log(this.name+"会走路")
// 	}
// 	born(){
// 		console.log(this.name+"已经出生"+this.age+"年了")
// 	}
// 	die(){
// 		console.log('有的人活着他已经死了,有的人死了他还活着')
// 	}
// }

//实例对象:具体的
var zhangsan = new Human("张三",12,"男");
var lisi = new Human("李四",23,"女");

console.dir(zhangsan)
console.dir(lisi)

//好处:方便代码复用,节约命名空间

//面向对象

//语法点:
//如何判断一个函数是构造函数:当使用new调用函数的时候,就是构造函数
//构造函数以及构造函数方法中的this都是实例对象
//new做了什么:开辟一块内存空间,把空间地址给this,在this上添加键值对,返回this
//如果new调用函数时,函数定义了return,并且返回的是复杂数据类型,那么返回值为你定义的那个复杂数据类型
//es6新增的class(类),类似构造函数
```

## day19

#### 数组字符串的常用方法

```js
// 字符串常用方法
var str = "hEllo"
// length 字符串的长度 
console.log(str.length);//5
// charAt() 返回在指定位置的字符。 
console.log(str.charAt(0));//h
// charCodeAt() 返回在指定的位置的字符的 Unicode 编码。 
console.log(str.charCodeAt(0));//104
// concat() 连接字符串。 
var str1 = "world";
console.log(str.concat(str1));
// fromCharCode() 从字符编码创建一个字符串。 
console.log(String.fromCharCode(104))
// indexOf() 检索字符串。 
console.log(str.indexOf('l'));//检索不到返回-1
// lastIndexOf() 从后向前搜索字符串。 
console.log(str.lastIndexOf('l'));//检索不到返回-1
// match() 找到一个或多个正则表达式的匹配。 
console.log(str.match(/l/g))
// replace() 替换与正则表达式匹配的子串。 
console.log(str.replace(/l/g,"*"));//第一个参数是正则或者子串
// search() 检索与正则表达式相匹配的值。
console.log(str.search(/l/));//忽略全局匹配
// slice(start,end) 提取字符串的片断，并在新的字符串中返回被提取的部分。 
console.log(str.slice(0,2));//如果第二个参数不写表示到末尾
// split() 把字符串分割为字符串数组。 
console.log(str.split(""));//参数是分隔符,默认不分割
// toLowerCase() 把字符串转换为小写。
console.log(str.toLowerCase()) 
// toUpperCase() 把字符串转换为大写。 
console.log(str.toUpperCase())
// toString() 返回字符串。
console.log(str.toString())
// substr(start,length) 从起始索引号提取字符串中指定数目的字符。 
console.log(str.substr(1,2))//如果第二个参数不写表示到末尾
// substring(start,end) 提取字符串中两个指定的索引号之间的字符。 
console.log(str.substring(1,3))//如果第二个参数不写表示到末尾

// 数组常用方法
var arr = ["3","29","19","2"]
// length 设置或返回数组中元素的数目。 
console.log(arr.length)
// concat() 连接两个或更多的数组，并返回结果。 
var arr1 = ["hello","world"]
console.log(arr.concat(arr1))
// join() 把数组的所有元素放入一个字符串。元素通过指定的分隔符进行分隔。 
console.log(arr.join("-"));//参数是分隔符,默认是逗号
// sort() 对数组的元素进行排序 
arr.sort(function(a,b){
  return a-b
})
console.log(arr)
// pop() 删除并返回数组的最后一个元素 
console.log(arr.pop())
// push() 向数组的末尾添加一个或更多元素，并返回新的长度。 
console.log(arr.push("从后增加一个元素"))	 
// shift() 删除并返回数组的第一个元素 
console.log(arr.shift())
// unshift() 向数组的开头添加一个或更多元素，并返回新的长度。 
console.log(arr.unshift("从前面增加一个元素"))
// reverse() 颠倒数组中元素的顺序。
console.log(arr.reverse())	
// slice(start,end) 从某个已有的数组返回选定的元素 
console.log(arr.slice(0,2))
// splice(start,length,item1,.....,itemX) 删除元素，并向数组添加新元素。 
console.log(arr1.splice(0,0,"我是增加的第一个元素","我是增加的第二个元素"));//返回值是被删除的元素的集合
console.log(arr1)
// toString() 把数组转换为字符串，并返回结果。 
console.log(arr1.toString())
```

#### es6新增语法

```js
//es5语法新增:

//严格模式:'use strict';
// "use strict";
function fn(){
  //在严格模式下,普通函数中的this是undefined
  console.log(this)
}
fn();
var a = 1;//在严格模式下,变量要先声明再赋值
function ff(a,a){
  // 函数参数变量名不能重名
  console.log(a)
}

var arr = [23,2,432,3,4,4,3,324,43,34]
//Array增加方法:every(检测数值元素的每个元素是否都符合条件，返回布尔)、some(检测数组元素中是否有元素符合指定条件，返回布尔) 、forEach、filter 、indexOf、lastIndexOf、isArray、map、reduce方法	

console.log(Array.isArray(arr));//判断一个数据是否是数组
console.log(arr.indexOf(23));
console.log(arr.lastIndexOf(4));


console.log("===============every===============")
console.log(arr.every(function(value,index){
  console.log(value,index)
  return value>0;
}))
console.log("===============some================")
console.log(arr.some(function(value,index){
  console.log(value,index)
  return value>400;
}))
console.log("===============forEach==================")
arr.forEach(function(value,index){
  console.log(value,index)
})
console.log("===============filter==================")
console.log(arr.filter(function(value,index){
  // console.log(value,index)
  return value>200;
}))
console.log("===============map==================")
console.log(arr.map(function(value,index){
  // console.log(value,index)
  return value*2;
}))
console.log("===============reduce==================")
console.log(arr.reduce(function(prev,current){
  //第一个参数是上次函数的返回值,第二个参数是本次遍历到的数组元素
  return prev+current;
},0))//第二个参数是遍历最后一个元素时自己补充的元素


//es6语法新增:
//class:类
class Human{
  constructor(name,age){
    this.name = name;
    this.age = age
  }
  sing(){
    console.log('i can sing')
  }

}
//let const:块级作用域,const不能重复赋值,初始化就需要赋值,不能重复声明,没有变量声明提升
//箭头函数:不改变this的指向
var fn = a=>a;	
//解构赋值
// var obj = {
// 	name:"zhangsan",
// 	age:12
// }

// let {name,age} = obj;
let name = "zhangsan";
let age = 12;

let obj = {
  name,
  age
}

let arr1 = [3242,"ewr",432,43,2,3,3];
var [a,b,c,...d] = arr1;

//参数打包
function fn(...arr){
  console.log(arr)
}
fn(23,2,32,1,43)
//Array.from
var liArr = document.getElementsByTagName('li');
console.log(liArr)
console.log(Array.from(liArr))
//set类型:类似数组,不允许重复
var set = new Set(arr1)	
set.add(3)
console.log(set)
//map类型:类型对象,键可以是任意类型
var map = new Map();
map.set(document.getElementsByTagName('li')[0],"zhangsan");
console.log(map.get(document.getElementsByTagName('li')[0]))
//Symbol类型:for in循环不能遍历出来
var sym = Symbol();
var obj2 = {};
obj2[sym] = "lisi";
console.log(obj2)
//JSON.stringify() JSON.parse()
var obj3 = {
  name:"zhangsan",
  age:23
}
console.log(JSON.stringify(obj3))
var str = '{"name":"zhangsan","age":23}';
console.log(JSON.parse(str))
//模板字符串
var str = ` i can read text${arr1}`;
console.log(str)
//for...of循环
for(var key in obj3){
  //key是字符串类型
  console.log(key)
}
for(var value of arr1){
  console.log(value)
}
//参数默认值
function fn(a=3){
  console.log(a)
}
fn()
//扩展运算符...
var arr2 = [...arr1,34,23,2,442,4,...arr1]
var obj4 = {
  ...obj3,
  name:"lisi"
}
console.log(arr2)
console.log(obj4)
//字符串增加方法:repeat,参数是要复制的次数,不改变原字符串
console.log(str.repeat(3))
```

#### 扩展选择器

```js
//选中的是一个集合
var liArr = document.querySelectorAll("li.one");
//返回符合条件的第一个节点
var li = document.querySelector('li');
```

#### input.focus()

```js
//获取焦点
input.focus();
```

#### 获取节点

```js
//通过id获取元素
var box = document.getElementById('box');
//通过标签获取元素
var ul = document.getElementsByTagName('ul')[0];
//通过类名获取元素
var sp = document.getElementsByClassName('sp')[0]
//通过name获取元素
var inp = document.getElementsByName('inp')[0]
```

