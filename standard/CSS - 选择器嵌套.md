# 嵌套选择器

**应该尽可能避免选择器嵌套。**



## 例外

在最外层选择器中嵌套伪类和伪元素是被允许，也是受推荐的。
```scss
.foo {
  color: red;

  &:hover {
    color: green;
  }

  &::before {
    content: 'pseudo-element';
  }
}
```
使用选择器嵌套选择伪类和伪元素不仅仅有道理的（因为它的处理功能与选择器紧密相关），而且有助于保持总体的一致性。
当然，如果使用类似 .is-active 类名来控制当前选择器状态，也可以这样使用选择器嵌套。
```scss
.foo {
  // ...

  &.is-active {
    font-weight: bold;
  }
}
```
这并不是最重要的，当一个元素的样式在另一个容器中有其他指定的样式时，可以使用嵌套选择器让他们保持在同一个地方。
```scss
.foo {
  // ...

  .no-opacity & {
    display: none;
  }
}
```