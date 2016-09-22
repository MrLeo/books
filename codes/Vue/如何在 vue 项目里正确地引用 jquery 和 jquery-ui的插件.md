# 如何在 vue 项目里正确地引用 jquery 和 jquery-ui的插件

使用vue-cli构建的vue项目，webpack的配置文件是分散在很多地方的，而我们需要修改的是`build/webpack.base.conf.js`，修改两处的代码

```js
// 在开头引入webpack，后面的plugins那里需要
var webpack = require('webpack')
// resolve

module.exports = {
   // 其他代码...
   resolve: {
      extensions: ['', '.js', '.vue'],
      fallback: [path.join(__dirname, '../node_modules')],
      alias: {
          'src': path.resolve(__dirname, '../src'),
          'assets': path.resolve(__dirname, '../src/assets'),
          'components': path.resolve(__dirname, '../src/components'),

          // webpack 使用 jQuery，如果是自行下载的
          // 'jquery': path.resolve(__dirname, '../src/assets/libs/jquery/jquery.min'),
          // 如果使用NPM安装的jQuery
          'jquery': 'jquery' 
      }
   },

   // 增加一个plugins
   plugins: [
      new webpack.ProvidePlugin({
          $: "jquery",
          jQuery: "jquery"
      })
   ],

   // 其他代码...
}
```

这样就可以正确的使用jQuery了，比如我要引入`Bootstrap`，我们在vue的入口js文件`src/main.js`开头加入

```js
// 使用Bootstrap
import './assets/libs/bootstrap/css/bootstrap.min.css'
import './assets/libs/bootstrap/js/bootstrap.min'
```

这样Bootstrap就正确的被引用并构建。
在比如使用`toastr`组件，只需要在需要的地方`import`进来，或者全局引入css在需要的地方引用js，然后直接使用

```js
// 使用toastr
import 'assets/libs/toastr/toastr.min.css'
import toastr from 'assets/libs/toastr/toastr.min'

toastr.success('Hello')
```

**参考: **
- [Managing Jquery plugin dependency in webpack](http://stackoverflow.com/questions/28969861/managing-jquery-plugin-dependency-in-webpack)
- [如何在vue项目里正确地引用jquery和jquery-ui的插件](https://forum.vuejs.org/topic/4976/%E5%A6%82%E4%BD%95%E5%9C%A8-vue-%E9%A1%B9%E7%9B%AE%E9%87%8C%E6%AD%A3%E7%A1%AE%E5%9C%B0%E5%BC%95%E7%94%A8-jquery-%E5%92%8C-jquery-ui%E7%9A%84%E6%8F%92%E4%BB%B6/2)



# vue-cli webpack全局引入jquery
1. 首先在`package.json`里加入，
   ```js
    dependencies:{
        "jquery" : "^2.2.3"
    }
   ```
    然后 nmp install
2. 在`webpack.base.conf.js`里加入
   ```js
    var webpack = require("webpack")
   ```
3. 在module.exports的最后加入
   ```js
    plugins: [
        new webpack.optimize.CommonsChunkPlugin('common.js'),
        new webpack.ProvidePlugin({
            jQuery: "jquery",
            $: "jquery"
        })
    ]
   ```
4. 然后一定要重新 **run dev**
5. 在main.js 引入就ok了
    ```
    import $ from 'jquery'
    ```

参考:[vue-cli怎么引入jquery](http://618cj.com/2016/08/24/vue-cli%E6%80%8E%E4%B9%88%E5%BC%95%E5%85%A5jquery/)

# 在.vue文件中引入第三方非NPM模块
```js
var Showbo = require("exports?Showbo!./path/to/showbo.js");
```
参考:[exports-loader](http://webpack.github.io/docs/shimming-modules.html#exporting)


# vue-cli引入外部文件
在`webpack.base.conf.js`中添加**externals**
![](https://segmentfault.com/img/bVvRpA)
externals 中 swiper 是键，对应的值一定的是插件 swiper.js 所定义的变量 Swiper :
![](https://segmentfault.com/img/bVvRpK)
![](https://segmentfault.com/img/bVvRpL)
之后再在根目录下的index.html文件里引入文件：`<script src="static/lib/swiper.js"></script>`
这样子就可以在需要用到swiper.js的文件里加入这行代码：`import Swiper from 'swiper'`，这样就能正常使用了。
参考: [https://segmentfault.com/q/1010000005169531?_ea=806312](https://segmentfault.com/q/1010000005169531?_ea=806312)
