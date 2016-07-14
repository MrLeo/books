# 数字

1. 当数字小于 1 时，省略小数的 0 
   ```css
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
   ```css
   // Yep
   $length: 0;

   // Nope
   $length: 0em;
   ```

3. 给数字添加单位，可以让该数值乘以 `1` 个单位，也可以加上一个 `0unit`
   ```css
   $value: 42;

    // Yep
    $length: $value * 1px;

    // Nope
    $length: $value + px;
   ```
   ```css
   $value: 42 + 0px;
    // -> 42px

    $value: 1in + 0px;
    // -> 1in

    $value: 0px + 1in;
    // -> 96px
   ```
4. 删除一个值的单位，可以除以*相同类型*的 `1` 单位。
   ```css
   $length: 42px;

    // Yep
    $value: $length / 1px;

    // Nope
    $value: str-slice($length + unquote(''), 1, 2);
   ```

# 运算

**最高级运算应该始终被包裹在括号中。**这么做不仅是为了提高可读性，也是为了防止一些 Sass 强制要求对括号内内容计算的极端情况。
```css
// Yep
.foo {
  width: (100% / 3);
}

// Nope
.foo {
  width: 100% / 3;
}
```