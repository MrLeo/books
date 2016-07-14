# 列表

列表需要遵守以下规范：

- 除非列表太长不能写在 80 字符宽度的单行中，否则应该始终单行显示；
- 除非适用于 CSS，否则应该始终使用逗号作为分隔符；
- 要么使用内联形式，要么使用多行形式；
- 始终使用括号包裹；
- 始终不要添加尾部的逗号。
```scss
// Yep
$font-stack: ('Helvetica', 'Arial', sans-serif);

// Yep
$font-stack: (
  'Helvetica',
  'Arial',
  sans-serif
);

// Nope
$font-stack: 'Helvetica' 'Arial' sans-serif;

// Nope
$font-stack: 'Helvetica', 'Arial', sans-serif;

// Nope
$font-stack: ('Helvetica', 'Arial', sans-serif,);
```

当需要给列表添加一个新列表项时，请遵守其提供的 API，不要试图手动给列表添加列表项。

```scss
$shadows: (0 42px 13.37px hotpink);

// Yep
$shadows: append($shadows, $shadow, comma);

// Nope
$shadows: $shadows, $shadow;
```