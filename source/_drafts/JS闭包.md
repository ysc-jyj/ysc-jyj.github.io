---
title: JS闭包
tags: JavaScript
---
闭包就是一个函数包含一个函数，内部函数可以访问外部函数的变量，那么内部函数就是一个闭包
闭包可以让我们间接访问函数内部的变量

将函数作为返回值
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
a 变量的查找规则，它会在函数被定义的地方向上查找，而不会在函数执行的地方向上查找