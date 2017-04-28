---
title: ES6知识整理
date: 2017-04-28 20:10:04
tags:
---


ES6默认开始严格模式`'use strict'`
块级zuo'yong'yu

## let和const

* `let、const`都是在块作用域内有效
* 不能重复声明同名变量及常量
* `const`基本类型的值不能修改，但引用类型的常量可以修改
* `const`声明时必须赋值
	```js
    const obj = {
        a: 1
    }
    obj.a = 2; // 2
    ```
## 解构赋值
```js
 // 数组解构赋值
{
    let a, b, c;
    [a, b, c] = [1, 2, 3];
    console.log(a, b, c) //1 2 3
}

{
    let a, b, c;
    [a, b] = [1, 2, 3];
    console.log(a, b, c) //1 2 undefined
}

{
    let a, b, c;
    [a, b, c=10] = [1, 2, 3];
    console.log(a, b, c) //1 2 10
}

{
    let a = 1;
    let b = 2;
    [a, b] = [b, a];
    console.log(a, b) //2 1
}

{
    let a, b, c;
    [a, b, ...c] = [1, 2, 3, 4, 5]
    console.log(a, b, c) //1 2 [3, 5]
}

{
    function f() {
        return [1, 2, 3];
    }
    let a, b;
    [a,...a] = f();
    console.log(a) //1 [2, 3]
}

 // 对象解构赋值
{
    let a, b;
    {a,b} = {a:1, b: 2};
    console.log(a, b) //1 2
}

{
   let o = {
        a: 12,
        b: 345
   };
   let {a, b} = o;
   console.log(a, b) //12 345
}

{
   let o = {
        a: 12,
        b: 345
   };
   let {a = 100, b} = o;
   console.log(a, b) //100 345
}

{
    let data = {
        type: 'a',
        test: [{
            type: 'b'
        }]
    };
    lef {
        type: esType,
        test:[
            type: cnType
        ]
    } = data;
    console.log(esType, cnType) //'a' 'b'
}


```

## 正则扩展

* 如果第一个参数是`/xyz/ig`形式，第二个参数会覆盖前者的flags
```js
let reg1 = new new RegExp(/xyz/ig, 'i');
console.log(reg1.flags) // i
```

* `y`与`g`修饰符的区别
	* `g`修饰符会在多次调用，匹配剩下的内容是否包含正则内容`（没有位置限制）`
	* `y`修饰符在多次调用，必须要求从`剩余的内容的第一位`成功`才能继续`
* `u`修饰符
	*  如果处理的字符里面有大于两个字节的字符
	*  修证`.`可以匹配任意字符的概念
	*  `.`只能匹配`小于两个字节长度`的字符
* `s`修饰符`（提案）`
	*  匹配换行  

## 字符串扩展

* 大于两个字节的字符使用`\u{20BB7}`表示
