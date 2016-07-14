# 颜色

> [参考](参考)


1. 使用(2/4)空格代表缩进，而不是使用tab键
2. 理想上，每行保持为80个字符宽度
3. 正确书写多行CSS规则
4. 有意义的使用空格、换行
   ```css
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
   ```




# 编码

为了避免潜在的字符编码问题，强力建议在入口文件中通过 `@charset` 指令使用 **UTF-8** 编码格式。请确保该指令是文件的第一条语句，并排除其他字符编码声明。
```css
@charset 'utf-8';
```








[^参考]: http://www.kancloud.cn/kancloud/sass-guidelin/48096 