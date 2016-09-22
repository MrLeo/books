# vue-router
## 参考
- [vue-router文档](http://router.vuejs.org/zh-cn/index.html)
- [使用Vue快速开发单页应用 vue-router](http://hiluluke.cn/2016/08/05/vue-router/)
- [Vue.js——vue-router 60分钟快速入门](http://www.cnblogs.com/keepfool/p/5690366.html)
    Demo:[https://github.com/keepfool/vue-tutorials/blob/master/06.Router/basic/basic_04.html](https://github.com/keepfool/vue-tutorials/blob/master/06.Router/basic/basic_04.html)

## 路由配置
路由配置其实是分两步的，第一步把vue-router的指令方法挂到Vue实例，第二步才是添加路由配置上。
```js
import Vue from 'vue'
import VueRouter from 'vue-router'
import App from 'App.vue'
Vue.use(VueRouter) // 第一步

//路由配置项:http://router.vuejs.org/zh-cn/options.html
const router = new VueRouter({
  hashbang = true,
  abstract = false,
  history = true,
  saveScrollPosition = true,
  transitionOnLoad = false,
  suppressTransitionError = false,
  root = null,
  linkActiveClass = 'v-link-active'
}) // 第二步

//路由映射: http://router.vuejs.org/zh-cn/api/map.html
router.map({
    '/': {
      name: 'index',
      title: '全部',
      component: (resolve) => require(['./components/main/index.vue'], resolve)
    },
    '/good': {
      name: 'good',
      title: '精华',
      component: (resolve) => require(['./components/main/index.vue'], resolve)
    }
  })
router.start(App, '#app')
```

## 路由参数
```js
import Home from 'components/Home'
import News from 'components/News'
import NewsDetail from 'components/NewsDetail'
import Message from 'components/Message'
import About from 'components/About'
router.map({
    '/home': {
        component: Home,
        subRoutes: {
            '/news': {
                name: 'news',
                component: News,
                subRoutes: {
                    'detail/:id': {
                        name: 'detail',
                        component: NewsDetail
                    }
                }
            },
            '/message': {
                component: Message
            }
        }
    },
    '/about': {
        component: About
    }
})
```

> `/:id`是路由参数。例如：如果要查看id = '01'的News详情，那么访问路径是/home/news/detail/01。

```html
<template id="home">
    <div>
        <ul class="nav nav-tabs">
            <li>
                <a v-link="{ name: 'news'}">News</a>
            </li>
            <li>
                <a v-link="{ path: '/home/message'}">Messages</a>
            </li>
        </ul>
        <router-view></router-view>
    </div>
</template>

<template id="news">
    <div>
        <ul>
            <li>
                <a v-link="{ name: 'detail', params: {id: '01'} }">News 01</a>
            </li>
            <li>
                <a v-link="{ path: '/home/news/detail/02'}">News 02</a>
            </li>
            <li>
                <a v-link="{ path: '/home/news/detail/03'}">News 03</a>
            </li>
        </ul>
        <div>
            <router-view></router-view>
        </div>
    </div>
</template>
```

> `<a v-link="{ name: 'news'}">News</a>`和`<a v-link="{ name: 'detail', params: {id: '01'} }">News 01</a>`这两行HTML代码，使用了用了具名路径。
> 
> `params: {id: '01'}`对应路由配置中的`/:id`，使用`this.$route.parames.id`接收params参数。
> 也可使用`query: {id: '01'}`传参，然后使用`this.$route.query.id`接收参数