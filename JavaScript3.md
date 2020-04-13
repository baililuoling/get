# JavaScript

## String字符串
* str.includes(关键字)：判断str中是否含有关键字，返回布尔值
* str.padStart(length,补的字符)：从左补齐，例 '1'.padStart(2,'0')==='01'
* str.padEnd(length,补的字符)：从右补齐,例 '1'.padEnd(2,'0')==='10'

```js

```

## Array数组

```js
var arr=[1,2,3,4,5]
//遍历方法
//arr.find((item,index,arr)=>boolean)，查询符合条件的元素，函数返回布尔值，找到了返回第一个元素，没找到返回undefined
console.log(arr.find(item=>item>3));//4
//arr.findIndex((item,index,arr)=>boolean)，查询符合条件的元素下标，函数返回布尔值，找到了返回第一次的下标，没找到返回-1
console.log(arr.findIndex(item=>item>3));//3
```

## Object对象

```js
var obj={a:1,b:2,c:3};
//Object.keys(obj)，返回对象的键组成的数组
console.log(Object.keys(obj));//["a", "b", "c"]

//Object.values(obj)，返回对象的值组成的数组
console.log(Object.values(obj));//[1, 2, 3]

//Object.entries(obj)，返回对象的键值对组成的数组
console.log(Object.entries(obj));//[["a", 1], ["b", 2], ["c", 3]]
```