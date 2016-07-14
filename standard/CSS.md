# web前端规范-CSS

> 
>
> [参考 Sass Guidelines（中文版）](http://www.kancloud.cn/kancloud/sass-guidelin/48096 )
>
> 



## 编码

为了避免潜在的字符编码问题，强力建议在入口文件中通过 `@charset` 指令使用 **UTF-8** 编码格式。请确保该指令是文件的第一条语句，并排除其他字符编码声明。
```scss
@charset 'utf-8';
```



## 命名

就变量、函数和混合宏的命名而言，我们坚持一些很 *CSS-y* 的风格：**小写连字符分隔**，有意义的命名。
```scss
$vertical-rhythm-baseline: 1.5rem;

@mixin size($width, $height: $width) {
  // ...
}

@function opposite-direction($direction) {
  // ...
}
```
建议使用全大写方式书写常量
```scss
// Yep
$CSS_POSITIONS: (top, right, bottom, left, center);

// Nope
$css-positions: (top, right, bottom, left, center);
```



## CSS属性

1. 使用(2/4)空格代表缩进，而不是使用tab键
2. 理想上，每行保持为80个字符宽度
3. 正确书写多行CSS规则
4. 有意义的使用空格、换行
5. 相关联的选择器写在同一行；不相关联选择器分行书写
6. 最后一个选择器和左开大括号({)中间书写一个空格
7. 每个声明单独一行
8. 冒号(:)后添加空格
9. 所有声明的尾部都添加一个分号 (;)
10. 右闭大括号(})单独一行
11. 右闭大括号(})后添加空行
```scss
   // Yep
   .foo {
     display: block;
     overflow: hidden;
     padding: 0 1em;
   }

   // Nope
   .foo {
       display: block; overflow: hidden;

       padding: 0 1em;
   }
   
   // Yep
    .foo, .foo-bar,
    .baz {
      display: block;
      overflow: hidden;
      margin: 0 auto;
    }
    
    // Nope
    .foo,
    .foo-bar, .baz {
        display: block;
        overflow: hidden;
        margin: 0 auto }
```

添加与 CSS 相关的规范时，我们需要注意：
- 本地变量在其他任何变量之前声明，并和其他声明用空行分隔开；
- 不需 @content 的混合宏在放在其他声明之前；
- 嵌套选择器在新行声明；
- 需要 @content 的混合宏在嵌套选择器后声明；
- 右闭大括号(})上一行无需空行；
```scss
.foo, .foo-bar,
.baz {
  $length: 42em;

  @include ellipsis;
  @include size($length);
  display: block;
  overflow: hidden;
  margin: 0 auto;

  &:hover {
    color: red;
  }

  @include respond-to('small') {
    overflow: visible;
  }
}
```



## 注释

在代码完成之时立即注释

- 一个文件的结构或者作用；
- 规则集的目标；
- 使用幻数背后的目的；
- CSS 声明的原因；
- CSS 声明的顺序；
- 方法执行背后的逻辑思维。

##### CSS文件开头或核心块，使用多行注释：

```scss
/**
 * Helper class to truncate and add ellipsis to a string too long for it to fit
 * on a single line.
 * 1\. Prevent content from wrapping, forcing it on a single line.
 * 2\. Add ellipsis at the end of the line.
 */
.ellipsis {
  white-space: nowrap; /* 1 */
  text-overflow: ellipsis; /* 2 */
  overflow: hidden;
}
```

##### 当注释 Sass 的一个特定部分时，使用单行注释：

```scss
// Add current module to the list of imported modules.
// `!global` flag is required so it actually updates the global variable.
$imported-modules: append($imported-modules, $module) !global;
```

##### 每一个旨在代码库中复用的变量、函数、混合宏和占位符，都应该使用 [SassDoc](http://sassdoc.com/)  记录下来作为全部 API 的一部分。

```scss
/// Vertical rhythm baseline used all over the code base.
/// @type Length
$vertical-rhythm-baseline: 1.5rem;
```

SassDoc 需要三个反斜杠(`/`)，主要有两个作用：

- 作为公有或私有 API 的一部分，在所有的地方使用一个注释系统强制标准化注释。
- 通过使用任意的 SassDoc 终端(CLI tool, Grunt, Gulp, Broccoli, Node…)，能够生成 API 文档的 HTML 版本。

```scss
/// Mixin helping defining both `width` and `height` simultaneously.
///
/// @author Hugo Giraudel
///
/// @access public
///
/// @param {Length} $width - Element’s `width`
/// @param {Length} $height ($width) - Element’s `height`
///
/// @example scss - Usage
///   .foo {
///     @include size(10em);
///   }
///
///   .bar {
///     @include size(100%, 10em);
///   }
///
/// @example css - CSS output
///   .foo {
///     width: 10em;
///     height: 10em;
///   }
///
///   .bar {
///     width: 100%;
///     height: 10em;
///   }
@mixin size($width, $height: $width) {
  width: $width;
  height: $height;
}
```



## 媒体查询

**媒体查询紧贴选择器**

```scss
.foo {
  color: red;

  @include respond-to('medium') {
    color: blue;
  }
}
```

生成结果：

```css
.foo {
  color: red;
}

@media (min-width: 800px) {
  .foo {
    color: blue;
  }
}
```

