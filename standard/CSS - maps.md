# Maps

从 Sass3.3 开始，样式表作者可以使用 map 这种数据结构—— Sass 团队使 map 可以映射关联数组、哈希表甚至是 Javascript 对象。map 是一种映射任何类型键值对（可以是任何类型，包括内嵌 maps，不过不推荐这种内嵌方式）的数据结构。

map 的使用应该遵循下述规范：
- 冒号(`:`)之后添加空格；
- 左开括号(`(`)要和冒号(`:`)写在同一行；
- 如果键是字符串（99% 都是字符串），则**使用引号包裹起来**。
- 每一个键值对单独一行；
- 每一个键值对以逗号(`,`)结尾；
- 为最后一个键值对添加**尾部逗号** (`,`)，方便添加新键值对、删除和重排已有键值对；
- 单独一行书写右闭括号 (`)`)；
- 右闭括号 (`)`)和分号(`;`)之间不使用空格和换行。
```scss
// Yep
$breakpoints: (
  'small': 767px,
  'medium': 992px,
  'large': 1200px,
);

// Nope
$breakpoints: ( small: 767px, medium: 992px, large: 1200px );
```



# 调试 SASS MAP

如果你感到困惑并想了解 Sass 的 map 到底有怎样的魔力，请不要担心，Sass 中始终存在一个自动保存运行过程的机制。
```scss
@mixin debug-map($map) {
  @at-root {
    @debug-map {
      __toString__: inspect($map);
      __length__: length($map);
      __depth__: if(function-exists('map-depth'), map-depth($map), null);
      __keys__: map-keys($map);
      __properties__ {
        @each $key, $value in $map {
          #{'(' + type-of($value) + ') ' + $key}: inspect($value);
        }
      }
    }
  }
}
```
如果你想深入了解 map 的实现机制，可以添加下述函数。该混合宏可以自动显示 map 的运行机制。
```scss
/// Compute the maximum depth of a map
/// @param {Map} $map
/// @return {Number} max depth of `$map`
@function map-depth($map) {
  $level: 1;

  @each $key, $value in $map {
    @if type-of($value) == 'map' {
      $level: max(map-depth($value) + 1, $level);
    }
  }

  @return $level;
}
```
