#### 1、Vue起步

* 渐近式框架：由浅入深、由简单到复杂地使用。
* 优势：代码体积小，基于虚拟DOM，数据双向绑定，生态圈繁荣。
* 可以胜任Web开发、移动端开发、跨平台APP开发。
* 两种安装方式：script标签引入、vue-cli脚手架工程化安装。
* HelloWorld:
	* new Vue()
	* 文本插值 {{ }}
* Vue实例：
	* 响应式体验，动态地改变Vue实例数据：app.msg = "hello 1912"
* Vue指令初体验：
	v-text 插入文本
	v-model 绑定表单的值
	v-on / @  绑定事件
* [在线编码 JSFiddle](https://jsfiddle.net/boilerplate/vue)

#### 2、Vue指令

* 文本类指令
	* 文本用 `{{}}`，用`v-text`优化显示效果
	* 纯HTML，用`v-html`
	* `v-html` ，可以防止XSS,CSRF攻击
	* 表达式，在指令中可以使用js表达式
	* `v-once` 只渲染一次
```
  {{}} 文本插值
  v-text 插入文本
  v-html 插入HTML片段
  v-once 只渲染一次
```

* 动态属性、动态样式
	* 动态样式：`v-bind:class` 和 `v-bind:style`
	* 它们都支持数组语法
	* 它们也支持对象语法
  * `v-bind:`可简写`:`
```
  v-bind:title
  v-bind:class="{ active: isActive, 'text-danger': hasError }"
  v-bind:class="[isActive ? activeClass : '', errorClass]"
  v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }"
  v-bind:style="[baseStyles, overridingStyles]"
```


* 列表渲染
```
  v-for="(item, index) in arr"
  v-bind:key="index"
```

* 对象渲染
```html
<div v-for="(value, name, index) in obj">
  {{ index }}. {{ name }}: {{ value }}
</div>
```

* 条件渲染  
  * 重点区分v-if 和 v-show的区别
	* 前者条件为false时，元素将从DOM中被移除
	* 后者是用`display:none`来实现显示隐藏的
```
  v-if
  v-else-if
  v-else
  v-show
```


* 事件绑定（事件对象，事件修饰符）
	* 事件处理：`v-on`，简写`@`，灵活使用事件修饰符、键盘修饰符等
	* v-on:click
	* @click.stop
```
<div @click='say("hi", $event)'></div>
```

* 事件修饰符
  * `.stop` :阻止单击事件继续传播，同阻止冒泡event.stopPropagation()
  * `.prevent` :提交事件不再重载页面，同阻止事件的默认行为event.preventDefault()
  * `.capture` :添加事件监听器时使用事件捕获模式
  * `.self` :只当在 event.target 是当前元素自身时触发处理函数
  * `.once` :点击事件将只会触发一次
  * `.passive` :滚动事件的默认行为 (即滚动行为) 将会立即触发
```html
<!-- 阻止单击事件继续传播 -->
<a v-on:click.stop="doThis"></a>
<!-- 提交事件不再重载页面 -->
<form v-on:submit.prevent="onSubmit"></form>
<!-- 修饰符可以串联 -->
<a v-on:click.stop.prevent="doThat"></a>
<!-- 只有修饰符 -->
<form v-on:submit.prevent></form>
<!-- 添加事件监听器时使用事件捕获模式 -->
<!-- 即内部元素触发的事件先在此处理，然后才交由内部元素进行处理 -->
<div v-on:click.capture="doThis">...</div>
<!-- 只当在 event.target 是当前元素自身时触发处理函数 -->
<!-- 即事件不是从内部元素触发的 -->
<div v-on:click.self="doThat">...</div>
<!-- 使用修饰符时，顺序很重要；相应的代码会以同样的顺序产生。 -->
<!-- 因此，用 v-on:click.prevent.self 会阻止所有的点击， -->
<!-- 而 v-on:click.self.prevent 只会阻止对元素自身的点击。 -->
<!-- 点击事件将只会触发一次 -->
<a v-on:click.once="doThis"></a>
<!-- 滚动事件的默认行为 (即滚动行为) 将会立即触发 -->
<!-- 而不会等待 `onScroll` 完成  -->
<!-- 这其中包含 `event.preventDefault()` 的情况 -->
<div v-on:scroll.passive="onScroll">...</div>
<!-- 不要把 .passive 和 .prevent 一起使用，因为 .prevent 将会被忽略， -->
<!-- 同时浏览器可能会向你展示一个警告。 -->
<!-- 请记住，.passive 会告诉浏览器你不想阻止事件的默认行为。 -->
```

* 按键修饰符
  * `.enter`
  * `.tab`
  * `.delete` (捕获“删除”和“退格”键)
  * `.esc`
  * `.space`
  * `.up`
  * `.down`
  * `.left`
  * `.right`
  * `.number`（keyCode attribute）
```html
<!-- 只有在 `key` 是 `Enter` 时调用 `vm.submit()` -->
<input v-on:keyup.enter="submit">
<!-- 你可以直接将 KeyboardEvent.key 暴露的任意有效按键名转换为 kebab-case 来作为修饰符 -->
<!-- 在下述示例中，处理函数只会在 $event.key 等于 PageDown 时被调用 -->
<input v-on:keyup.page-down="onPageDown">
<!-- 使用 keyCode attribute 也是允许的 -->
<input v-on:keyup.13="submit">
```

* 系统修饰键
  * `.ctrl`
  * `.alt`
  * `.shift`
  * `.meta`
```html
<!-- Alt + C -->
<input @keyup.alt.67="clear">
<!-- Ctrl + Click -->
<div @click.ctrl="doSomething">Do something</div>
```

* `.exact`修饰符
  * .exact 修饰符允许你控制由精确的系统修饰符组合触发的事件
```html
<!-- 即使 Alt 或 Shift 被一同按下时也会触发 -->
<button @click.ctrl="onClick">A</button>
<!-- 有且只有 Ctrl 被按下的时候才触发 -->
<button @click.ctrl.exact="onCtrlClick">A</button>
<!-- 没有任何系统修饰符被按下的时候才触发 -->
<button @click.exact="onClick">A</button>
```

* 表单绑定（表单修饰符）
	* `.lazy` :失去焦点同步一次，在“change”时而非“input”时更新
	* `.number` :格式化数字
	* `.trim` : 去除首尾空格
	* `v-model` 等价于 `v-bind:value`+`v-on:input`
```
  v-model.trim=''
  v-model.number=''
  v-model.lazy=''
```

* TodoList项目实践

  * [原型](http://www.todolist.cn/)
  * `v-model` 表单数据绑定
  * `v-on` / `@` 事件绑定
  * `v-for` 列表渲染
  * 列表渲染：`v-for` 与 `:key`的使用
	* 变异方法：push() pop() shift() unshift() splice() sort() reverse()
	* 非变异方法：filter(), concat() 和 slice() ,map()


#### 3、Vue生命周期
```js
beforeCreate: function() {
	console.log('beforeCreate')
},
created: function() {
	console.log('created')
},
beforeMount: function() {
	console.log('beforeMount')
},
mounted: function() {
	console.log('mounted')
	// 在这里调接口、创建swiper组件等操作
},
beforeUpdate: function() {
	console.log('beforeUpdate')
},
updated: function() {
	console.log('updated')
},
beforeDestroy: function() {
	console.log('beforeDestroy')
	// 在这里清除耗费性能的东西，比如定时器等
},
destroyed: function() {
	console.log('destroyed')
}
```

* 各种接口请求等操作， 建议放在`mounted` 这个钩子函数里。
* 需要完整的DOM结构才能做初始化渲染的第三方UI相关的库，它们的业务逻辑都要放在`mounted`这里调用、执行。
* 定时器清除等，可以放在`beforeDestroy`中进行执行。
* 使用 `app.$destroy()` 手动触发组件销毁，组件销毁之后它的各种指令都将失效。
* swiper插件库的使用：`https://www.swiper.com.cn/`

* 其它钩子函数

```js
//被 keep-alive 缓存的组件激活时调用
activated: function() {
  console.log('activated')
},
//被 keep-alive 缓存的组件停用时调用
deactivated: function() {
  console.log('deactivated')
},
//当捕获一个来自子孙组件的错误时被调用
//此钩子会收到三个参数：错误对象、发生错误的组件实例以及一个包含错误来源信息的字符串
//此钩子可以返回 false 以阻止该错误继续向上传播
errorCaptured: function(err,Com,str) {
  console.log('err',err)
  console.log('Com',Com)
  console.log('str',str)
}
```

#### 4、响应式原理

```js
var app = {}
// 把普通对象的定义，转化成setter/getter方式进行对象定义
Object.defineProperty(app, 'msg', {
  get: function() {
	return value
  },
  set: function(arg) {
	value = arg
	// 在setter操作里面，通知监听器，更新页面
	watch(value)
  }
})

// 当页面数据发生变化时，更新对象，触发setter操作

document.getElementById('input').addEventListener('keyup', function(e){
  // 触发setter
  app.msg = e.target.value
})

// 监听器
function watch(value) {
  document.getElementById('msg').innerHTML = value
}
```


#### 5、虚拟DOM

* 什么是MVP、MVC、MVVM模式？
	* M  model数据
	* V  view视图
	* C  control控制器
* 如何理解MVVM？
	* VM 即视图模型，你可以理解为虚拟DOM
* 什么是虚拟DOM？
	虚拟DOM就是一个json对象，它用于对真实DOM进行描述。
* 什么是diff运算？
	当Vue实例中的数据发生变化时，Vue会获得一份对虚拟DOM的拷贝，如此我们就有两份虚拟DOM，一份是数据变化前的虚拟DOM，一份是数据变化后的虚拟DOM。所谓的Diff运算，就是对这两份虚拟DOM进行差异比较，从而找出它们的最小差异。再把这份最小的差异渲染到真实DOM中去。
	MVVM框架，基于这种虚拟DOM的Diff运算，大大地减少了DOM的频繁操作，减少DOM操作本身就是一种性能优化。所以MVVM框架有利于性能优化，非常适合数据化的产品应用开发。
	
	
#### 6、自定义组件/插槽

什么是Vue自定义组件？
* 组件化的目的：扩展 HTML 元素，封装可重用的代码

如何自定义组件？
* 使用 `Vue.component('my-button', {})` 进行全局组件的注册
* template:`<div></div>`，只能有一个根元素。
* props,实现从父组件向子组件动态传值，在子组件中可以 props进行多重验证，比如`type``required`等。
* data,它必须使用一个工厂函数进行返回，目的为了解决作用域问题
* methods,使用自定义事件，实现子组件向父组件的传值通信（$emit）
* 组件也可以用<component is='组件名'></component>来渲染
```html
<div id='app'>
  <my-component v-model='msg'></my-component>
  <!-- <my-component :msg='msg' @aaa='bbb'></my-component>--><!-- 自定义事件 -->
  <!-- <component is='my-component'></component>-->
</div>
```
```js
//全局组件
Vue.component('my-component',{
  props:{
    value:{
      type:String,//设置传值类型
      require:true,//设置是否必填
      default:[],//设置默认值，如果require:false，且值为空，则值为默认值
      validator: function (value) {   //自定义验证
              return value >= 0
            }
    }
    //msg:{
    //  type:String
    //}
  },
  data:function(){
    return {
      list:[]
    }
  },
  template:`<div>
  <div v-text='msg'></div>
  <button @click='change'>改为aaa</button>
  </div>`,
  methods:{
    change(){
      this.$emit('input','newMsg')//将父组件的msg的值更新为'aaa'
      //this.$emit('aaa','newMsg') 自定义事件传值
    }
  }
})
//
var app = new Vue({
  el:'#app',
  data:{
    msg:'msg'
  },
  methods:{
    //bbb(val){
    //  console.log(val)
    //  this.msg=val
    //}
  }
})
```


自定义表单类的组件：
* 自定义表单组件的封装，原理是`v-model`等价于`:value`和 `@input`。
* 自定义input组件
* 自定义select组件
* 自定义radio组件
* 自定义checkbox组件
* 自定义类表单组件

使用slot插槽自定义组件：
* 使用 slot 插槽，扩展自定义组件
* v-slot指令用在template标签上，指定具名插槽
* 每个插槽都有独立的作用域，可以进行动态传值
* 多插槽
```html
<div id='app'>
  <my-layout>

    <!-- 这个插槽的名字叫 default -->
    <template v-slot:default='scope'>
      <h4 v-text='scope.msg'></h4>
    </template>

    <!-- v-slot可以简写成 # -->
    <template #aside='scope'>
      <h4 v-text='scope.info'></h4>
    </template>

    <!-- slot传值，仅在自己的slot中有效，有作用域限制 -->
    <template v-slot:main='scope'>
      <h4 v-text='scope.item.a'></h4>
      <h4 v-text='scope.item.b'></h4>
    </template>

    <!-- 这个插槽的名字叫 footer -->
    <template v-slot:footer>
      <h4>底部</h4>
    </template>

  </my-layout>
</div>
```
```js
Vue.component('my-layout', {
  data: function() {
    return {
      msg: '小明',
      info: 'Hello',
      item: {
        a: '1111',
        b: '2222'
      }
    }
  },
  template: `
  <div class='container'>

    <div class='header'>
      <slot v-bind:msg='msg'></slot>
    </div>

    <div class='aside'>
      <slot name='aside' :info='info'></slot>
    </div>

    <div class='main'>
      <slot name='main' :item='item'></slot>
    </div>

    <div class='footer'>
      <slot name='footer'></slot>
    </div>

  </div>
  `
})
var app = new Vue({
  el: '#app',
  data: {}
})
```
* 只有一个插槽
```html
<div id='app'>
  <!-- 当组件内无内容时，显示slot内预设内容'this default'-->
  <my-com></my-com>
  <!-- 当组件内有内容时，显示正常内容-->
  <my-com>aaa</my-com>
</div>
```
```js
Vue.component('my-com',{
  template:`<div>
              <p>up</p>
              <slot>this default</slot>
              <p>down</p>
            </div>`
})
var app = new Vue({
  el: '#app',
  data: {}
})
```

#### 7、Vue选项/computed/watch

* Vue实例与选项
	* data 声明式渲染
	* 自定义组件的 props / template
	* methods 方法事件
	* 计算属性`computed`
	* 侦听器`watch`
	* 生命周期与钩子函数

* 计算属性 computed
	* 使用计算属性，替代复杂的模板表达式，让代码更加容易维护
	* 计算属性是基于它们的依赖进行缓存的。
	* 计算属性只有在它的相关依赖发生改变时才会重新求值

* 侦听器 watch
	* 所侦听的data数据，有任何一个发生变化，侦听器都会被触发、执行
```html
<div id='app'>
  <div>
    当前页面变化了<span v-text='count'></span>次
  </div>
  <input type="text" v-model='firstname'>
  <input type="text" v-model='lastname'>
  <h3 v-text='fullname'></h3>
  <input type="text" v-model.number='price'>
  <input type="text" v-model.number='num'>
  <h3 v-text='total'></h3>
</div>
```
```js
var app = new Vue({
  el: '#app',
  data: {
    firstname: '',
    lastname: '',
    price: 0,
    num: 0,
    count: 0
  },
  computed: {
    fullname () {
      return this.firstname + ' ' + this.lastname
    },
    total () {
      return this.price * this.num
    }
  },
  watch: {
    // firstname (val) {
    //   console.log('firstname 发生了变化', val)
    // },
    // lastname (val) {
    //   console.log('lastname 发生了变化', val)
    // },
    fullname (val) {
      // console.log('fullname 发生了变化', val)
      this.count++
    },
    total (val) {
      this.count++
    }
  }
})
```

#### 8、全局组件和局部组件
```js
//全局组件
Vue.component('my-com',{
  template:`<div>aaa</div>`
})
//局部组件
var app = new Vue({
  el:'#app',
  components:{
    'my-com':{
      template:`<div>aaa</div>`
    }
  }
})
```

#### 9、keep-alive状态保留
```html
<div id='app' class='app'>

  <!-- 第一种实现tab选项卡的方式 -->
  <!-- 当Tab切换时，组件的状态会重置 -->
  <!-- <div>
    <my-home v-if='curPage==1'></my-home>
    <my-find v-else-if='curPage==2'></my-find>
    <my-user v-else></my-user>
  </div> -->

  <!-- 使用动态组件实现tab选项卡 -->
  <!-- 当Tab切换时，组件的状态会保留 -->
  <keep-alive>
    <component :is='comp'></component>
  </keep-alive>

  <div class="tabs">
    <span @click='tabChange("my-home")'>首页</span>
    <span @click='tabChange("my-find")'>发现</span>
    <span @click='tabChange("my-user")'>我</span>
  </div>
</div>
```
```js
var app = new Vue({
  el: '#app',
  data: {
    curPage: 1,
    comp: 'my-home'
  },
  components: {
    'my-home': {
      data: function() {
        return {
          home: ''
        }
      },
      template: `
      <div>
        <h3>首页</h3>
        <input type="text" v-model='home'>
      </div>
      `
    },
    'my-find': {
      data: function() {
        return {
          find: ''
        }
      },
      template: `
      <div>
        <h3>发现</h3>
        <input type="text" v-model='find'>
      </div>
      `
    },
    'my-user': {
      data: function() {
        return {
          user: ''
        }
      },
      template: `
      <div>
        <h3>我</h3>
        <input type="text" v-model='user'>
      </div>
      `
    }
  },

  methods: {
    tabChange(name) {
      // this.curPage = idx
      this.comp = name
    }
  }
})
```

#### 10、异步组件
```js
Vue.component('my-async-component', function(resolve, reject) {
  setTimeout(function(){
    resolve({
      template: `<h1>我是异步组件</h1>`
    })
  }, 5000)
})
```

#### 11、mixin混入
* 全局混入

```html
<div id='app1'>
  <my-global-component></my-global-component>
  <h1 v-text='msg'></h1>
</div>
<div id='app2'>
  <my-global-component></my-global-component>
  <h1 v-text='msg' @click='click'></h1>
</div>
```
```js
// 全局混入
Vue.mixin({
  created() {
    console.log('created')
  },
  mounted() {
    console.log('mounted')
  },
  data: function() {
    return {
      msg: 1
    }
  },
  methods: {
    click() {
      alert('全局混入的click方法')
    }
  }
})
// 全局组件
Vue.component('my-global-component', {
  template: `<h1>全局组件 <span v-text='msg'></span></h1>`
})

var app1 = new Vue({
  el: '#app1',
  data: {
    msg: 2
  }
})

var app2 = new Vue({
  el: '#app2',
  methods: {
    click() {
      alert('这是我自己的click方法')
    }
  }
})
```

* 局部混入

```html
<div id='app1'>
  <h1 v-text='msg'></h1>
  <h1 v-text='username'></h1>
</div>
<div id='app2'>
  <h1 v-text='username'></h1>
</div>
```
```js
// 局部混入
var mixin = {
  created() {
    console.log('created')
  },
  mounted() {
    console.log('mounted')
  },
  data: function() {
    return {
      msg: 1
    }
  },
  methods: {
    click() {
      alert('局部的mixin的click方法')
    }
  }
}
// 局部混入
var obj = {
  data: function() {
    return {
      username: '1916'
    }
  }
}

var app1 = new Vue({
  el: '#app1',
  mixins: [mixin, obj]
})

var app2 = new Vue({
  el: '#app2',
  mixins: [obj]
})
```

#### 11、filter过滤器
```html
<div id='app'>
  <!-- 过滤器可以用在两个地方：双花括号插值和 v-bind 表达式 -->
  <h1>{{no | student}}</h1><!-- <h1>SZ19161137878</h1> -->
  <h1>{{money | rmb}}</h1><!-- <h1>￥10500</h1> -->
</div>
```
```js
// 全局过滤器，一次定义，所有组件中都可以用
Vue.filter('rmb', function(value) {
  return '￥'+value
})

var app = new Vue({
  el: '#app',
  data: {
    no: '19161137878',
    money: 10500
  },
  // 局部过滤器
  filters: {
    student: function(value) {
      return 'SZ'+value
    }
  }
})
```

#### 12、ref dom节点绑定（减少使用）
```html
<div id='app'>
  <input type='text' value='msg' ref='input' />
  <button @click='getVal'></button>
</div>
```
```js
var app = new Vue({
  el:'#app',
  methods:{
    getVal(){
      console.log(this.$refs.input.value)//msg
    }
  }
})
```

#### 13、directive自定义指令
* 钩子函数
  * bind：只调用一次，指令第一次绑定到元素时调用。在这里可以进行一次性的初始化设置。
  * inserted：被绑定元素插入父节点时调用 (仅保证父节点存在，但不一定已被插入文档中)。
  * update：所在组件的 VNode 更新时调用，但是可能发生在其子 VNode 更新之前。指令的值可能发生了改变，也可能没有。但是你可以通过比较更新前后的值来忽略不必要的模板更新。
* 钩子函数参数
  * el：指令所绑定的元素，可以用来直接操作 DOM
  * binding：一个对象，包含以下属性：
    * name：指令名，不包括 v- 前缀。
    * value：指令的绑定值，例如：v-my-directive="1 + 1" 中，绑定值为 2。
    * oldValue：指令绑定的前一个值，仅在 update 和 componentUpdated 钩子中可用。无论值是否改变都可用。
    * expression：字符串形式的指令表达式。例如 v-my-directive="1 + 1" 中，表达式为 "1 + 1"。
    * arg：传给指令的参数，可选。例如 v-my-directive:foo 中，参数为 "foo"。
    * modifiers：一个包含修饰符的对象。例如：v-my-directive.foo.bar 中，修饰符对象为 { foo: true, bar: true }。
  * vnode：Vue 编译生成的虚拟节点。移步 VNode API 来了解更多详情。
  * oldVnode：上一个虚拟节点，仅在 update 和 componentUpdated 钩子中可用。
  
```html
<div id='app'>
  <input type="text" v-focus>
  <hr>

  <h3 v-color='"orange"'>我们是1916班</h3>
  <h3 v-color='"red"'>我们是1916班</h3>
  <h3 v-color='"#0000ff"'>我们是1916班</h3>
  <h3 v-color='color'>我们是1916班</h3>
</div>
```
```js
// 全局指令
Vue.directive('focus', {
  inserted: function(el) {
    el.focus()
  }
})

var app = new Vue({
  el: '#app',
  data: {
    color: '#096720'
  },
  // 局部指令
  directives: {
    color: {
      inserted: function(el, binding) {
        console.log(binding)
        el.style.color = binding.value
      }
    }
  }
})
```

#### 14、bus 事件总线
```html
<div id='app' class='app'>
  <div>
    <child-a></child-a>
  </div>
  <div>
    <child-b></child-b>
  </div>
</div>
```
```js
// 事件总线，通过“订阅-发布”模式实现组件之间的直接通信
var bus = new Vue()
// bus.$emit('频道',msg)              发射消息
// bus.$on('频道',function(msg){})    收到消息

Vue.component('child-a', {
  data: function() {
    return {
      msg: '',
      html: ''
    }
  },
  template:`
  <div>
    <input type="text" v-model='msg' @keyup.enter='send'>
    <button @click='send'>发送</button>
    <div v-html='html'></div>
  </div>
  `,
  methods: {
    send() {
      // 发送消息
      bus.$emit('childA', this.msg)
      this.msg = ''
    }
  },
  created() {
    var that = this
    bus.$on('childB', function(msg) {
      that.html += '<div>B说：'+msg+'</div>'
    })
  }
})

Vue.component('child-b', {
  data: function() {
    return {
      msg: '',
      html: ''
    }
  },
  template:`
  <div>
    <input type="text" v-model='msg' @keyup.enter='send'>
    <button @click='send'>发送</button>
    <div v-html='html'></div>
  </div>
  `,
  methods: {
    send() {
      bus.$emit('childB', this.msg)
      this.msg = ''
    }
  },
  created() {
    var that = this
    bus.$on('childA', function(msg) {
      that.html += '<div>A说：'+msg+'</div>'
    })
  }
})

var app = new Vue({
  el: '#app'
})
```

#### 15、transition过渡&动画
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <link href="https://cdn.jsdelivr.net/npm/animate.css@3.5.1" rel="stylesheet" type="text/css">
  <style>
    .xxx-enter-active, .xxx-leave-active {
      transition: opacity .5s;
    }
    .xxx-enter, .xxx-leave-to {
      opacity: 0;
    }

    .fade-enter-active, .fade-leave-active {
      transition: opacity 1.5s;
    }
    .fade-enter, .fade-leave-to {
      opacity: 0;
      color: red;
    }
  </style>
</head>
<body>

  <div id="app">

    <!-- 使用自定义的动画 -->
    <button @click='show1=!show1'>显示/隐藏</button>
    <transition name='xxx'>
      <div v-show='show1'>
        <h1>我是用来演示动画的-1</h1>
      </div>
    </transition>

    <hr>

    <!-- 使用animate.css动画，工作中常用 -->
    <button @click='show2=!show2'>显示/隐藏</button>
    <transition
      enter-active-class="animated tada"
      leave-active-class="animated bounceOutRight">
      <div v-show='show2'>
        <h1>我是用来演示动画的-2</h1>
      </div>
    </transition>

    <hr>

    <!-- 学习使用mode属性 -->
    <!-- 注意要给元素指定key值 -->
    <button @click='show3=!show3'>显示/隐藏</button>
    <transition name='fade' mode='out-in'>
      <div v-if='show3' key='1'>
        <h1>我是用来演示动画的-3</h1>
      </div>
      <div v-else key='2'>
        <h1>我是用来演示动画的-4</h1>
      </div>
    </transition>


  </div>


  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
  <script>
    var app = new Vue({
      el: '#app',
      data: {
        show1: true,
        show2: true,
        show3: true
      }
    })
  </script>

</body>
</html>
```



--------------------------------------------------

#### 1、dpr设备像素比

* 设备像素比：DPR(devicePixelRatio)  dpr=1/2/3
* dpr = 屏幕像素 / 设备物理像素
* 使用`window.devicePixelRatio`可以动态地获取到硬件设备的dpr


#### 2、关于移动端Web

* [使用WebApp meta标签](https://guide.aotu.io/docs/html/webapp.html)
* 使用rem布局时，一定要指定这个`meta`标签，示例如下：
```html
<meta name="viewport" content="width=device-width,initial-scale=1.0">
```


#### 3、rem移动端布局（root）

* 在`public/index.html`中引入这个`rem.js`文件，把根字体设置成html宽度的十分之一。
```js
function resetRootFZ(){
  var oHtml = document.querySelector('html');
  var w = oHtml.getBoundingClientRect().width;
  oHtml.style.fontSize = w/10 + 'px';
};
resetRootFZ();
window.addEventListener('resize',function(){
  resetRootFZ();
});
```
* 在编辑器中安装px转换rem的插件，并设置其fontSize=75，在写代码时就可以自动地把px单位转化成rem单位。
* [教程：VScode中如何将px转rem](https://blog.csdn.net/wjnf012/article/details/92074232)


#### 4、Touch事件

* Click事件在移动端，会有300毫秒延迟，用于区分移动设备上的单击、双击事件。
* 给网页指定WebApp meta元数据后，可以降低click事件延迟时间。
* Touch事件由`touchstart``touchmove``touchend`组件，仅在移动端Web中被支持，在PC Web中不支持。



--------------------------------------------------

#### 1、服务端渲染

* [Vue.js 服务器端渲染指南](https://ssr.vuejs.org/zh/)
* SSR与BSR的优劣势对比
* SSR有利于搜索引擎优化(SEO)，页面的加载速度会更快(解决首页加载慢的问题)

#### 2、Nuxt.js框架

* [Nuxt.js入门指南](https://zh.nuxtjs.org/guide/installation)
* 使用`create-nuxt-app`脚手架
* [Nuxt项目的配置说明](https://zh.nuxtjs.org/guide/configuration)
* Nuxt路由：Nuxt.js 依据 pages 目录结构自动生成 vue-router 模块的路由配置。
* 声明式路由：<nuxt-link>，支持`active-class`属性。
* Nuxt嵌套路由：创建内嵌子路由，你需要添加一个 Vue 文件，同时添加一个与该文件同名的目录用来存放子视图组件。
* Nuxt动态路由：必须加下划线 (文件夹也可以加下划线(多级嵌套)， 文件也可以加下划线)。
* 编程式路由：`this.$router.push()`等等。
* Nuxt视图：在layout目录下的 default.vue 即根组件的模板了，用<nuxt>指定视图容器。
* Nuxt子视图：<nuxt-child>用于渲染二级的子视图组件。
* 在Nuxt项目中使用axios请求后端数据，使用`asyncData`属性。
```js
// 异步数据请求
  asyncData() {
    return axios.get(url).then(res=>{
      // 这里是无法访问当前组件的this对象
      console.log('this', this)
      console.log('res34', res.data.data.song.list.length)
      // 在这里return 的数据，在页面组件中可以直接使用
      return {
        list: res.data.data.song.list
      }
    })
  }
```
* 在Nuxt项目中使用Vuex，Nuxt项目建议Vuex状态分模块（即多个module）。
```
export const state = () => ({
  list: [1,2,3,4,5]
})
export const mutations = {
  add (state, payload) {
    state.list.push(payload)
  },
  remove (state, { todo }) {
    state.list.splice(state.list.indexOf(todo), 1)
  },
  toggle (state, todo) {
    todo.done = !todo.done
  }
}
```

#### 3、项目部署

* 云服务器介绍
* 域名、IP地域、DNS域名解析器、域名备案等

* 如何把本地代码转移至远程服务器上？使用Git，或者使用其它文件上传软件。
* 如何部署前端项目？使用Nginx
* 什么是反向代理？什么是正向代理？
