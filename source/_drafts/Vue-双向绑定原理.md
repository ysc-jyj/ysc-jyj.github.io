---
title: Vue 双向绑定原理
date: 2021-10-30 16:56:58
tags: 笔记
---
> 双向绑定数据是`vue`的一大特点，在面试中也被提问到，通过博客的方式记录一下

##  Object.defineProperty()  
`Object.defineProperty()`实现数据双向绑定的核心，它对data的每个属性进行了get、set的拦截
 这方法可以接收三个函数
 1. 属性所属的对象
 2. 操作的属性
 3. 操作的属性的特性（一般是get,set）  

```js
    const data={}
    let name = 'Vue'
    Object.defineProperty(data,'name',{//进行拦截
        get:function(){
            console.log('get')
            return name
        },
        set:function(newValue){
            console.log('set')
            name = newValue;//视图重新渲染
        }
    })
    //访问或修改数据会被Object.defineProperty()拦截
    console.log(data.name)
    data.name = 'Crisis'
    console.log(data.name)

```
###  极简版的双向绑定
```html
<body>
    <h2>极简版双向绑定</h2>
    <input type='text' id='ipt'>
    <p id='text'></p>
</body>
<script>
    let data = {}
    const ipt = document.getElementById('text')
    Object.defineProperty(data, 'name', {//进行拦截
        get: function () {
            return name
        },
        set: function (newValue) {
            ipt.innerHTML = newValue;//视图重新渲染
        }
    })
    document.getElementById('ipt').addEventListener('keyup', function (e) {
        data.name = e.target.value
    })
</script>
```
![](/images/极简双向绑定.gif)

## 观察者模式
一对多的模式

经历了波涛汹涌的秋招，虽然有收到offer但都不太满意，主要感觉自己能力还不行，所以目前决定先去小公司实习一下，后面有机会再战春招！