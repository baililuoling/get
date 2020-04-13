# vue-project

created at 2020-3-21

## 工程架构

当我们创建一个新项目，或者是从仓库里拉取到一个旧项目时。
* README.md
* package.json

### 脚手架的使用

* [Vue CLI 脚手架](https://cli.vuejs.org/zh/)

```
// 创建项目

npm install @vue/cli -g
vue create vue-project

// 项目启动
npm install
npm run serve  或  npm start

// 项目执行ESLint检测与修复
npm run lint

// 项目打包上线
// 会生成一个 /dist 目录，把这个目录发给运维工程就可以了
// .map这个是静态资源的映射关系的配置文件
npm run build
```


### ESLint/JSLint

* [ESLint官网](https://eslint.bootcss.com/)
* ESLint 这样的可以让你在编码的过程中发现问题，并且可以自己创建检测规则，保持代码编写风格的一致性。
* Vue项目中，如何修改ESLint验证规则？在package.json文件中配置：

```
"eslintConfig": {
	"rules": {
		"no-console": 0
	}
}
```

* ESLint规则的配置，有三种处理级别，分别是`error-2  warn-1  off-0`
* 在package.json中配置完成后，要重启服务器才能生效。




## 项目结构说明

### 1、项目结构介绍

* `src` 开发目录
	* `src/main.js` 程序的入口文件
	* `src/App.vue` App组件
	* `scr/components` 组件目录
	* `src/assets` 程序的静态资源目录
* `public` 本地服务器的静态资源目录
* `dist`目录，执行`npm run build`所生成的目录

### 2、单文件组件

* [Vue单文件组件](https://cn.vuejs.org/v2/guide/single-file-components.html)
* 为什么要使用单文件？有哪些优势？
* `<template></template>`放置HTML模板
* `<script></script>`放置js代码
* `<style></style>`放置样式代码
* 一个`.vue`文件就是一个组件

### 3、绝对路径

```js
//@符表示从src开始
import Com from '@/components/Com.vue'
```

## 项目架构

### 使用 SASS

* [Sass官网](https://www.sass.hk/)

```
//  建议使用 cnpm 进行安装
cnpm install sass-loader -D
cnpm install node-sass -D
```
```
<style lang="scss" scoped> //加scoped把css样式只作用在当前组件，原理是在标签上加了一个唯一的hash属性
	@import '@/assets/css/common.scss';
	.page {
	  > button {
	    font-size: $btnSize;
	    color: $color;
	  }
	  > div {
	    button {
	      color: $color2;
	    }
	  }
	  > .box1 {
	    .btn {
	      border: .03rem solid red;
	    }
	  }
	}
</style>
//module也能解决样式冲突,原理是将class名red替换成一个唯一的class名
<template>
  <div class='red'>233</div>//修改前
  <div :class='$style.red'>233</div>//修改后
</template>
<style lang="scss" module>
	.red{
    color: red;
  }
</style>
```

* 如果因为网络原因，node-sass安装失败，使用下面命令进行安装

```
npm install node-sass --sass_binary_site=https://npm.taobao.org/mirrors/node-sass/
```

* [node-sass 安装失败报错的原因及解决办法(整理)](https://www.cnblogs.com/gitnull/p/10188030.html)
* [Less官网](http://lesscss.cn/)

### Vue-Router路由

* 什么是SPA单页面程序？SPA应用有哪些优点和缺点？

#### 开始使用路由

```
// Vue-Router的安装
npm install vue-router -S
```

```js
// /src/router.js
import Vue form 'vue'
import VueRouter from 'vue-router'
Vue.use(VueRouter)
const router = new VueRouter({
  // mode: 'history',  // 切换VueRouter的路由模式
  routes: [
    {
      path: '/todo',   // 当路由是 /todo时，渲染TodoList组件；下面的同理
      component: TodoList,
      name: 'todo'
    }
  ]
})
export default router
// 在main.js引入，在Vue实例化时，进行挂载
import router from './router'
new Vue({
	router,
	render: h=>h(App)
}).$mount('#app')
```

* 路由实现，使用`router-view`和`router-link`组件

```
<div class="navbar">
	<!-- 声明式路由 -->
	<!-- to 指定要跳转至哪个路由 -->
	<!-- tag 指定用什么HTML标签来替换渲染router-link -->
	<!-- activeClass 指定导航选项卡的高亮样式 -->
  <!-- exact表示完全匹配 -->
	<router-link to='/todo' tag='span' activeClass='on' exact>TodoList</router-link>
</div>

<!-- 在这里承载一级路由所对应的组件，在这里渲染一线路由所对应的组件 -->
<router-view></router-view>
<!-- <router-view name='geek'></router-view> -->
```

#### 动态路由

* 路由传参`/detail/:id`

```js
//编程式路由
this.$router.push('/detail/'+item.id)
//声明式路由
<router-link :to='"/detail/"+item.id' tag='span' activeClass='on'>TodoList</router-link>
```

* 参数获取`this.$route.params`

* 捕获所有路由

```
{
  path:'/*'
}
```

#### 嵌套路由（二级路由），使用路由的`children`字段

```
<!-- 组件中添加一个 <router-view> -->
const User = {
  template: `
    <div class="user">
      <h2>User {{ $route.params.id }}</h2>
      <router-view></router-view>
    </div>
  `
}
```

```js
const router = new VueRouter({
  routes: [
    { path: '/user/:id', component: User,
      children: [
        {
          // 当 /user/:id/profile 匹配成功，
          // UserProfile 会被渲染在 User 的 <router-view> 中
          path: 'profile',
          component: UserProfile
        },
        {
          // 当 /user/:id/posts 匹配成功
          // UserPosts 会被渲染在 User 的 <router-view> 中
          path: 'posts',
          component: UserPosts
        }
      ]
    }
  ]
})
```

* 当你访问 /user/foo 时，User 的出口是不会渲染任何东西，这是因为没有匹配到合适的子路由。
* 如果你想要渲染点什么，可以提供一个 空的 子路由：

```js
const router = new VueRouter({
  routes: [
    {
      path: '/user/:id', component: User,
      children: [
        // 当 /user/:id 匹配成功，
        // UserHome 会被渲染在 User 的 <router-view> 中
        { path: '', component: UserHome },

        // ...其他子路由
      ]
    }
  ]
})
```

#### 编程式的导航

* this.$router.push

```
<!-- 声明式 -->
<router-link :to="...">	
<!-- 编程式 -->
// 字符串
this.$router.push('/home')

// 对象
this.$router.push({ path: '/home' })

// 命名的路由
this.$router.push({ name: 'user', params: { userId: '123' }})

// 带查询参数，变成 /register?plan=private
this.$router.push({ path: '/register', query: { plan: 'private' }})
```

* 如果提供了 path，params 会被忽略，上述例子中的 query 并不属于这种情况。
* 取而代之的是下面例子的做法，你需要提供路由的 name 或手写完整的带有参数的 path：

```
const userId = '123'
router.push({ name: 'user', params: { userId }}) // 当路由设置为/user -> /user，当路由设置为/user/:userId -> /user/123，两种情况传参一样，只是路径显示不同
router.push({ path: `/user/${userId}` }) // -> /user/123
// 这里的 params 不生效
router.push({ path: '/user', params: { userId }}) // -> /user
```

* 只有显示在路径上的参数刷新不会丢失



* this.$router.replace
* 替换掉当前的 history 记录，不会向 history 添加新记录

```
<!-- 声明式 -->
<router-link :to="..." replace>
<!-- 编程式 -->
router.replace(...)
```

* this.$router.go(n)
* 这个方法的参数是一个整数，意思是在 history 记录中向前或者后退多少步，类似 window.history.go(n)

```
// 在浏览器记录中前进一步，等同于 history.forward()
router.go(1)

// 后退一步记录，等同于 history.back()
router.go(-1)

// 前进 3 步记录
router.go(3)

// 如果 history 记录不够用，那就默默地失败呗
router.go(-100)
router.go(100)
```

* 你也许注意到 router.push、 router.replace 和 router.go 
* 跟 window.history.pushState、 window.history.replaceState 和 window.history.go好像，
* 实际上它们确实是效仿 window.history API 的

#### 路由命名与别名与重定向

* 路由命名，即给路由取一个名称，用一个变量值代表路由

```
{
	path: '/film/:id',
	component: Film,
	name: 'myfilm',		// 路由的名称
}
```
```js
this.$router.push({name: 'myfilm', params: {id:123}})
<!-- 或 -->
<router-link :to="{name: 'myfilm', params: {id:123}}">User</router-link>
<!-- 这两种方式都会把路由导航到 /film/123 路径 -->
```

* 路由别名，/a 的别名是 /b，意味着，当用户访问 /b 时，URL 会保持为 /b，但是路由匹配则为 /a，就像用户访问 /a 一样

```
{ 
  path: '/a',
  component: A,
  alias: '/b'   //路由/a的别名
}
```

* 重定向
* 注意：导航守卫并没有应用在跳转路由上，而仅仅应用在其目标(/404)上

```
{
  path:'/404',
  component:NotFound,
  name:'404'
},
{
  path:'/*',
  redirect:'/404'     //当路由匹配到/*时，路由将重定向到/404
  //redirect:{name:'404'}  可以是一个命名的路由
  //redirect: to => {      甚至是一个方法
      // 方法接收 目标路由 作为参数
      // return 重定向的 字符串路径/路径对象
    }}
}
```

#### 命名视图

* 当访问/film路径时，name=a的视图容器承载FilmA组件，name=b的视图承载FilmB组件，无name属性的视图容器承载默认组件Film

```html
<router-view></router-view>
<router-view name='a'></router-view>
<router-view name='b'></router-view>
```
```
{
	path: '/film',
	components: {
    default:Film,
		a: FilmA,
		b: FilmB
	}
}
```


#### History与Hash模式(https://router.vuejs.org/zh/guide/essentials/history-mode.html)

* 前端有两种路由方案，分别是History模式和Hash模式，Vue-Router默认使用Hash模式。
* 使用Vue-Router的 mode选项，可以改变其路由模式。
* History模式时，打包部署到服务端，需要后端配合对路由进行处理，否则会报404，其本质是由`history.pushState`来实现的。
* Hash模式，Url中拼接了一个`#`符，部署服务端没有404这个问题，其本质是由`location.hash`来实现的。

#### 导航守卫(https://router.vuejs.org/zh/guide/advanced/navigation-guards.html)

##### 全局前置守卫router.beforeEach
* to: Route: 即将要进入的目标 路由对象
* from: Route: 当前导航正要离开的路由
* next: Function: 一定要调用该方法来 resolve 这个钩子。执行效果依赖 next 方法的调用参数。

```js
let router = new VueRouter({})
// 路由守卫，全局的路由拦截
let isLogin = false
// 在路由匹配成功之前
router.beforeEach((to, from, next) => {
  if (to.path === '/order') {
    if (!isLogin) {
      // 如果用户没有登录，跳转至 /login
      next('/login')
    } else {
      // 已登录，直接通过
      next()
    }
  } else {
    next()
  }
})

export default router
```

##### 局部前置守卫beforeRouteEnter

```js
// 在组件的内部，实现路由拦截，即局部守卫
export default {
  // 局部的路由守卫，路由拦截
  // 箭头函数的写法
  beforeRouteEnter(to, from, next) {
    let isLogin = true
    if (!isLogin) {
      // 如果用户没有登录，跳转至 /login
      next('/login')
    } else {
      // 已登录，直接通过
      next()
    }
  }
}
```

* 其它

```js
beforeRouteEnter (to, from, next) {
  // 在渲染该组件的对应路由被 confirm 前调用
  // 不！能！获取组件实例 `this`
  // 因为当守卫执行前，组件实例还没被创建
},
beforeRouteUpdate (to, from, next) {
  // 在当前路由改变，但是该组件被复用时调用
  // 举例来说，对于一个带有动态参数的路径 /foo/:id，在 /foo/1 和 /foo/2 之间跳转的时候，
  // 由于会渲染同样的 Foo 组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用。
  // 可以访问组件实例 `this`
},
beforeRouteLeave (to, from, next) {
  // 导航离开该组件的对应路由时调用
  // 可以访问组件实例 `this`
}
```

##### 路由独享的守卫beforeEnter

```js
const router = new VueRouter({
  routes: [
    {
      path: '/foo',
      component: Foo,
      //同全局前置守卫
      beforeEnter: (to, from, next) => {
        // ...
      }
    }
  ]
})
```

##### 全局解析守卫router.beforeResolve
* 这和 router.beforeEach 类似
* 区别是在导航被确认之前，同时在所有组件内守卫和异步路由组件被解析之后，解析守卫就被调用

##### 全局后置钩子router.afterEach
* 你也可以注册全局后置钩子，然而和守卫不同的是，这些钩子不会接受 next 函数也不会改变导航本身：

```js
router.afterEach((to, from) => {
  // ...
})
```

#### 路由懒加载

```js
//引入组件时将
import Foo from './Foo.vue'
//替换为
const Foo = () => import('./Foo.vue')
```

### 使用Element(https://element.eleme.cn/#/zh-CN)

```js
// npm install element-ui -S
// 全局安装element
// 在 main.js 中写入以下内容：
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';
Vue.use(ElementUI);
//组件中就可以直接使用
```

### 使用Vuex状态管理工具

```
npm install vuex -S
```

```js
// /src/store/index.js
import Vue from 'vue'
import Vuex from 'vuex'
vue.use(Vuex)
const store = new Vuex.Store({
  // 状态、数据，组件取数据例this.$store.state.msg
  state:{
    msg:'msg',
    count:0,
    arr:[1,2,3],
    obj:{
      a:4,
      b:5,
      c:6
    }
  },
  //计算属性，类似于computed，组件取数据用this.$store.getters.msg2
  getters:{
    msg2(state){
      return state.msg+'1916'
    }
  },
  // 同步方法，这是改变state的唯一方式，组件调用例this.$store.commit('add',10)，payload为要传的参数，可不写
  mutations:{
    add(state, payload){
      console.log(payload)  //10
      state.count += payload
    },
    changeMsg(state, payload){
      state.msg = payload
    }
  },
  // 异步方法，所有调取后端接口的api，都在这里封装，组件调用例this.$store.dispatch('aaa','bbb')，payload为要传的参数，可不写
  actions:{
    aaa(store, payload){
      console.log(payload)  //bbb
      setTimeout(()=>{
        store.commit('changeMsg','hello msg')
      },1500)
    }
  }
})
export default store
// 在main.js引入，在Vue实例化时，进行挂载
import store from './store'
new Vue({
	store,
	render: h=>h(App)
}).$mount('#app')
```

* modules分模块

```js
const moduleA = {
  // 如果是分模块来管理store，一定要加这个属性
  namespaced: true,
  state: { msga:'msgaaa',msg:'msgaa' },
  mutations: { ... },
  actions: { ... },
  getters: { ... }
}

const moduleB = {
  // 如果是分模块来管理store，一定要加这个属性
  namespaced: true,
  state: { msgb:'msgbbb' },
  mutations: { ... },
  actions: { ... }
}

const store = new Vuex.Store({
  modules: {
    a: moduleA,
    b: moduleB
  }
})

store.state.a // -> moduleA 的状态
store.state.b // -> moduleB 的状态

//取模块数据this.$store.state.模块名.数据   this.$store.getters.模块名.数据   
//调用方法this.$store.commit('模块名/方法名')  this.$store.dispatch('模块名/方法名')
```

* 其它使用方法

```js
//组件中script内引入vuex，可挂载在组件中直接使用数据和方法
import { mapState, mapGetters, mapMutations, mapActions } from 'vuex'
export default {
  computed:{
    ...mapState(['msg','count']),  //取数据直接用this.msg，this.count
    ...mapGetters(['msg2']),       //取数据直接用this.msg2
    ...mapState('a',['msga'])      //取模块a里的数据this.msga，getters同理
    
  },
  methods:{
    ...mapMutations(['add']),      //使用方法this.add(参数)
    ...mapActions(['aaa']),        //使用方法this.aaa(参数)
    ...mapActions('b',[ ... ]),    //取模块b的actions方法，mutations同理
    
    //命名冲突解决方法示例
    ...mapState('orderStore', {
      orderMsg: (state)=>state.msg         //将orderStore模块的msg自定义名为orderMsg使用
    }),
    ...mapMutations('orderStore', {
      changeOrderMsg: (commit, payload)=>{
        commit('changeMsg', payload)       //将orderStore模块的changeMsg自定义名为changeOrderMsg使用
      }
    }),
    ...mapActions('orderStore', {
      getOrderMusic: (dispatch, payload)=>{
        dispatch('getMusic', payload)      //将orderStore模块的getMusic自定义名为getOrderMusic使用
      }
    }),
  }
}
```

* 五个核心概念：state, mutations, actions, getters, modules
* 当分多个modules时，每个module都要手动指定 namespaced:true 命名空间。
* 多modules时，尽量避免命名冲突，以减少代码的复杂度。


### axios的使用(https://www.jianshu.com/p/7a9fbcbb1114)

```
npm install axios -S
```

* 直接使用

```js
import axios from 'axios'
//get请求
axios.get('http://bit.ly/2mTM3nY?a=1&b=2').then(res=>{}).catch(err=>{})
axios.get('http://bit.ly/2mTM3nY',{
  params:{a:1,b:2}
}).then(res=>{}).catch(err=>{})
axios({
  method:'get',
  url:'http://bit.ly/2mTM3nY',
  params: {a:1,b:2}
}).then(res=>{}).catch(err=>{})
//post请求
axios.post('http://bit.ly/2mTM3nY',{
  username: 'aaa',
  password: '123'
}).then(res=>{}).catch(err=>{})
axios({
  method:'post',
  url:'http://bit.ly/2mTM3nY',
  data: {
  username: 'aaa',
  password: '123'
  }
}).then(res=>{}).catch(err=>{})
```

* 前后端分离项目，在工程化环境一般使用axios调接口
* axios非常轻量级，并且支持Promise
* axios的使用，必须预先封装，要配置请求拦截器和响应拦截器
* 在请求拦截器中，比如添加token等
* 在响应拦截器中，对响应数据进行预先过滤，以失败的情况进行统一处理。

```js
//axios封装
// /src/api/fetch.js
import axios from 'axios'
import { Message } from 'element-ui'

// 测试:http://localhost:9090
// 上线:http://baidu.com
// 如果url不是绝对路径，那么会将baseURL和url拼接作为请求的接口地址
var baseURL = 'http://localhost:9090'

// 这是axios实例
const fetch = axios.create({
  baseURL: baseURL,
  timeout: 7000,
  headers: {
    'Content-Type': 'application/json;charset=UTF-8'
  }
})

// 添加请求拦截器，发生在请求发起之前
fetch.interceptors.request.use(config => {
  console.log('请求拦截，ajax发起请求之前', config)
  var token = localStorage.getItem('token')
  config.headers.Authorization = token   // 用户鉴权
  return config
})


// 添加响应拦截器，发生客户端接收数据之前
fetch.interceptors.response.use(response => {
  var res = {}
  console.log('响应拦截，ajax接收数据之前', response)
  if (response.data && response.data.code===0) {
    res = response.data.data || {}
  } else {
    var msg = response.data.message || '请求错误'
    Message({
      message: msg,
      type: 'error',
      duration: 3 * 1000
    })
  }
  return res
}, error => {
  // 调接口失败时，弹个框提示一个用户
  const msg = error.Message !== undefined ? error.Message : ''
  Message({
    message: '网络错误' + msg,
    type: 'error',
    duration: 3 * 1000
  })
  return Promise.reject(error)
})

export default fetch
```

```js
// 使用封装后的axios
// /src/api/api.js
import fetch from './fetch'
export function fetchList(params) {
  // 返回Promise
  return fetch({
    method: "GET",
    params: params,
    url: '/youzan/getGoodList'
  })
}

export default {
  fetchList
}
```

* 小技巧

```js
// /src/main.js
// 把所有接口方法，都放在$http对象上
import http from './api/api'
Vue.prototype.$http = http
//组件中可以用this.$http.fetchList调用fetchList方法
```

### webpack 相关(https://cli.vuejs.org/zh/guide/webpack.html)

```js
//在项目根目录下(与package.json同级)新建vue.config.js
module.exports = {
  // 配置本地服务的反向代理
  devServer: {
    // 自定义端口号
    port: 9090,
    proxy: {
      '/soso': {
        //当路径匹配到/soso时，/soso之前的路径将被替换成https://c.y.qq.com
        target: 'https://c.y.qq.com',
        changeOrigin: true
      }
    }
  }
}

```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
