# CSS变量
在需要设计主题｜动态修改系列样式｜字体放大缩小 等情况下 CSS变量可以提供很大帮助

## CSS变量声明及使用
声明一个自定义属性，属性名需要以两个减号（`—`）开始，属性值则可以是任何有效的CSS值。和其他属性一样，自定义属性也是写在规则集之内的，如下：

```
element {
  —main-bg-color: brown;
}
```


**注意:** 规则集所指定的选择器定义了自定义属性的可见作用域。通常的最佳实践是定义在根伪类 [`:root`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:root) 下，这样就可以在HTML文档的任何地方访问到它了：

```
:root {
  —main-bg-color: brown;
}
```


然而这条规则不是绝对的，如果有理由去限制你的自定义属性，那么就应该限制。

**注意:** 自定义属性名是大小写敏感的，`—my-color` 和 `—My-color` 会被认为是两个不同的自定义属性。

如前所述，使用一个局部变量时用 [`var()`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/var()) 函数包裹以表示一个合法的属性值：

```
element {
  background-color: var(—main-bg-color);
}
```

## JS修改CSS变量
在 JavaScript 中获取或者修改 CSS  变量和操作普通 CSS 属性是一样的：

```
// 获取一个 Dom 节点上的 CSS 变量
element.style.getPropertyValue("--my-var");

// 获取任意 Dom 节点上的 CSS 变量
getComputedStyle(element).getPropertyValue("--my-var");

// 修改一个 Dom 节点上的 CSS 变量
element.style.setProperty("--my-var", jsVar + 4);
```