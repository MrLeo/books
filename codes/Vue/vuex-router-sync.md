
问题：vuex-router-sync，干嘛用的？

https://github.com/vuejs/vuex-router-sync
Effortlessly keep vue-router and vuex store in sync.

在 尤大写的 hacknews-2.0 中

https://github.com/vuejs/vue-hackernews-2.0

---------- (1) 怎么 import ? 

https://github.com/vuejs/vue-hackernews-2.0/blob/master/src/app.js
import Vue from 'vue'
import App from './App.vue'
import store from './store'
import router from './router'
import { sync } from 'vuex-router-sync'
import * as filters from './filters'


---------- (2) 下例 vue檔案，使用此插件的 demo。
https://github.com/vuejs/vue-hackernews-2.0/blob/master/src/components/ItemList.vue
48:       displayedPage: isInitialRender ? Number(this.$store.state.route.params.page) || 1 : -1,
55:       return Number(this.$store.state.route.params.page) || 1


https://github.com/vuejs/vue-hackernews-2.0/blob/master/src/views/ItemView.vue
36:     ids: [store.state.route.params.id]

https://github.com/vuejs/vue-hackernews-2.0/blob/master/src/views/UserView.vue
24:     id: store.state.route.params.id


---------- (3)vuex-router-sync 语法解释


How does it work?

It adds a route module into the store, which contains the state representing the current route:
小凡：在 store 增加 route 模块，这个 state，含有 目前的 route 对象

store.state.route.path   // current path (string)
store.state.route.params // current params (object)
store.state.route.query  // current query (object)
When the router navigates to a new route, the store's state is updated.

store.state.route is immutable, 
小凡：store.state.route (不可变)

because it is derived state from the URL, 
小凡：因为 state 它来自 url

which is the source of truth. 
小凡：来源是真实的

You should not attempt to trigger navigations by mutating the route object. 
小凡：你不应该企图让 route对象变化，来触发转址功能

Instead, just call $router.go(). 
取而代之，使用 $router.go() 函数

Note that you can do $router.go({ query: {...}}) to update the query string on the current path.
注意：你能使用 $router.go({ query: {...}}) 这个命令，来更新目前 path 的 查询字串

