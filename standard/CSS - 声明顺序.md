# 声明顺序

CSS 声明顺序以类型（position, display, colors, font, miscellaneous…）顺序排列，依赖盒模型定义顺序：由外而内。
```scss
.foo {
  width: 100px;
  height: 100px;
  position: absolute;
  right: 0;
  bottom: 0;
  background: black;
  overflow: hidden;
  color: white;
  font-weight: bold;
  font-size: 1.5em;
}
```