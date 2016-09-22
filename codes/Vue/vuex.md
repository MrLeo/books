# Vuex学习


## 参考
- [使用 Vuex + Vue.js 构建单页应用](https://segmentfault.com/a/1190000005891026)

- [使用Vue.js和Vuex实现购物车场景](https://segmentfault.com/a/1190000005780326)
    [vue-demo-collection](https://github.com/xiaoluoboding/vue-demo-collection)

## 配置Vuex
在`src`下创建一个文件夹叫做`vuex`。里面定义三个文件。
### `mutation-types.js` 定义类型的

```js
// src/vuex/mutation-types.js
export const SET_HEADER_TITLE = 'SET_HEADER_TITLE'
```

### `actions.js` 操作，可以分解成多个文件

```js
// src/vuex/actions.js
/**
 * 用统一的函数处理并分发mutations。
 * @param type
 * @returns {function({dispatch: *}, ...[*]): *}
 */
function makeAction (type) {
    return ({ dispatch }, ...args) => dispatch(type, ...args)
}

import {
    SET_HEADER_TITLE
} from './mutation-types'

/**
 * actions
 */
export const setTitle = makeAction(SET_HEADER_TITLE)
```

### `store.js` 入口文件，在根组件调用，然后所有子组件可以共享数据。

```js
// src/vuex/store.js
import Vue from 'vue'
import Vuex from 'vuex'
//import createLogger from 'vuex/logger'

Vue.use(Vuex)
//Vue.config.debug = true
//const debug = process.env.NODE_ENV !== 'production'

// 导入各个模块的初始状态和 mutations
import index from './modules/index'
export default new Vuex.Store({
    // 组合各个模块
    modules: {
        index
    },
    //strict: debug,
    //moddlewares: debug ? [createLogger()] : []
})
```

### `modules/index.js` 只是例子用的，一个index的操作，需要定义数据的状态和mutation。`actions.js`只是分发操作。
```js
// src/vuex/modules/index.js
import {
    SET_HEADER_TITLE
} from '../mutation-types'

const state = {
    title: 'default',
    info: {
        name:''
    }
}

const mutations = {
    [SET_HEADER_TITLE](state, newTitle) {
        state.title = newTitle
    }
}

export default {
    state,
    mutations
}
```

## 挂载store
```js
// src/App.vue
import store from './vuex/store'
import HeaderComponent from './components/header'
import FooterComponent from './components/footer'
export default {
    store,
    components: {
        HeaderComponent,
        FooterComponent
    }
}
```

## 获取数据及操作
```js
// src/components/header.vue
// 从vuex拿数据，然后渲染到页面上
// 如果需要修改可以调用setTitle
import { setTitle } from '../vuex/actions'
export default {
    vuex: {
        //获取vuex状态数据
        getters: {
            title: state => state.title,
            info: ({index}) => index.info
        },
        //状态变更事件
        actions: {
            setTitle
        }
    }
}
```