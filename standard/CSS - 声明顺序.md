# 声明顺序

CSS 声明顺序以类型（position, display, colors, font, miscellaneous…）顺序排列，依赖盒模型定义顺序：由外而内。

1. 位置属性(position, top, right, z-index, display, float等)
2. 大小(width, height, padding, margin)
3. 文字系列(font, line-height, letter-spacing, color- text-align等)
4. 背景(background, border等)
5. 其他(animation, transition等)


```scss
.foo {
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1;
  width: 100px;
  height: 100px;
  margin: 0;
  padding: 0;
  font-weight: bold;
  font-size: 1.5em;
  color: white;
  background: black;
  overflow: hidden;
}
```


![css-written-order](http://images.shejidaren.com/wp-content/uploads/2013/09/css-written-order.png)

