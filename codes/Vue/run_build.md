
# 发布服务器
进入项目所在目录运行
```
npm run build
```

# 修改build生成的静态文件路径
进入`~\config\index.js`
在`build`下的`assetsPublicPath`默认情况下是`'/'`，此时打包的index.html文件中的资源文件(js、css、img)默认情况都是以`/`开头的绝对路径，指向http服务器的根路径
如果想修改为相对路径则需要将`assetsPublicPath`的值修改为`'./'`，这样就是指向index.html的相对路径了

# 部署SPA
> 将打包生成好的项目部署到服务器，但是访问SPA项目的前端路由会出现`404`，这是由于HTTP服务器默认情况下访问的是对应目录下的index.html，此时需要对HTTP服务器做下路由映射，将前端路由地址映射到index.html。

以下是SPA项目常用的几种部署方式:
*例如前端路由地址:[http://localhost/live/292/wonderful](http://localhost/live/292/wonderful)*

## Apache
如果只使用Apache做HTTP服务器，可以设置Apache的url重定向，将所有的请求路由到index.html
1. 打开`~\Apache\conf\httpd.conf`文件
2. 去除httpd.conf文件中`LoadModule rewrite_module modules/mod_rewrite.so`前面的`#`号
3. 在httpd.conf文件中添加重定向规则
```
RewriteEngine on 
# 当访问路由地址为 /live 开头的，则将路由重定向到 /index.html
RewriteRule \/live.*$ /index.html
```

## nginx
使用nginx做反向代理服务器，配置文件参考：
```
server {
    listen 80;
    server_name localhost:80;
    index  index.html;
    root /wwwroot/;
    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

## node.js
使用node.js做反向代理服务器，配置文件参考：
```
var config = require("./webpack.config.js");
var webpack = require("webpack")
var webpackDevServer=require("webpack-dev-server")

config.entry.unshift("webpack-dev-server/client?http://localhost:80", "webpack/hot/dev-server");
var compiler = webpack(config);

var server = new webpackDevServer(compiler, {
  contentBase: "build",
  hot: true,
  inline: true,
  historyApiFallback: true,
  proxy: {
        '/*': {
            target: 'loaclhost:8080/',
            secure: false
        },
    }
});

server.listen(80);
```

# 参考
- [Vue-router子页面刷新404](http://forum.vuejs.org/topic/215/vue-router子页面刷新404)
- [Apache Rewrite url重定向功能的简单配置](http://www.jb51.net/article/24435.htm)
- [webpack构建的项目的部署问题](https://segmentfault.com/q/1010000006757292)
- [vue实现spa实例讲解：前后分离](http://www.jianshu.com/p/32259952a5a8)