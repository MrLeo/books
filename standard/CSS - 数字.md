# 数字

1. 当数字小于 1 时，省略小数的 0 
   ```scss
   // Yep
   .foo {
     padding: 2em;
     opacity: .5;
   }

   // Nope
   .foo {
     padding: 2.0em;
     opacity: 0.5;
   }
   ```

2. 当定义长度时，0 后面不需要加单位
   ```scss
   // Yep
   $length: 0;

   // Nope
   $length: 0em;
   ```

3. 给数字添加单位，可以让该数值乘以 `1` 个单位，也可以加上一个 `0unit`
   ```scss
   $value: 42;

    // Yep
    $length: $value * 1px;

    // Nope
    $length: $value + px;
   ```
   ```scss
   $value: 42 + 0px;
    // -> 42px

    $value: 1in + 0px;
    // -> 1in

    $value: 0px + 1in;
    // -> 96px
   ```
4. 删除一个值的单位，可以除以*相同类型*的 `1` 单位。
   ```scss
   $length: 42px;

    // Yep
    $value: $length / 1px;

    // Nope
    $value: str-slice($length + unquote(''), 1, 2);
   ```



# 运算

**最高级运算应该始终被包裹在括号中。**这么做不仅是为了提高可读性，也是为了防止一些 Sass 强制要求对括号内内容计算的极端情况。
```scss
// Yep
.foo {
  width: (100% / 3);
}

// Nope
.foo {
  width: 100% / 3;
}
```


# 幻数（MAGIC NUMBERS）

“幻数”，是http://en.wikipedia.org/wiki/Magic_number_(programming)#Unnamed_numerical_constants">古老的学校编程给未命名数值常数的命名。基本上，它们只是能工作™但没有任何逻辑思维的随机数。

相信不用多说你也会理解，幻数是一场瘟疫，应不惜一切代价以避免。当你对数值的解析方式无法找到一个合理解释时，你可以对此提交一个内容宽泛的评论，包括你是怎样遇见这个问题以及你认为它应该怎样工作。承认自己不清楚一些机制的解析方式，远比让以后的开发者从零开始弄清它们更有帮助。

```scss
/**
 * 1\. Magic number. This value is the lowest I could find to align the top of
 * `.foo` with its parent. Ideally, we should fix it properly.
 */
.foo {
  top: 0.327em; /* 1 */
}
```