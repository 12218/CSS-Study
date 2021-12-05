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

