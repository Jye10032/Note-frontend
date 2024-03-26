# 选择器

**CSS 选择器**规定了 CSS 规则会被应用到哪些元素上。

1. 元素选择器（Element Selector）：通过元素名称选择元素。\
   例如：`p` 选择所有 `<p>` 元素。
2. 类选择器（Class Selector）：通过类名选择元素。\
   例如：`.my-class` 选择具有 `my-class` 类的元素。
3. ID选择器（ID Selector）：通过ID属性选择元素。\
   例如：`#my-id` 选择具有 `my-id` ID的元素。
4. 属性选择器（Attribute Selector）：通过元素的属性选择元素。\
   例如：`[type="text"]` 选择所有 `type` 属性值为 `"text"` 的元素。
5. 伪类选择器（Pseudo-class Selector）：通过元素的状态或位置选择元素。\
   例如：`:hover` 选择鼠标悬停在元素上的状态。
6. 伪元素选择器（Pseudo-element Selector）：选择元素的特定部分。\
   例如：`::before` 在元素前插入内容。
7. 后代选择器（Descendant Selector）：选择指定元素的后代元素。\
   例如：`.parent .child` 选择 `.parent` 元素内的所有 `.child` 元素。
8. 相邻兄弟选择器（Adjacent Sibling Selector）：选择紧接在指定元素后的兄弟元素。\
   例如：`.sibling + .sibling` 选择紧接在 `.sibling` 元素后的兄弟 `.sibling` 元素。
9. 通用选择器（Universal Selector）：选择所有元素。\
   例如：`*` 选择页面中所有元素。

***

**伪元素选择器示例：**

* 使用 `::before` 插入内容：

```
p::before {
  content: ">> ";
}
```

上述示例将在所有 `<p>` 元素的内容前插入 `>>` 。

* 使用 `::first-line` 修改首行样式：

```
p::first-line {
  font-weight: bold;
  color: blue;
}
```

上述示例将使所有 `<p>` 元素的首行文本加粗并设置为蓝色。

* 使用 `::first-letter` 修改首字母样式：

```
p::first-letter {
  font-size: 2em;
  color: red;
}
```

上述示例将使所有 `<p>` 元素的首字母字体大小为 2 倍，并设置为红色。

**直接子元素 >**

`>` 是子选择器（child selector）的一种。它用于选择指定元素的直接子元素。

```
<div class="rtl">
  <p>This paragraph is selected.</p> <!-- 直接作为 .rtl 元素的子元素 -->
  <div>
    <p>This paragraph is not selected.</p> <!-- 不是 .rtl 元素的直接子元素 -->
  </div>
</div>

```

在上述示例中，只有第一个 `<p>` 元素会被选择，因为它是直接作为具有 `.rtl` 类的 `<div>` 元素的子元素。

所以，`>` 选择器用于选择特定元素的直接子元素，而不会匹配更深层次的子元素。



{% embed url="https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_selectors" %}
