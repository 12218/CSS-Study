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
