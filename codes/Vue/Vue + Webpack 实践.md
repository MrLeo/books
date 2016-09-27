# Vue全家桶

## 参考
- [vue-tutorial](https://github.com/MeCKodo/vue-tutorial)
- [Vue+Webpack开发可复用的单页面富应用教程](https://www.talkingcoder.com/article/6310756346094488391)
- [Vue+Webpack使用规范](https://www.talkingcoder.com/article/6309726065044556372)
[对比其他框架](http://cn.vuejs.org/guide/comparison.html)


推荐代码使用 CommonJS 或 ES6 模块，然后使用 [Webpack](http://webpack.github.io/) 或 [Browserify](http://browserify.org/) 打包。

你可以使用 Webpack + [vue-loader](https://github.com/vuejs/vue-loader) 或 Browserify + [vueify](https://github.com/vuejs/vueify) 构建这些单文件 Vue 组件。
> 可以在 [Webpackbin.com](http://www.webpackbin.com/vue) 上在线尝试！
> **chrome开发工具 : [vue-developertools](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)**

## 安装

1. 我们将会使用webpack去为我们的模块打包，预处理，热加载。如果你对webpack不熟悉，它就是可以帮助我们把多个js文件打包为1个入口文件，并且可以达到按需加载。这就意味着，我们不用去担心由于太多的组件，导致了过多的HTTP请求，这是非常有益于产品体验的。但，我们并不只是为了这个而使用webpack，我们需要用webpack去编译.vue文件，如果没有使用一个loader去转换我们.vue文件里的style，js，html，那么浏览器就无法识别。
2. 模块热加载是webpack的一个非常碉堡的特性，将会为我们的单页应用带来极大的便利。
    通常来说，当我们修改了代码刷新页面，那应用里的所有状态就都没有了。这对于开发一个单页应用来说是非常痛苦的，因为需要重新在跑一遍流程。如果有模块热加载，当你修改了代码，你的代码会直接修改，页面并不会刷新，所以状态也会被保留。
3. Vue也为我们提供了CSS预处理，所以我们可以选择在.vue文件里写LESS或者SASS去代替原生CSS。
4. 我们过去通常需要使用npm下载一堆的依赖，但是现在我们可以选择Vue-cli。这是一个vue生态系统中一个伟大创举。这意味着我们不需要手动构建我们的项目，而它就可以很快地为我们生成。

> 使用脚手架工具 [vue-cli](https://github.com/vuejs/vue-cli) 可以快速地构建项目：单文件 Vue 组件，热加载，保存时检查代码，单元测试等。
- 安装vue-cli (确保你有node和npm)
    ```
    $ npm install -g vue-cli
    ```

- 使用脚手架初始创建项目
    ```
    $ vue init <template-name> <project-name>
    ```

    Example:*创建一个webpack项目* 

    ```
    $ vue init webpack my-project
    ```

- 项目模版下载好了之后需要安装项目用到的依赖包
    ```
    $ cd my-project
    $ npm install
    ```

- 这时可以将项目运行起来看看效果了
    ```
    $ npm run dev
    ```
  这一行命令代表着它会去找到`package.json`的`scripts`对象，执行`node bulid/dev-server.js`。在这文件里，配置了Webpack，会让它去编译项目文件，并且运行服务器，我们在`localhost:8080`即可查看我们的应用。

  ![](https://cdn.scotch.io/9/vFba0QgQRReyNZPgFpKU_vue-time-1.png)

### vue-cli 构建的目录结构
```
.
├── build/                      # webpack config files
│   └── ...
├── config/                     
│   ├── index.js                # main project config
│   └── ...
├── src/
│   ├── main.js                 # app entry file
│   ├── App.vue                 # main app component
│   ├── components/             # ui components
│   │   └── ...
│   └── assets/                 # module assets (processed by webpack)
│       └── ...
├── static/                     # pure static assets (directly copied)
├── test/
│   └── unit/                   # unit tests
│   │   ├── specs/              # test spec files
│   │   ├── index.js            # test build entry file
│   │   └── karma.conf.js       # test runner config file
│   └── e2e/                    # e2e tests
│   │   ├── specs/              # test spec files
│   │   ├── custom-assertions/  # custom assertions for e2e tests
│   │   ├── runner.js           # test runner script
│   │   └── nightwatch.conf.js  # test runner config file
├── .babelrc                    # babel config
├── .editorconfig.js            # editor config
├── .eslintrc.js                # eslint config
├── index.html                  # index.html template
└── package.json                # build scripts and dependencies
```

  更多内容参照[https://vuejs-templates.github.io/webpack](https://vuejs-templates.github.io/webpack)

## Vue 指令
常用指令:
- v-if
- v-show
- v-else
- v-for
- v-bind
- v-on
- v-model
更多指令请移步[Vue 指令](http://cn.vuejs.org/api/#u6307_u4EE4)

## 初始化（main.js)

对于单页应用，推荐使用[官方库 vue-router](https://github.com/vuejs/vue-router)。详细请查看它的[文档](http://vuejs.github.io/vue-router/)。

### 添加route配置
```js
import VueRouter from 'vue-router'
import VueResource from 'vue-resource'

import Hello from './components/Hello.vue'
import Page from './components/Page.vue'

//注册两个插件
Vue.use(VueResource)
Vue.use(VueRouter)

const router = new VueRouter()

// 路由map
router.map({
  '/hello': {
    component: Hello
  },
  '/page': {
    component: Page
  }
})

router.redirect({
  '*': '/hello'
})

router.start(App, '#app')//设置启动页面
```
index.html
```html
<div id="app">
    <app></app>
</div>
```

### 应用route
```html
<template>
    <!-- 使用指令 v-link 进行导航。 -->
    <ul class="nav navbar-nav">
        <li><a v-link="{path: '/home'}">首页</a></li>
        <li><a v-link="{path: '/page'}">首页</a></li>
    </ul>
    <!-- 路由外链 -->
    <router-view></router-view>
</template>
```

## 创建＆应用组件
![](http://cn.vuejs.org/images/vue-component.png)
如果你喜欢预处理器，甚至可以这么做：
![](http://cn.vuejs.org/images/vue-component-with-pre-processors.png)

定义View:
```html
<template>
    <vue-component></vue-component>
</template>
```
定义Model和ViewModel:
```js
    var vueComponent = require('../components/vue-component');
    module.exports = {
        components: {
            vueComponent
        }
    }
```

## 数据请求:[vue-resource](http://www.cnblogs.com/keepfool/p/5657065.html)
```js
//在main.js中注册vue-resource
import VueResource from 'vue-resource'
Vue.use(VueResource)
```
```js
// 基于全局Vue对象使用http
Vue.http.get('//webapi.busi.inke.com/web/live_hotlist_pc', {}).then((response) => {
    console.log('[Leo]Vue-resource:success=>', response);
}, (response) => {
    console.log('[Leo]Vue-resource:error=>', response);
});
// 在一个Vue实例内使用$http
this.$http.get('//webapi.busi.inke.com/web/live_hotlist_pc', {}).then((response) => {
    console.log('[Leo]Vue-resource:success=>', response);
}, (response) => {
    console.log('[Leo]Vue-resource:error=>', response);
});
```
