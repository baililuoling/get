# react

created at 2020-3-29

## 起步

* 用于构建用户界面的 JavaScript 库
* 声明式  组件化  一次学习，随处编写
* react特点 简洁 灵活

## 环境搭建

* 建立一个项目的目录，在目录中 npm init -y 会在目录中产生一个文件package.json
* npm i  react --save (或yarn add react) 会在目录中有一个node_modules目录，找到react目录，找到这个目录下的umd目录，拷贝umd目录下react.development.js到自己的js目录下
* npm i react-dom --save(或 yarn add react-dom)在node_modules目录下找到react-dom目录，在这个目录下找到umd目录，在react-dom／umd目录下找到react-dom.development.js文件拷贝到自己的js目录下
* npm i babel-standalone --save（或yarn add babel-standalone）在node_modules目录下找到babel-standalone目录拷贝这个目录下的babel.js 到js目录下
* 引入顺序
  * react.development.js
  * react－dom.development.js
  * babel.js
* 注意这个问题，script的type属性指定为 text/babel
* babel
  * es6转为es5
  * 解析jsx
* jsx
  * 是一种语法糖 
  * jsx是javascript扩展的意思
  * 相当于  js+xml
  * jsx 不是必须的，但是用jsx可以提高开发效率
  * jsx的原理就是  React.createElement(tag,{attrs},content)
* react 差值表达式是一个{ }
* jsx 注意事项
  * 对象不能直接渲染,数组以字符串的形式进行渲染
  * jsx中 class 改为className
  * 事件的首字母要大写 onXxx 形式
* react当中遍历列表要指定key值，可以使用map方法进行映射
* 遍历列表的时候，注意标签的语义化
* return 后面要有字符

```js
//html
//<div id="box"></div>
class 组件名 extends React.Component{
  constructor(props){
    super(props)  //构造函数，等价于this.props=props
    this.state ={
       key:value
    }
  }
  render(){
    // this  常用的属性 state props refs 不常用 context
    // state 是组件内部的数据  props 来自组件外部的数据  refs 标识一个组件的节点
    return (jsx表达式)
  }
}
//挂载在dom节点上
ReactDom.render(<组件名/>,document.getElementById('box'))
```

## 组件

```js
//无状态组件
const 组件名=(props)=>{
  return (jsx表达式)
}
//类组件
class 组件名 extends React.Component{
  render(){
    return (jsx表达式)
  }
}
```

## this.props.children组件嵌套

```js
//无状态组件
const 组件=(props)=>{
  return (
    <div>{props.children}</div>
  )
}

//类组件
class 组件 extends React.Component{
  //没有 undefined 一个 Object 多个Array
  console.log(this.props.children)
  render(){
    return (
      <div>{this.props.children}</div>
    )
  }
}

<组件>
  <子组件 />
</组件>
```

## setState

* 更新state状态
* 异步操作
* 会触发render更新组件
* 连续执行对象会合并

```js
//连续执行多次对象会合并
this.setState({
  key:newValue
},()=>{
  console.log('更新后的回调函数，可不写')
})
//连续执行多次会放入队列中依次执行
this.setState((prevState,props)=>{//prevState是前一个状态，props是来自组件外部的数据，可不写
  return {
    key:newValue
  }
},()=>{
  console.log('更新后的回调函数，可不写')
})
```

## ref绑定节点

```js
//方法一
<node ref='自定义属性' />
//获取节点
this.refs.自定义属性

//方法二（推荐）
<node ref={(表示节点的变量（任意写）)=>this.自定义属性=表示节点的变量}/>
//获取节点
this.自定义属性
```

## context见day10

```js

```

## 事件绑定处理函数，要进行传参数

* this.方法名字.bind(this,参数)
* 事件处理函数的最后一个参数时事件对象

## dangerouslySetInnerHTML

* 可以渲染html的字符串

```
<div dangerouslySetInnerHTML={{__html:html的字符串}}></div>
```

## 脚手架环境

* npm i create-react-app -g  全局安装
* create-react-app -V  查看版本号
* create-react-app 项目名字  创建项目
* npm start  启动项目
* src/index.js就是入口文件

