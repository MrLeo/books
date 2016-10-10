# [如何理解Vue.js的组件中的slot?](https://www.zhihu.com/question/37548226)
> slot 有点类似面向对象思想中的「多态」。

举个例子，比如我要实现一个这么 Alert 组件：
![](https://pic3.zhimg.com/55b5f7f0b72d1a88c81affcff9e69246_b.png)
它会有默认的内容和样式，比如第一行的 Default 我们只需要使用 
```html
<alert></alert>
```
当我们想要有 Success、Warning、Error 等不同样式和不同内容的 alert 时，我们会希望这样使用：
```html
<alert type="success">
  <strong>Success!</strong> Looks good to me!
</alert>

<alert type="warning">
  <strong>Warning!</strong> Something not good.
</alert>

<alert type="error">
  <strong>Error!</strong> Oooops...
</alert>
```
要实现这个功能，我们就会用到 slot。
```html
<style>
  .Alert__close {
    font-weight: bold;
    cursor: pointer;
  }
  .Alert--Success {
    color: green;
  }
  .Alert--Warning {
    color: #aa0;
  }
  .Alert--Error {
    color: red;
  }
</style>

<template id="alert-template">
  <div :class="alertClasses"  v-show="show">
    <slot><strong>Default!</strong> Hello World~</slot>
    <span class="Alert__close" @click="show = false">x</span>
  </div>
</template>

<script src="./node_modules/vue/dist/vue.js"></script>
<script>

Vue.component('alert', {
  template: '#alert-template',
  props: ['type'],
  computed: {
    alertClasses: function () {
      return {
        'Alert--Success': this.type === 'success',
        'Alert--Warning': this.type === 'warning',
        'Alert--Error'  : this.type === 'error'
      }
    }
  },
  data: function () {
    return {
      show: true
    };
  }
});

new Vue({
  el: 'body'
});
</script>
```
<slot> 就是外部调用时，标签中的内容。如果外部调用时没有提供内容的话，那么它就会使用自己默认提供的内容，非常方便。
