# 参考
- [Webpack——令人困惑的地方](https://segmentfault.com/a/1190000005089993)

# package.json
```js
{
    "name": "项目名称", //项目名称
    "version": "1.0.0", //版本
    "description": "vue+webapck", //描述
    "author": "Leo", //作者
    "license": "MIT", //开源协议
    "main": "index.js", //主文件
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "start": "webpack-dev-server --inline --hot --port 8090"
    }, //scripts指定了运行脚本命令的npm命令行缩写，比如这是的start指定了运行npm run start时，所要执行的命令。
    "dependencies": { //项目依赖
        "vue": "^1.0.21",
        "babel-runtime": "^6.0.0",
        "vue-resource": "^0.6.1",
        "vue-router": "^0.7.11"
    },
    "devDependencies": { //各种各样的loader，用来解析想相应的文件格式。要解析vue并且完成相应的功能，这些基本都是必须的。
        "autoprefixer-loader": "^2.0.0",
        "babel": "^6.3.13",
        "babel-core": "^6.3.21",//ES2015 babel 編譯核心
        "babel-loader": "^6.2.0",//編譯匯入 ES2015 類型的檔案
        "babel-plugin-transform-runtime": "^6.3.13",//polyfilling
        "babel-preset-es2015": "^6.3.13",//es2015 語法
        "babel-preset-stage-0": "*",//開啟草稿階段的功能
        "babel-runtime": "^5.8.34",//babel 執行環境
        "file-loader": "^0.8.5",//編譯匯入檔案類型的資源
        "html-loader": "^0.3.0",
        "css-loader": "^0.16.0",//編譯匯入 css
        "style-loader": "^0.12.3",//把編譯後的 css 整合進 html
        "node-sass": "^3.4.2",
        "sass-loader": "^3.2.0",
        "less": "^2.7.1",
        "less-loader": "^2.2.3",
        "url-loader": "^0.5.6",//編譯匯入檔案類型的資源，把檔案轉成 base64 等
        "vue-style-loader": "*",//編譯 vue 樣式部分
        "vue-html-loader": "^1.2.0",//編譯 vue 的 template 部份
        "vue-loader": "^7.2.0",//編譯匯入 vue 元件檔案
        "vue-hot-reload-api": "*",//Hot reload API for Vue components
        "webpack": "^1.12.0",//webapck 核心程式
        "webpack-dev-server": "^1.14.0",//開發伺服器
        "webpack-merge": "*"//合併設定檔使用
    },
    "keywords": [ //关键字
        "vue",
        "webpack"
    ]
}
```

# webpack.config.js
```js
var path = require('path');
// NodeJS中的Path对象，用于处理目录的对象，提高开发效率。
// 模块导入
module.exports = {
    // 入口文件地址
    entry: {
        app: './src/main.js'
    },
    // 输出
    output: {
        path: path.join(__dirname, './dist'),
        // 文件地址，使用绝对路径形式
        filename: '[name].js',
        //[name]这里是webpack提供的根据路口文件自动生成的名字
        publicPath: '/dist/'
        // 公共文件生成的地址
    },
    // 服务器配置相关，自动刷新!
    devServer: {
        historyApiFallback: true,
        hot: false,
        inline: true,
        grogress: true,
    },
    // 加载器
    module: {
        //忽略:不编译的js文件
        noParse: [
            /node_modules\/video.js\/dist\/video.js/,//正则表达式
        ],
        // 加载器
        loaders: [
            // 解析.vue文件
            { test: /\.vue$/, loader: 'vue' },
            // 转化ES6的语法
            { test: /\.js$/, loader: 'babel', exclude: /node_modules/ },
            // 编译css并自动添加css前缀
            { test: /\.css$/, loader: 'style!css!autoprefixer'},
            //.scss 文件想要编译，scss就需要这些东西！来编译处理
            //install css-loader style-loader sass-loader node-sass --save-dev
            { test: /\.scss$/, loader: 'style!css!sass?sourceMap'},
             // LESS
            { test: /\.less$/, loader: 'style!css!less' },
            // 图片转化，小于8K自动转化为base64的编码
            { test: /\.(png|jpg|gif)$/, loader: 'url-loader?limit=8192'},
            //html模板编译？
            { test: /\.(html|tpl)$/, loader: 'html-loader' },
        ]
    },
    // .vue的配置。需要单独出来配置，其实没什么必要--因为我删了也没保错，不过这里就留这把，因为官网文档里是可以有单独的配置的。
    vue: {
        loaders: {
            css: 'style!css!autoprefixer',
        }
    },
    // 转化成es5的语法
    babel: {
        presets: ['es2015'],
        plugins: ['transform-runtime']
    },
    resolve: {
        // require时省略的扩展名，如：require('module') 不需要module.js
        extensions: ['', '.js', '.vue'],
        // 别名，可以直接使用别名来代表设定的路径以及其他
        alias: {
            filter: path.join(__dirname, './src/filters'),
            components: path.join(__dirname, './src/components')
        }
    },
    // 开启source-map，webpack有多种source-map，在官网文档可以查到
    devtool: 'eval-source-map'
};
```