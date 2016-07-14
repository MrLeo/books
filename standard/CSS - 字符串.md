# 字符串

字符串、URL 应该始终被**单引号(')**所包裹，*initial* 或 *sans-serif* 的专用名词无须引用起来
```css
// Yep
$direction: 'left';

// Nope
$direction: left;
```
```css
// Yep
.foo {
background-image: url('/images/kittens.jpg');
}

// Nope
.foo {
background-image: url(/images/kittens.jpg);
}
```
```css
// Yep
$font-type: sans-serif;

// Nope
$font-type: 'sans-serif';

// Okay I guess
$font-type: unquote('sans-serif');
```
```css
// Okay
@warn 'You can\'t do that.';

// Okay
@warn "You can't do that.";
```
