
[JSFiddle Hello World 例子](http://jsfiddle.net/chrisvfritz/4tpzm3e1/)

# 独立构建 vs 运行时构建
- **独立构建**:包括编译和支持 `template` 选项。 **它也依赖于浏览器的接口的存在，所以你不能使用它来为服务器端渲染。**
- **运行时构建**:不包括模板编译，不支持 `template` 选项。运行时构建，可以用 `render` 选项，但它只在单文件组件中起作用，因为单文件组件的模板是在构建时预编译到 `render` 函数中，运行时构建只有独立构建大小的30%，只有 16Kb min+gzip大小。

默认 NPM 包导出的是 `运行时` 构建。为了使用独立构建，在 webpack 配置中添加下面的别名：

```js
resolve: {
  alias: {
    'vue$': 'vue/dist/vue.js'
  }
}
```
> 不要用 `import Vue from 'vue/dist/vue.js'` - 用一些工具或第三方库引入 Vue ，这可能会导致应用程序在同一时间加载运行时和独立构建并造成错误。

# 生命周期钩子
![](./_image/f847b38a-63fe-11e6-9c29-38e58d46f036[1].png)

# 数组
- 突变方法
    - push()
    - pop()
    - shift()
    - unshift()
    - [splice](http://vuefe.cn/guide/list.html#注意事项)()
    - sort()
    - reverse()
- 重塑数组
    - [filter](http://vuefe.cn/guide/list.html#重塑数组)()
    - [concat](http://www.w3school.com.cn/jsref/jsref_concat_array.asp)()
    - [slice](http://www.w3school.com.cn/jsref/jsref_slice_array.asp)()

# vue 1.0->2.0 改变
### v-for `track-by`->[`:key`](http://vuefe.cn/guide/list.html#key)
```html
<div v-for="item in items" :key="item.id">
  <!-- 内容 -->
</div>
```
> 建议尽可能用 `v-for` 时提供一个 `key`，类似 Vue 1.X 的 `track-by="$index"`

### [自定义事件](http://vuefe.cn/guide/components.html#自定义事件)
- 使用 `$on(eventName)` 监听事件
- 使用 `$emit(eventName)` 触发事件

### [keep-alive](http://vuefe.cn/guide/components.html#keep-alive)
> 把切换出去的组件保留在内存中，可以保留它的状态或避免重新渲染

```html
<keep-alive>
  <component :is="currentView">
    <!-- 非活动组件将被缓存！ -->
  </component>
</keep-alive>
```

1.0 写法:

```html
<component :is="currentView" keep-alive>
  <!-- 非活动组件将被缓存 -->
</component>
```

### [v-once](http://vuefe.cn/guide/components.html#Cheap-Static-Components-with-v-once)
组件中包含大量静态内容时，可以考虑使用 `v-once` 将渲染结果缓存起来
```js
Vue.component('terms-of-service', {
  template: '\
    <div v-once>\
      <h1>Terms of Service</h1>\
      ... a lot of static content ...\
    </div>\
  '
})
```

### 过渡 [transition](http://vuefe.cn/guide/transitions.html#单元素-组件的过渡)

```js
new Vue({
  el: '#demo',
  data: {
    show: true
  }
})
```
```html
<div id="demo">
  <button v-on:click="show = !show">
    Toggle
  </button>
  <transition name="fade">
    <p v-if="show">hello</p>
  </transition>
</div>
```
```css
/*v-enter: 定义进入过渡的开始状态。在元素被插入时生效，在下一个帧移除。*/
/*v-enter-active: 定义进入过渡的结束状态。在元素被插入时生效，在 transition/animation 完成之后移除。*/
/*v-leave: 定义离开过渡的开始状态。在离开过渡被触发时生效，在下一个帧移除。*/
/*v-leave-active: 定义离开过渡的结束状态。在离开过渡被触发时生效，在 transition/animation 完成之后移除。*/
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s
}
.fade-enter, .fade-leave-active {
  opacity: 0
}
```
1.0 写法:
```html
<div v-if="show" transition="expand">hello</div>
```
```css
/* 必需 */
.expand-transition {
  transition: all .3s ease;
  height: 30px;
  padding: 10px;
  background-color: #eee;
  overflow: hidden;
}
/* .expand-enter 定义进入的开始状态 */
/* .expand-leave 定义离开的结束状态 */
.expand-enter, .expand-leave {
  height: 0;
  padding: 0 10px;
  opacity: 0;
}
```
**自定义过渡类名**
- enter-class
- enter-active-class
- leave-class
- leave-active-class

```html
<link href="https://unpkg.com/animate.css@3.5.1/animate.min.css" rel="stylesheet" type="text/css">
<div id="example-3">
  <button @click="show = !show">
    Toggle render
  </button>
  <transition
    name="custom-classes-transition"
    enter-active-class="animated tada"
    leave-active-class="animated bounceOutRight"
  >
    <p v-if="show">hello</p>
  </transition>
</div>
```
```js
new Vue({
  el: '#example-3',
  data: {
    show: true
  }
})
```