```
//引入图片
import 变量 from '图片路径';
<img src={变量} />
或
<img src={require('图片路径')} />

//导出导入
//情形一
export default aaa
import 自定义名 from '路径'
//情形二
export aaa
export bbb
import {aaa,bbb} from '路径'
或
import {aaa as 自定义名,bbb} from '路径'
或
import * as 自定义名 from '路径'
```

* yarn 和npm 命令对比表格[npm to yarn](https://yarn.bootcss.com/docs/migrating-from-npm/)
* 改端口
  * 项目的目录/node_modules/react-scripts/scripts/start.js
  * 代码const DEFAULT_PORT = parseInt(process.env.PORT, 10) || 5000;
* eslint[配置文档](https://www.codercto.com/a/13256.html)

## jsx的规则

* value 改为defaultValue
* checked 改为 defaultChecked
* onclick 改为 onClick
* for 改为htmlFor
* style 写对象
* class className
* {/*注释*/}

## ref的第三种使用方式

```
import { createRef } from 'react'

this.state={
  变量: createRef()
}

<node ref={this.state.变量} />

this.state.变量.current 就可以引用这个节点了
```

## 组件传值

* 父--》子  通过属性传递
* 子--》父   调用父组件传递过来的方法来实现的。传递的数据放到参数里去
* 兄弟组件传值  状态提升，将要传的值放在同一父级上，由父级传给各子级

## 代理

* 正向代理   开发环境
* 反向代理   上线环境
* 配置文件的路径
  * 项目目录下/node_modules/react-scripts/config/webpackDevServer.config.js

```js
proxy:{
    "/weather":{
         target:"http://www.weather.com.cn",
         changeOrigin:true,
         "pathRewrite":{
           "^/weather":"/"
         }
    }
}
```

## 弹射 eject

* yarn eject 不能撤销  
* 如果弹射后出错，重装依赖

## 生命周期函数

* 挂载阶段四个钩子函数的执行次序
  * constructor(props,context)
  * static getDerivedStateFromProps(props,state)
  * render()
  * componentDidMount()
    * 可获取DOM节点
    * 一般用于做初始化

```
Derived State  派生状态
静态方法不能用this,调用是用 类.静态方法名()
this.state ={
    a:props.n    //派生状态(derivedState)
}

static getDerivedStateFromProps(props,state){  //返回对象更新状态
    return {
        a: props.n  
    }
}
```

* 更新阶段的钩子函数
  * static getDerivedStateFromProps(props, state)
  * shouldComponentUpdate(nextProps,nextState)
    * 默认返回true
    * 返回true 就会render
    * 返回false 不会render
    * 可以加条件减少不必要的渲染，增加性能
  * render()
  * getSnapshotBeforeUpdate(prevProps,prevState)
    * 必须和componentDidUpdate一起用
    * 必须返回一个值，componentDidUpdate的最后一个参数接收这个值
    * 不能和旧版的钩子函数一起使用
    * 目的是为了返回数据更新前的dom状态
  * componentDidUpdate(prevProps,prevState,snapshot)
    * 监控组件里的数据的变化，可以单独用

* 卸载阶段的钩子函数
  * componentWillUnmount()
    * 一般用于关闭定时器，事件监听和清除缓存

### 卸载组件

```js
//从节点卸载组件
import ReactDOM from 'react-dom';
ReactDOM.unmountComponentAtNode(document.getElementById("root"))
```

### 性能优化，减少不必要的渲染

* shouldComponentUpdate(nextProps,nextState)

```js
shouldComponentUpdate(nextProps){
  return  nextProps.flag!==this.props.flag  //新值和旧值不等才渲染
}
```

* PureComponent

```js
//进行浅比对，进行性能的优化 （纯组件）
import { PureComponent } from 'react'
class Item extends PureComponent {
  ...
}
```

* React.memo(组件)

```js
//对无状态组件用 React.memo(组件)
import React from 'react'
export default React.memo(组件)
```

* 其它优化

```js
componentWillUnmount(){  //解决异步数据回来时,组件却卸载了
  //重写组件的setState方法，直接返回空
  this.setState = (state,callback)=>{
    return;
  };
}
```

## Fragment空标记

```js
import { Fragment } from 'react'
return (
  <Fragment>
    <div>aaa</div>
    <div>bbb</div>
  </Fragment>
)
//或
return (
  <>
    <div>aaa</div>
    <div>bbb</div>
  </>
)
```

## 设置props默认值

```js
//类组件
static  defaultProps ={
   key：默认值
}

//无状态组件
组件名.defaultProps ={
   key:默认值
}
```

## 设置props限定类型

```js
import { PropTypes } from 'prop-types'//react脚手架中无需下载

//类组件
static propTypes={
  key:PropTypes.类型
}

//无状态组件
组件名.propTypes={
  key:PropTypes.类型.isRequired//加isRequired表示必须传
}
```

## forceUpdate 强制刷新

## fetch

```js
fetch("http://localhost:4000/list").then((res)=>res.json()).then((res)=>{
    this.setState({
        list:res
    })
})
```

## 非父子组件传值pubsub-js

* npm i pubsub-js --save  安装

```js
import PubSub from 'pubsub-js'
PubSub.publish("事件名","数据")//事件发布
PubSub.subscribe("事件名",(evt,data)=>{ })//事件监听，evt是事件名，data是接收的数据
```

## sass

* npm i node-sass sass-loader -D  安装
* 安装后就可以直接使用sass

## public目录下的图片

```
//直接写路径
<img src="/img.png" />
```

## hook

* useState 在无状态组件里也可以使用状态

```js
import { useState } from 'react';
//let [数据名,修改数据的函数名] = useState(数据的初始值)
//例
let [type,modifyType] = useState('aaa')
console.log(type)//aaa
modifyType('bbb')//每次调用都会刷新组件
console.log(type)//bbb
```

## 路由(router)[官网](https://reacttraining.com/react-router/web/guides/quick-start)

### 起步

* 后端路由: 根据用户的请求返还不通的内容
* 前端路由：根据不同的url 去切换组件
* npm install react-router-dom --save  安装
* import {...} from 'react-router-dom'  引入组件

### 两种模式

* 两种模式
  * 历史纪录模式  BrowserRouter
  * hash模式     HashRouter 
  
```
//如果部署到nginx服务器上 用BrowserRouter  (config /nginx.conf)
location / {
    try_files $uri $uri/ /index.html;
}
```

* 引入

```js
//src/index.js
import {BrowserRouter as Router} from 'react-router-dom'
ReactDOM.render(
  <Router>
    <App />
  </Router>,
  document.getElementById('root')
);
```

### router组件

```js
//src/App.js
import {Route,Link,NavLink,Redirect,Switch} from 'react-router-dom'

//Link NavLink 路由导航，相当于a标签的功能
<Link to="/home">首页</Link>

//与Link功能一样，默认选中有一个class类 默认的名字叫active
<NavLink to="/home">首页</NavLink>
//activeClassName  可以指定当前路由的类名
<NavLink to="/home" activeClassName='on'>首页</NavLink>
//activeStyle  给当前路由添加样式
<NavLink to="/home" activeStyle={{color:'red'}}>首页</NavLink>

//Switch 多个组件匹配只渲染第一个
<Switch>

  //Route 路径是'/home'时渲染组件
  <Route path="/home" component={组件} />  //如果跳转的路由组件内有二级路由，千万不能加exact
  <Route path="/cart" component={组件} exact /> //exact 精确匹配
  
  //Redirect 重定向，从'/'重定向到'/home'
  <Redirect from="/" to="/home" exact  /> //exact 精确匹配
  
  //404页面
  <Route component={组件} />
  
</Switch>
```

```js
//子路由
//src/components/home/index.js
import {Route,NavLink,Redirect,Switch} from 'react-router-dom'
<NavLink to="/home/one">one</NavLink>
<NavLink to="/home/two">two</NavLink>
<Switch>
    <Route path="/home/one" component={One} />
    <Route path="/home/two" component={Two} />
    <Redirect from="/home" to="/home/one" exact />
</Switch>
```

* Link,NavLink补充
  * to: 可以传string,object,function
    * to='/xxx'
    * to={{pathname:"/xxx",search:"?a=1",hash:"#the-hash",state:{b:2}}}
    * to={location=>({ ...location,pathname:"/xxx"})}

* Route补充
  * path='/xxx'
  * component={组件}
  * render={(props)=>{return <组件 {...props} a=1 />}}
  * children={(props)=>{return <组件 {...props} a=1 />}}
  * exact 精确匹配

```js
//render 作用同component一样,好处是可以加渲染条件和传值
<Route path='/xxx' render={(props)=>{return <组件 {...props} a=1 />}} />

//权限路由示例，如果缓存空间有登录信息就渲染，否则重定向到登录页面
<Route path="/xxx" render={(props)=>{
    return sessionStorage.getItem("user")?<Xxx {...props} />:<Redirect to="/login" />
}} />

//children 没匹配上match为空，匹配了match有值，无论有没有匹配上都会渲染
<Route path='/xxx' children={(props)=>{return <组件 {...props} a=1 />}} />
```

* Redirect补充
  * from='/xxx'
  * to='/yyy'
  * exact 精确匹配

```js
//to属性同Link上的to属性一样可以传值
<Redirect to={{pathname:yyy,state:{key:value}}} />
```

* withRouter高阶组件
  * 作用是让不是路由切换的组件也具有路由切换组件的三个属性(location match history)
  * 参数是组件，返回值也是组件

```js
import React, { Component } from 'react'
import {withRouter} from 'react-router-dom'
class Com extends Component {
  ...
}
export default withRouter(Com)
```

* 路由切换的组件有三个属性(props)
  * history
  * location
  * match

### this.props.history

```js
//监控路由的变化
this.propos.history.listen((location)=>{
  //locatin.pathname 会根据路由的变化而变化
})

//编程式导航
this.props.history.push('/xxx',[state])

//替换当前地址
this.props.history.replace('/xxx',[state])

//历史压栈跳转
this.props.history.go(n) //将历史堆栈中的指针移动n个条目
this.props.history.goBack()//同go(-1)
this.props.history.goForward() //同go(1)
```

### this.props.location

```js
//获取当前路由的路径
this.props.location.pathname

//取路径上的查询字符串
this.props.location.search

//取通过state传过来的参数
this.props.location.state
```

### this.props.match

```js
//接收路由的传参
this.props.match.params
```

### 动态路由传参

```js
//组件传参
<Link to="/xxx/实参1/实参2">路由传参</Link>
<Route path="/xxx/:形参1/:形参2" component={组件} />
//接收参数
this.props.match.params.形参

//编程式导航
//参数形式
this.props.history.push('/xxx/实参1/实参2')
//接收参数
this.props.match.params.形参

//查询字符串形式
this.props.history.push('/xxx/实参?a=1&b=2')
//取查询字符串
this.props.location.search //?a=1&b=2
//字符串处理
this.props.location.search.slice(1) //a=1&b=2
import qs from 'querystring' //node自带
qs.parse('a=1&b=2') //{a:1,b:2}

//通过state传多个参
this.props.history.push('/xxx/实参?a=1&b=2',{c:3,d:4})
//取state参数
this.props.location.state //{c:3,d:4}
```

* PS
* params 默认值  {}  state 默认值是undefined
* 只有显示在路径上的参数刷新不会丢失

## 高阶组件

* 参数是组件，返回值也是组件
* 自写高阶组件示例

```js
import React from 'react'
//方法一
var  Hoc=(Com)=> {  //属性代理
   return class  extends React.Component {
        render(){
         
            return <div><Com {...this.props} /> qf &copy;2020</div>
        }
   }

}
//方法二
var  Hoc=(Com,jf)=> {
    return class  extends Com{  //反向继承  渲染劫持
         render(){
             if(jf<10){
                return <div>积分不足</div>
             }
             else{
                 return <div>{super.render()}vip专享</div>//super.render() 调用父组件Com的render()
                 //也可以这么写return <div><Com {...this.props} />vip专享</div>
             }
            
         }
    }
    
 }
//导出
export default Hoc;

//其它组件使用
import React, { Component } from 'react'
import Hoc from '../hoc';
class One extends Component {
    render() {
        return (
            <div>
                One
            </div>
        )
    }
}
export default Hoc(One,25)  //返回的时候代理版权的信息
```

## redux 状态管理工具

### 起步

* npm i redux -S  安装
* 三个原则
  * store是唯一的
  * state 是只读的
  * 通过纯函数reducer 能够对状态进行修改
* 纯函数：只要是同样的输入，必定得到同样的输出。 
  * 不得改写参数
  * 不能调用系统 I/O 的API
  * 不能调用Date.now()或者Math.random()等不纯的方法，因为每次会得到不一样的结果

### 使用

```js
//src/store/reducer.js
//设置初始数据
const initState={  //状态的初始值
  count:0
}
//传给reducer 
export default (state=initState,action)=>{  //纯函数 state 数据  action动作  也可以写成type,payload形式
  switch(action.type){
    case 'ADD':
      return {...state,count:state.count+=action.payload};
    default:
      return state;
  }
}
```

```js
//src/store/index.js
//引入 createStore
import {createStore} from 'redux';
import reducer from './reducer';
const store=createStore(reducer); //仓库是唯一的
export default store;
```

```js
//src/App.js
//引入store
import store from './store';
//获取数据
store.getState().state中的变量
```

### 修改数据

* store.dispatch(action)
* action 是一定含有type的一个对象
* 动作发给了 reducer 第二个参数 action
* action 一定有type ,还可能接收一些其他参数
* action对象的type值千万不要重复
* 根据type修改数据
  * 做 state 的复本
  * 修改state的复本对象
  * 返回新的state

```js
store.dispatch({type:'ADD',payload:5}) //count加5
```

### subscribe 监听

```js
//subscribe 监听store里的数据变化
constructor(props){
  super(props);
  this.state ={
      count:store.getState().count
  }
  store.subscribe(()=>{  //当store里数据修改的时候会执行这个回调函数
    this.setState({count:store.getState().count}) //重新渲染刷新数据
  });
}
```

### combineReducers分模块

```js
//组件/reducer.js
const initState={
  ...
}
export default (state=initState,action)=>{
  ...
}
```

```js
//src/store/reducer.js
import {combineReducers} from 'redux'
import oneStore from '../components/one/reducer'
import twoStore from '../components/two/reducer'
const reducer=combineReducers({  //返回的reducer 是总的reducer 
  //模块的名字: 引入的reducer
  one:oneStore,
  two:twoStore
})
export default reducer

//分模块以后取数据
store.getState().模块的名字.变量
```

## react-redux

### 起步

* npm i react-redux -S  安装
* 自动监听数据变化

### 使用

```js
//src/index.js
import {BrowserRouter as Router} from 'react-router-dom'
import {Provider} from 'react-redux'
import store from './store'
ReactDOM.render(
  <Provider store={store}>
    <Router>
      <App />
    </Router>
  </Provider>,
  document.getElementById('root')
);
```

* 配合分模块使用
* 组件内

```js
//reducer.js
const initState={
  count:0
}
export default (state=initState,action)=>{
  switch(action.type){
    case 'ADD':
      return {...state,count:state.count+=action.payload};
    default:
      return state;
  }
}
```

```js
//actionCreator.js
export default {
  add(payload){
    return {
      type:'ADD',
      payload
    }
  }
}
```

```js
//index.js
import React from 'react';
import store from '../../store'
import {connect} from 'react-redux'  //connect 高阶组件  连接容器组件和ui组件
import actionCreator from './actionCreator'
class One extends React.Component {
  render() {
    return (
      <div>
        one{this.props.one.count}  //取数据this.props.模块名.变量
        <button onClick={()=>{this.props.add(10)}}>加5</button>  //调用方法this.props.方法名(传参)
      </div>
    )
  }
}
export default connect(state=>state,actionCreator)(One)
```

### 补充

```js
//index.js
class One extends React.Component {
  render() {
    return (
      <div>
        one{this.props.count} {this.props.label} //取数据this.props.变量
        <button onClick={()=>{this.props.add(10)}}>加5</button>  //调用方法this.props.方法名(传参)
      </div>
    )
  }
}

//映射的时候，可以做计算的值的映射
const mapState=(state)=>{
  count:state.one.count
  label: "你好" +(state.one.count>=18?"先生或女士":"小朋友")
}

//方法一  给方法改名
let {add:a} =actionCreator 
let mapDispatch ={a};
//方法二  可以给方法改名, 可以拿到父组件的props  ,可以控制发出动作
var mapDispatch=(dispatch,ownProps)=>{
    console.log(ownProps)
    return {
        a(payload){
            dispatch(actionCreator.add(payload))
        }
    }
}

//var mapDispatch =(dispatch)=>bindActionCreators(actionCreator,dispatch);相当于直接写 actionCreator

export default connect(mapState,mapDispatch)(One)
```

## redux-thunk

### 起步

* npm i redux-thunk -S  安装
* 异步操作

### 使用

```js
//src/store/index.js
import {createStore,applyMiddleware} from 'redux';
import thunk from 'redux-thunk';
import reducer from './reducer';
const store=createStore(reducer,applyMiddleware(thunk));
export default store;
```

```js
//actionCreator.js
export default {
  add(payload){
    return (dispatch)=>{
      //异步动作
      setTimeout(()=>{
        //成功后再调用dispatch发出动作给reducer
        dispatch({
          type:'ADD',
          payload
        })
      },1500)
    }
  }
}
```

## redux-saga

### 起步

* npm i redux-saga -S  安装
* 异步操作

### 使用

```js
//src/store/index.js
import {createStore,applyMiddleware} from 'redux';
import reducer from './reducer'
import createSagaMiddleware from 'redux-saga'
import watchAll from "./saga"; //导入了一个生成器函数
var sagaMiddleware =createSagaMiddleware();  //创建一个saga中间件的实例

var store = createStore(reducer,applyMiddleware(sagaMiddleware));

sagaMiddleware.run(watchAll);    //saga中间件的实例运行生成器函数
export default store;
```

```js
//actionCreator.js
export default {
  add(){
    return {
      type:'WATCHALL',
    }
  }
}
```

```js
//src/store/saga.js
import {takeEvery,call,put} from 'redux-saga/effects'
function *test(){
  var result =  yield call(()=>{ 
                        return fetch("http://localhost:4000/list")
                        .then((res)=>res.json())
                     })
 
  yield put({   //相当于dispatch 
      type:"ADD",
      list:result
  })
  }
export default function *watchAll(){  //监听发出WATCHALL的动作
    yield takeEvery("WATCHALL", test);
}
```

## react-loadable异步加载组件

* npm i react-loadable -S  安装

```js
var 组件名=Loadable({  //异步加载组件
  loader:()=>import("加载的组件路径"),
  loading:()=>加载中组件
})
//例
//import Home from '../components/home'
var Home=Loadable({  //异步加载组件
    loader:()=>import("../components/home"),
    loading:()=><div>loading.....</div>
})
```

## Ant Design

### 在 create-react-app 中使用 [官方文档](https://ant.design/docs/react/use-with-create-react-app-cn)

### 起步

* npm i antd -S  安装
* 全局引入：在index.js里引入样式import 'antd/dist/antd.css';
* 在组件里引入组件就可以使用了，例如组件里使用button
  * import { Button } from 'antd';
  * <Button type="primary">xxx</Button>

图片上传

```js
upload=({file})=>{
    var form = new FormData;
    form.append("file",file)
    upload(form).then((res)=>{
        if(res.status===0){
            this.setState({
                img:"http://localhost:4000"+res.path
            })
        }
    })
}
```

# 拓展

## webpack
webpack 是一个资源打包器
1） 入口
2） 出口
3） loader
4)  插件
全局

npm i webpack -g
npm i webpack-cli -g 
项目
    npm init -y
npm i webpack --save
npm i webpack-cli --save
两种模式
   development 不压缩
   production  压缩
 默认的入口文件是  src/index.js
 默认的出口文件是  dist/main.js

插件
  html-webpack-plugin   自动根据html模板生成一个html文件,
 自动引入就打包后的js

  clean-webpack-plugin  清理dist中打包后的文件

 loader 
   除了js文件，其他文件打包都需要loader
    css style-loader css-loader 
   进行配置（webpack.config.js)
     { 
    test: /\.css$/,
    use: ['style-loader','css-loader']
  }

  图片打包引入两个loader 
   file-loader url-loader

 webpack-dev-server 
   npm i webpack-dev-server --save
    devServer:{
        inline:true 热更新
    }
   “start“：”webpack -w  --progress --open“

## mobx













