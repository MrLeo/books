# 颜色
> 当涉及到操纵色彩时，Sass 通过提供少数的 [函数功能](http://sass-lang.com/documentation/Sass/Script/Functions.html)，最终成为了极具价值的助手。



## 颜色格式

为了尽可能简单地使用颜色，我建议颜色格式要按照以下顺序排列：
1. [CSS 颜色关键字](https://www.w3.org/TR/css3-color/#svg-color)
2. [HSL 值](http://en.wikipedia.org/wiki/HSL_and_HSV)
3. [RGB 值](http://en.wikipedia.org/wiki/RGB_color_model)
4. 十六进制。小写并尽可能简写
```scss
// Yep
.foo {
  color: red;
}

// Nope
.foo {
  color: #FF0000;
}

// Yep
.foo {
  color: #ebc;
}

// Nope
.foo {
  color: #eebbcc;
}
```
使用 HSL 值或者 RGB 值，通常在逗号 (,)后面追加一个空格，而不在前后括号 ((, )) 和值之间添加空格。
```scss
// Yep
.foo {
  color: rgba(0, 0, 0, 0.1);
  background: hsl(300, 100%, 100%);
}

// Nope
.foo {
  color: rgba(0,0,0,0.1);
  background: hsl( 300, 100%, 100% );
}
```



## 颜色和变量

当一个颜色被多次调用时，最好用一个有意义的变量名来保存它。
```scss
$sass-pink: #c69;
color: $sass-pink;
```
不过，如果你是在一个主题中使用，我不建议固定的使用这个变量。相反，可以使用另一个标识方式的变量来保存它。
```scss
$main-theme-color: $sass-pink;
```


## 变亮和变暗颜色

`lighten` 和 `darken` 函数都是通过增加或者减小HSL中颜色的亮度来实现调节的。基本上，它们就是 [`adjust-color`](http://sass-lang.com/documentation/Sass/Script/Functions.html#adjust_color-instance_method) 函数添加了 `$lightness` 参数的别名。
另一方面，通过混合 `白色` 或 `黑色` 实现变量或变暗的 [`mix`](http://sass-lang.com/documentation/Sass/Script/Functions.html#mix-instance_method) 函数，是一个不错的方法。
> 使用 `mix` 的好处是，当你降低颜色的比例时，它会渐进的接近黑色（或者白色），而 `darken` 和 `lighten` 立即变换颜色到黑色或白色。具体差异可以查看 [`KatieK`](http://codepen.io/KatieK2/pen/tejhz/)。

```scss
/// Slightly lighten a color
/// @access public
/// @param {Color} $color - color to tint
/// @param {Number} $percentage - percentage of `$color` in returned color
/// @return {Color}
@function tint($color, $percentage) {
  @return mix(white, $color, $percentage);
}

/// Slightly darken a color
/// @access public
/// @param {Color} $color - color to shade
/// @param {Number} $percentage - percentage of `$color` in returned color
/// @return {Color}
@function shade($color, $percentage) {
  @return mix(black, $color, $percentage);
}
```