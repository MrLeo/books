# 数据请求:vue-resource

## 参考
- [vue-resource docs](https://github.com/vuejs/vue-resource/tree/master/docs)
- [Vue.js——vue-resource全攻略](http://www.cnblogs.com/keepfool/p/5657065.html)

## 支持的HTTP方法
> - get(url, [options])
> - head(url, [options])
> - delete(url, [options])
> - jsonp(url, [options])
> - post(url, [body], [options])
> - put(url, [body], [options])
> - patch(url, [body], [options])

## 示例
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