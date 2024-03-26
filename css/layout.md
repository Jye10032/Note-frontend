# 布局

块级元素和内联元素

* 常见的块级元素有 DIV, FORM, TABLE, P, PRE, H1\~H6, DL, OL, UL 等。
* 常见的内联元素有 SPAN, A, STRONG, EM, LABEL, INPUT, SELECT, TEXTAREA, IMG, BR 等。

***

* **display:block**

1. block元素会独占一行，多个block元素会各自新起一行。默认情况下，block元素宽度自动填满其父元素宽度。
2. block元素可以设置width,height属性。块级元素即使设置了宽度,仍然是独占一行。
3. block元素可以设置margin和padding属性。

* **display:inline**

1. inline元素不会独占一行，多个相邻的行内元素会排列在同一行里，直到一行排列不下，才会新换一行，其宽度随元素的内容而变化。
2. inline元素设置width,height属性无效。
3. inline元素的margin和padding属性，水平方向的padding-left, padding-right, margin-left, margin-right都产生边距效果；但竖直方向的padding-top, padding-bottom, margin-top, margin-bottom不会产生边距效果。

* **display:inline-block**

1. 简单来说就是将对象呈现为inline对象，但是对象的内容作为block对象呈现。之后的内联对象会被排列在同一行内。比如我们可以给一个link（a元素）inline-block属性值，使其既具有block的宽度高度特性又具有inline的同行特性。

注：**inline-block 存在间隙问题**

元素被当成行内元素排版的时候，元素之间的空白符（空格、回车换行等）都会被浏览器处理，根据 white-space 的处理方式（默认是normal，合并多余空白），原来HTML代码中的回车换行被转换成一个空白符，因此出现了间隙。

{% embed url="https://juejin.cn/post/7078969860545314824" %}

{% embed url="https://github.com/XXHolic/blog/issues/13" %}

#### span 元素换行

在 span&#x20;

```
span {
    display: inline-block;
}
```
