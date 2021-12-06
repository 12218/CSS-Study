# CSS笔记01

## 01 结构伪类选择器

```css
:first-child	第一个子节点
:last-child		最后一个子节点
:nth-child(n)	第n个子节点
:nth-last-child(n)从后数第n个子节点
```

特殊使用：

```css
li:nth-child(even)
li:nth-child(odd)
li:nth-child(n)
li:nth-child(2n)
```

## 02 调用预设值

```css
.penguin {
    --penguin-skin: black;
	...
  }

  .penguin-top {
    ...
    background: var(--penguin-skin, gray);
    ...
  }
```

使用var可以直接调用预设值，其中“gray”在“--penguin-skin”不存在时作为替补颜色

## 03 media

```css
:root {
		--penguin-skin: black;
		--penguin-belly: gray;
		--penguin-beak: yellow;
	}
@media (max-height: 350px) {
		:root {
			--penguin-skin: green;
			--penguin-belly: blue;
			--penguin-beak: red;
		}
	}
```

当height小于350px时root发生改变

## 04 grid

```css
.container {
			...
			grid-template-columns: 1fr 2fr 1fr;
			grid-template-rows: 50px 70px 100px;
			grid-column-gap: 30px;
		}
.d5 {
			...
			grid-column: 2 / 4; // 开始于第二条线，终止于第四条线
		}
```

## 05 grid template

```css
.d5 {
		...
		grid-area: footer;
	}
.container {
	...
	grid-template-areas:
		"header header"
		"content content"
		"footer footer";
}
```

父元素定制模板，子元素可以调用模板

![01](E:\git\CSS\images\01.png)

## 06 grid-area

```css
.d5 {
		background: palegreen;
		/*grid-area: footer;*/
		grid-area: 1/1/2/3;
	}
.container {
	font-size: 40px;
	width: 100%;
	background-color: lightblue;
	display: grid;
	grid-template-columns: 1fr 1fr;
	/*grid-template-areas:
	"header header"
	"content content"
	"footer footer";*/
}
```

grid-area的值可以是元素的起止位置，1/1/2/3表示元素从grid中的1，1开始到2，3结束

![02](E:\git\CSS\images\02.png)

## 07 grid重复

```css
grid-template-rows: repeat(2, 1fr 50px) 20px;
/*等价于*/
grid-template-rows: 1fr 50px 1fr 50px 20px;
```

## 08 minmax函数

minmax函数包含两个值，代表元素长度最小和最大值

## 09 media queries响应式布局

```css
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Document</title>
	<style type="text/css">
		.container {
			background-color: lightgray;
			width: 100%;
			min-height: 250px;
			display: grid;
			grid-gap: 10px;
			grid-template-columns: 1fr 3fr;
			grid-template-rows: 1fr 8fr 1fr;
		}
		.header {
			background-color: lightblue;
			grid-area: 1/2/1/3;
		}
		.advert {
			background-color: orange;
			grid-area: 1/1/4/2;
		}
		.content {
			background-color: lightgreen;
			grid-area: 2/2/3/3;
		}
		.footer {
			background-color: lightsalmon;
			grid-area: 3/2/4/3;
		}
		@media (max-width: 600px) {
			.container {
				grid-template-columns: 1fr;
				grid-template-rows: 1fr 2fr 6fr 1fr;
			}
			.header {
				grid-area: 1/1/2/2;
			}
			.advert {
				grid-area: 2/1/3/2;
			}
			.content {
				grid-area: 3/1/4/2;
			}
			.footer {
				grid-area: 4/1/5/2;
			}
		}
	</style>
</head>
<body>
	<div class="container">
		<div class="header">header</div>
		<div class="advert">advert</div>
		<div class="content">content</div>
		<div class="footer">footer</div>
	</div>
</body>
</html>
```

布局随着浏览器大小的改变而进行改变
