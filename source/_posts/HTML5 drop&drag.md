---
title: HTML5 drop&drag
date: 2022-01-05
tags:
---

> 实现拖放

主要涉及的属性和方法

-   DataTransfer 对象：拖拽对象用来传递的媒介
-   draggable 属性：需要设置为`true`
-   ondragstart：被拖拽元素，开始被拖拽时
-   ondragenter：目标元素，拖拽元素进入目标元素
-   ondragover：目标元素，拖拽元素在目标元素上移动
-   ondrop：目标元素，拖拽元素在目标元素上鼠标放开
-   ondropend：被拖拽元素，拖拽完成
-   Event.preventDefault()：阻止默认事件，drop 事件默认以链接打开
-   Event.effectAllowed()：拖拽的效果

```html
<body>
	<div id="box1" ondrop="drop(event)" ondragover="allowDrop(event)">
		<div class="contain" draggable="true" ondragstart="drag(event)" id="tag"></div>
	</div>
	<div id="box2" ondrop="drop(event)" ondragover="allowDrop(event)"></div>
</body>
<script>
	// 拖拽什么
	function drag(e) {
		e.dataTransfer.setData('text', e.target.id)
	}
	// 放在哪里
	function allowDrop(e) {
		e.preventDefault() //ondrop会调用drop(event),阻止drop默认行为
	}
	// 放置
	function drop(e) {
		e.preventDefault()
		var data = e.dataTransfer.getData('text')
		e.target.appendChild(document.getElementById(data))
	}
</script>
```
