# 启动
开发的时候启动webpack热替换
```
npm run dev
```

# 端口
默认端口号是`8080`
如果希望修改端口号，则进入`~\config\index.js`，修改`dev`下的`port`为希望启动的端口号
```
例如:  port: 80,
```

# 跨域
## webpack+Express
进入`~\config\index.js`，在`dev`下的`proxyTable`就是网址映射
```js
proxyTable: {
  '/api': {
    target: 'http://localhost:6060',//要跨域访问的API域名
    rewrite: function(req) {
        //可以用正則方式替代掉，這樣往後 /api/xxx/xxx 之類的網址，就會自動匹配了
        req.url = req.url.replace(/^\/api/, '');
    }
  }
}
```
這樣當你呼叫 `/api` 時：
```js
this.$http.get('/api')
```
就會幫你自動導向 `http://localhost:8080/api`，是為了當 Server 和 前端 不在同個網域或是Port時，可以方便調試，例如我 Server 在 `localhost:6060`，前端在 `localhost:5050` ，就可以直接調用 `/api`，而不用每次都要加上完整網址
更多信息可参考:[https://webpack.github.io/docs/webpack-dev-server.html#proxy](https://webpack.github.io/docs/webpack-dev-server.html#proxy)

## Fetch.js
参考地址:[http://wwsun.github.io/posts/fetch-api-intro.html](http://wwsun.github.io/posts/fetch-api-intro.html)

## ngrok