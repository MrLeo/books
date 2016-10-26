
# 修改的webpack配置文件

## 全局配置
### 修改 webpack.base.conf.js
打开 `~\build\webpack.base.conf.js` ，找到`entry`，添加多入口
```js
entry: {
    app: './src/main.js',
    app2: './src/main2.js',
    app3: './src/main3.js',
},
```
> 运行、编译的时候每一个入口都会对应一个`Chunk`

## run dev 开发环境 
### 修改 webpack.dev.conf.js
打开 `~\build\webpack.dev.conf.js` ，在`plugins`下找到`new HtmlWebpackPlugin`，在其后面添加对应的多页，并为每个页面添加`Chunk`配置
> `chunks: ['app']`中的app对应的是`webpack.base.conf.js`中`entry`设置的入口文件

```js
plugins:[
    // https://github.com/ampedandwired/html-webpack-plugin
    // 多页:index.html → app.js
    new HtmlWebpackPlugin({
      filename: 'index.html',//生成的html
      template: 'index.html',//来源html
      inject: true,//是否开启注入
      chunks: ['app']//需要引入的Chunk，不配置就会引入所有页面的资源
    }),
    // 多页:index2.html → app2.js
    new HtmlWebpackPlugin({
      filename: 'index2.html',//生成的html
      template: 'index2.html',//来源html
      inject: true,//是否开启注入
      chunks: ['app2']//需要引入的Chunk，不配置就会引入所有页面的资源
    }),
    // 多页:index3.html → app3.js
    new HtmlWebpackPlugin({
      filename: 'index3.html',//生成的html
      template: 'index3.html',//来源html
      inject: true,//是否开启注入
      chunks: ['app3']//需要引入的Chunk，不配置就会引入所有页面的资源
    })
]
```

## run build 编译
### 修改 config/index.js
打开`~\config\index.js`，找到`build`下的`index: path.resolve(__dirname, '../dist/index.html')`，在其后添加多页
```js
build: {
    index: path.resolve(__dirname, '../dist/index.html'),
    index2: path.resolve(__dirname, '../dist/index2.html'),
    index3: path.resolve(__dirname, '../dist/index3.html'),
},
```

### 修改 webpack.prod.conf.js
打开`~\build\webpack.prod.conf.js`，在`plugins`下找到`new HtmlWebpackPlugin`，在其后面添加对应的多页，并为每个页面添加`Chunk`配置
> `HtmlWebpackPlugin` 中的 `filename` 引用的是 config/index.js 中对应的 `build`
```js
plugins: [
    // 多页:index.html → app.js
    new HtmlWebpackPlugin({
        filename: config.build.index,
        template: 'index.html',
        inject: true,
        minify: {
            removeComments: true,
            collapseWhitespace: true,
            removeAttributeQuotes: true
            // more options:
            // https://github.com/kangax/html-minifier#options-quick-reference
        },
        // necessary to consistently work with multiple chunks via CommonsChunkPlugin
        chunksSortMode: 'dependency',
        chunks: ['manifest','vendor','app']//需要引入的Chunk，不配置就会引入所有页面的资源
    }),
    // 多页:index2.html → app2.js
    new HtmlWebpackPlugin({
        filename: config.build.index2,
        template: 'index2.html',
        inject: true,
        minify: {
            removeComments: true,
            collapseWhitespace: true,
            removeAttributeQuotes: true
        },
        chunksSortMode: 'dependency',
        chunks: ['manifest','vendor','app2']//需要引入的Chunk，不配置就会引入所有页面的资源
    }),
    // 多页:index3.html → app3.js
    new HtmlWebpackPlugin({
        filename: config.build.index3,
        template: 'index3.html',
        inject: true,
        minify: {
            removeComments: true,
            collapseWhitespace: true,
            removeAttributeQuotes: true
        },
        chunksSortMode: 'dependency',
        chunks: ['manifest','vendor','app3']//需要引入的Chunk，不配置就会引入所有页面的资源
    }),
]
```




> **参考:**
> [小凡哥视频 - 讲解 vuejs2 ，使用 vue-cli 怎么搭起 多页应用](http://www.bilibili.com/video/av6805317/)