---
title: JS闭包
tags: JavaScript
date: 2021-11-04 14:01:23
---

**闭包**指有权访问另一函数作用域中变量的**函数**
闭包可以让我们间接访问函数内部的变量
1. 将函数作为返回值
    ```js
        function fn() {
            const a = 1;
            return function () {
                consloe.log('a', a);
            }
        }
        const fn = test()
        const a = 2
        fn();
    ```
    控制台输出 a 1
    a 变量的查找规则，它会在函数**被定义**的地方向上查找，而不会在函数执行的地方向上查找

2. 函数作为参数
    ```js
        function test(fn){
            const a =1;
            fn();
        }

        const a = 2
        function fn(){
            console.log('a'+ a)
        }

        test(fn)
    ```
    此时a的值为2，也是在被定义的地方向上查找