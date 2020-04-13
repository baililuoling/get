# JavaScript算法题

## 交换两个变量的值

```js
//使用了临时变量
var a = 12,b = 23;
var c;
c = a;	//c = 12;
a = b;  //a = 23;
b = c;  //b = 12

//不使用临时变量
var one = 22,two = 33;
// 和
// one = one + two;//one = 55;
// two = one - two;//two = 22;
// one = one - two;//one = 33;

//差
one = two - one;//one = 11;
two = two - one;//two = 22;
one = two + one;//one = 33;
```

## 99乘法表

```js
//左下版
for(var row=1;row<10;row++){
  var str = ""
  for(var col=1;col<=row;col++){
    str = str +row+"*"+col+"="+row*col +"\t";
  }
  console.log(str)
}
//右上版
for(var i=1;i<10;i++){
  var str = "";
  for(j=1;j<10;j++){
    if(j<i){
      str = str+ "      \t"
    }else{
      str = str+ i+"*"+j+"="+i*j+'\t'
    }			
  }
  console.log(str);
}
```

## 斐波那契数列

```js
//书写函数计算斐波那契数列的第n项:1 1 2 3 5 8 13 21
function feiBo(n){
  if(n==1||n==2){
    return 1;
  }
  //如果代码执行到此处n>2
  return feiBo(n-1)+feiBo(n-2);
  //递归
}
console.log(feiBo(8));
// feiBo(8) = feiBo(6)+feiBo(5) + feiBo(5)+feiBo(4)


//书写函数计算斐波那契数列的第n项:1 1(a) 2(b) 3(sum) 5 8 13 21	
function feiBo2(n){
  var a = 1;//记录第n-2项
  var b = 1;//记录第n-1项
  var sum =1;//记录第n项
  if(n==1||n==2){
    sum = 1;
  }
  //如果n>2
  for(var i=3;i<=n;i++){			
    a = b;
    b = sum;
    sum = a+b;
  }
  
  return sum;
  
}
console.log(feiBo2(8))
```

## 辗转相除法

```js
// 辗转相除法
// 两个整数中最大的公约数等于较小那个数和两个数相除的余数最大公约数
// 就是先比较两个数的大小,取较小那个数作为除数.两数相除,如果余数为0,除数最大公约数;两数相除不为0,除数和余数继续进行相除
// 90和15 90/15=6 余0 最大的公约数就是15
// 30和8 30/8=3 余6
// 8/6=1 余2
// 6/2=3 最大公约数就是2
function gcd(x,y){
  if(x>y){
    var max = x;
    var min = y;
  }else{
    var max = y;
    var min = x;
  }
  if(max % min == 0){
    return min;
  }else{
    return gcd(min,max%min)

  }
}
console.log(gcd(90,15));
console.log(gcd(30,8))
```

## 求一组数中的最大值和最小值，以及所在位置

```js
var arr = [34,12,13,43,17,76,768,53,4232,456]

//第一步:最大值
//我假设最大值的索引是0
var maxIndex = 0;
//我假设数组的索引为0的是最大值
var max = arr[0];	

//第二步:最小值
//假设最小值的索引是0
var minIndex = 0;
//最小值就是
var min = arr[minIndex];

//数组最后一个值的索引是:arr.length-1
//然后依次把这个最大值和其他元素比较
for(var i=0;i<arr.length;i++){
  if(arr[i]>max){
    //如果遍历到的那个元素比max还大,max就会变成这个元素
    max = arr[i];
    //索引就换成i
    maxIndex = i;
  }
  if(arr[i]<min){
    //如果遍历到的那个元素比min还小,min就变成那个元素,最小值索引就变成i
    minIndex = i;
    min = arr[i]
  }

}	
// for(var j=0;j<arr.length;j++){
// 	if(arr[j]<min){
// 		//如果遍历到的那个元素比min还小,min就变成那个元素,最小值索引就变成j
// 		minIndex = j;
// 		min = arr[j]
// 	}
// }
//统一打印结果
console.log("最大值是:"+max+",所在位置是:"+maxIndex)
console.log("最小值是:"+min+",所在位置是:"+minIndex)
```

## 冒泡排序

```js
//从小到大排序
var arr = [23,34,45,56,67,78,89,90];
//比较的次数
var count = 0;
//用一个变量记录有没有换过位置

for(var num=1;num<arr.length;num++){
  //如果没有换过位置,flag就是true,如果换了位置flag就是false;
  var flag = true;
  //外层循环是轮数
  for(var i=0;i<arr.length-num;i++){
    count++;
    //内层循环是比较大小来调换位置
    if(arr[i]>arr[i+1]){
      flag = false;
      //换位置
      var temp = arr[i];
      arr[i] = arr[i+1];
      arr[i+1] = temp;
    }
  }
  if(flag==true){
    break;
  }
}
console.log(count)
```

## 质数判断

```js
//判断一个数是否是质数:1 2 3 5 7 11
//只能被1和本身整除的数就是质数/素数
function getNum(num){
  if(num<4){
    console.log(num+"是质数")
  }else{			
    for(var i=2;i<num;i++){
      //i = 2 num = 15 
      //i = 3 num = 15 
      if(num%i==0){
        console.log(num+"不是质数");
        break;
      }
    }
    if(i==num){
      console.log(num+"是质数")
    }

  }
}
getNum(13);
```

## 生成m个n的数组
```js
//面试题 ： 定义一个函数，功能实现 生成m个n的数组   要求： 不利用循环
function fn2(m,n){
  return Array.from({length:m},()=>n)
}
console.log(fn2(5,7))
```