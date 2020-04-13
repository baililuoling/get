# Ant

antd 是基于 Ant Design 设计体系的 React UI 组件库，主要用于研发企业级中后台产品

#### 安装

使用 npm 或 yarn 安装

```shell
npm install antd --save

yarn add antd
```

# 浏览器引入

#### 引入样式

```js
// 可以在 index.js 入口文件引入

import 'antd/dist/antd.css'; // or 'antd/dist/antd.less'
```

#### 实例说明

```js
import { DatePicker } from 'antd';
ReactDOM.render(<DatePicker />, mountNode);
```

#### 实例说明 2

- 输入 antd.css 样式: `import 'antd/dist/antd.css';`
- 输入 zhCN 中文对象：`import zhCN from 'antd/es/locale/zh_CN';`
   - 在 ConfigProvider 组件添加 locale 属性： `locale={zhCN}`
   - 被 ConfigProvider 组件包裹的子孙组件就可以修改为中文
- moment 日期类库：
   - 输入 moment 日期类库：`import moment from 'moment';`
   - 修改 moment 语言：`import 'moment/locale/zh-cn';`
   - 使用中文文案：`moment.locale('zh-cn');`
- 输入 antd ：`import {ConfigProvider, DatePicker, message} from 'antd';` 解构使用

##### 渲染

![image](https://note.youdao.com/yws/res/37243/4242C461FC2540B2A1C188B84AE4705F)

```js
import React from 'react';
import './App.css';
import zhCN from 'antd/es/locale/zh_CN'; // 由于 antd 组件的默认文案是英文，所以需要修改为中文
// import moment from 'moment'; // moment 日期处理类库
import 'moment/locale/zh-cn'; // 由于 moment 默认文案是英文，所以需要修改为中文
import {ConfigProvider, DatePicker, Button} from 'antd';

// moment.locale('zh-cn'); // 使用中文

function App() {
    return (
        <div className="App">
            {/*通过 locale 属性使用中文对象*/}
            <ConfigProvider locale={zhCN}>
                {/*日期选择器*/}
                <DatePicker/>
            </ConfigProvider>
            {/*按钮，type 指颜色类型*/}
            <Button type="primary" style={{marginLeft: 8}}>确定</Button>
        </div>
    );
}

export default App;
```

#### 实例说明 3

直接用下面的代码替换 index.js 的内容，用 React 的方式直接使用 antd 组件

- 输入 antd.css 样式: `import 'antd/dist/antd.css';`
- 输入 zhCN 中文对象：`import zhCN from 'antd/es/locale/zh_CN';`
   - 在 ConfigProvider 组件添加 locale 属性： `locale={zhCN}`
   - 被 ConfigProvider 组件包裹的子孙组件就可以修改为中文
- moment 日期类库：
   - 输入 moment 日期类库：`import moment from 'moment';`
   - 修改 moment 语言：`import 'moment/locale/zh-cn';`
   - 使用中文文案：`moment.locale('zh-cn');`
- 输入 antd ：`import {ConfigProvider, DatePicker, message} from 'antd';` 解构使用

##### 渲染

![image](https://note.youdao.com/yws/res/37243/4242C461FC2540B2A1C188B84AE4705F)

```js
// src/index.js

import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import 'antd/dist/antd.css'; // 输入 antd 样式 // 或者 import  'antd/dist/antd.less'
import zhCN from 'antd/es/locale/zh_CN'; // 由于 antd 组件的默认文案是英文，所以需要修改为中文
import moment from 'moment'; // moment 日期处理类库
import 'moment/locale/zh-cn'; // 由于 moment 默认文案是英文，所以需要修改为中文
import {ConfigProvider, DatePicker, message} from 'antd'; // 输入组件

moment.locale('zh-cn'); // 使用中文

class App extends React.Component {
    state = {
        date: null,
    };

    handleChange = date => {
        message.info(`您选择的日期是: ${date ? date.format('YYYY-MM-DD') : '未选择'}`);
        this.setState({date});
    };

    render() {
        const {date} = this.state;
        return (
            // ConfigProvider 组件使用中文 locale 指用什么语言
            <ConfigProvider locale={zhCN}>
                <div style={{width: 400, margin: '100px auto'}}>
                    <DatePicker onChange={this.handleChange}/>
                    <div style={{marginTop: 20}}>
                        当前日期：{date ? date.format('YYYY-MM-DD') : '未选择'}
                    </div>
                </div>
            </ConfigProvider>
        );
    }
}

ReactDOM.render(<App/>, document.getElementById('root'));
```

# 手动按需加载

```js
import DatePicker from 'antd/es/date-picker'; // 加载 JS
import 'antd/es/date-picker/style/css'; // 加载 CSS
// import 'antd/es/date-picker/style';         // 加载 LESS
```

实例说明 2

- 根据需求，需要哪个组件
- 就加载哪个组件

渲染

![image](https://note.youdao.com/yws/res/37243/4242C461FC2540B2A1C188B84AE4705F)

```js
import React from 'react';
import './App.css';
import zhCN from 'antd/es/locale/zh_CN'; // 由于 antd 组件的默认文案是英文，所以需要修改为中文
import 'moment/locale/zh-cn'; // // 由于 moment 默认文案是英文，所以需要修改为中文
import {ConfigProvider} from 'antd';
// 加载 DatePicker 组件
import DatePicker from 'antd/es/date-picker' // 加载 JS
// 加载 Button 组件
import Button from 'antd/es/button' // 加载 JS
// DatePicker 组件样式
import 'antd/es/date-picker/style/css' // 加载 css
// 加载 Button 组件样式
import 'antd/es/button/style/css' // 加载 css


function App() {
    return (
        <div className="App">
            <ConfigProvider locale={zhCN}>
                {/*日期选择器*/}
                <DatePicker/>
            </ConfigProvider>
            {/*按钮，type 指颜色类型*/}
            <Button type="primary" style={{marginLeft: 8}}>确定</Button>
        </div>
    );
}

export default App;
```

# 配置 webpack 进行按需加载

## react-app-rewired 模块

- 此工具可以在不 'eject' 也不创建额外 react-scripts 的情况下修改 create-react-app 内置的 webpack 配置
- 然后将拥有 create-react-app 的一切特性，且可以根据需要去配置 webpack 的 plugins, loaders 等
- 不用弹射就可以配置 webpack

#### 下载安装

```shell
npm install react-app-rewired --save-dev

# 简写
npm i react-app-rewired -D
```

#### 配置

##### 1. 在根目录中创建一个 config-overrides.js 文件，用于修改默认配置

目录

```shell
+-- your-project
|   +-- config-overrides.js
|   +-- node_modules
|   +-- package.json
|   +-- public
|   +-- README.md
|   +-- src
```

config-overrides.js 文件

```js
/* config-overrides.js */
module.exports = function override(config, env) {
  //do stuff with the webpack config...
  return config;
}
```

##### 2. 替换 package.json 中 scripts 执行部分

> 注意
>
> 不用替换 eject 部分。工具中没有针对 eject 的配置替换，执行了 eject 命令会让工具失去作用

```js
  /* package.json */

  "scripts": {
-   "start": "react-scripts start",
+   "start": "react-app-rewired start",
-   "build": "react-scripts build",
+   "build": "react-app-rewired build",
-   "test": "react-scripts test",
+   "test": "react-app-rewired test",
    "eject": "react-scripts eject"
}
```

修改完后

```json
  /* package.json */

  "scripts": {
    "start": "react-app-rewired start",
    "build": "react-app-rewired build",
    "test": "react-app-rewired test",
    "eject": "react-scripts eject"
  },
```
##### 3. 启动 Dev Server

```shell
npm start
```

##### 构建你的应用程序

```shell
npm run build
```

## customize-cra 模块

- 该项目提供了一组实用程序，以利用react-app-rewired的核心功能
- 来自定义create-react-app版本2和3的配置。
- 自定义脚手架环境

#### 安装

> 注意
> 
> 该项目依赖于react-app-rewired。 您需要安装它才能使 custom-cra 正常工作。

```shell
npm i customize-cra react-app-rewired --save-dev
```

#### [配置请参考官网](https://www.npmjs.com/package/customize-cra)

## babel-plugin-import 模块

babel-plugin-import 是一个用于按需加载组件代码和样式的 babel 插件，可以通过修改 config-overrides.js 文件，进行按需加载

> 注意：
>
> 插件会帮你转换成 antd/es/xxx 的写法。另外此插件配合 style 属性可以做到模块样式的按需自动加载
> 
> babel-plugin-import 的 style 属性除了引入对应组件的样式，也会引入一些必要的全局样式。如果你不需要它们，建议不要使用此属性。你可以 import 'antd/dist/antd.css' 手动引入，并覆盖全局样式。

#### 安装

```shell
npm i babel-plugin-import --save-dev
```

#### 配置

修改 config-overrides.js 文件

```js
/* config-overrides.js */

+ const { override, fixBabelImports } = require('customize-cra');

- module.exports = function override(config, env) {
-   // do stuff with the webpack config...
-   return config;
- };
+ module.exports = override(
+   fixBabelImports('import', {
+     libraryName: 'antd',
+     libraryDirectory: 'es',
+     style: 'css',
+   }),
+ );
```

修改完后

```js
/* config-overrides.js */

const {override, fixBabelImports} = require('customize-cra');

module.exports = override(
    fixBabelImports('import', {
        libraryName: 'antd',
        libraryDirectory: 'es',
        style: 'css', // 设置 css 或者 less 。 true 为 less ； 'css' 为 css
    }),
);
```

#### 配置  @ 指向 src 目录

修改 config-overrides.js 文件

- 需要 customize-cra 模块解构 addWebpackAlias 方法
- 需要 path 模块解构 resolve 方法
- 输出 执行 override() 方法，以回调函数的方式，将解构的 addWebpackAlias 方法传入
- addWebpackAlias 方法出入 1 个对象，对象 key 为 '@'，value 为 resolve('src')
- 即可配置成功，配置完重启

```js
/* config-overrides.js */

const {override, fixBabelImports, addWebpackAlias} = require('customize-cra');
const {resolve} = require('path'); // 需要 path 模块，解构 resolve 方法

module.exports = override(
    fixBabelImports('import', {
        libraryName: 'antd',
        libraryDirectory: 'es',
        style: 'css', // 设置 css 或者 less 。 true 为 less ； 'css' 为 css
    }),
    addWebpackAlias({
        '@': resolve('src'),
    }),
);
```

使用

```js
import React from 'react';
import './App.css';

import One from '@/components/one'

function App() {
    return (
        <div className="App">
            <One/>
    );
}

export default App;
```

#### 按需使用组件

antd 组件的 js 和 css 代码都会按需加载

```js
  // src/App.js
  import React, { Component } from 'react';
  // import Button from 'antd/es/button';
  import { Button } from 'antd';
  import './App.css';

  class App extends Component {
    render() {
      return (
        <div className="App">
          <Button type="primary">Button</Button>
        </div>
      );
    }
  }

  export default App;
```

# 自定义主题

- 按照 配置主题 的要求，自定义主题需要用到 less 变量覆盖功能
- 可以引入 customize-cra 中提供的 less 相关的函数 addLessLoader 来帮助加载 less 样式
- 同时修改 config-overrides.js 文件如下

## less 模块

Less 是一门 CSS 预处理语言，它扩展了 CSS 语言，增加了变量、Mixin、函数等特性，使 CSS 更易维护和扩展

#### 安装

```shell
npm install less --save-dev
```

## less-loader 模块

用于 webpack 的 less-loader 用于处理编译 .less 文件，将其转为 css文件代码

#### 安装

> 注意：
>
> 使用 less-loader 的话，必须安装 less，单独一个 less-loader 是没办法正常使用的。

```shell
npm install --save-dev less-loader less
```

#### 配置

配置 config-overrides.js 文件

```js
/* config-overrides.js */

- const { override, fixBabelImports } = require('customize-cra');
+ const { override, fixBabelImports, addLessLoader } = require('customize-cra');

module.exports = override(
  fixBabelImports('import', {
    libraryName: 'antd',
    libraryDirectory: 'es',
-   style: 'css',
+   style: true,
  }),
+ addLessLoader({
+   javascriptEnabled: true,
+   modifyVars: { '@primary-color': '#1DA57A' },
+ }),
);
```

修改完后

```js
/* config-overrides.js */

const {override, fixBabelImports, addLessLoader} = require('customize-cra');

module.exports = override(
    fixBabelImports('import', {
        libraryName: 'antd',
        libraryDirectory: 'es',
        style: true, // 值为 true 指 less ；指为 'css' 指 css
    }),
    addLessLoader({
        javascriptEnabled: true,
        // 通过修改 modifyVars 对象内属性的值修改主题颜色
        modifyVars: {'@primary-color': '#1DA57A'},
    }),
);
```

#### [更多主题配置](https://ant.design/docs/react/customize-theme-cn)

# 配置装饰器

JS 使用的装饰器(Decorator)很像 Java 的 @annotation，其目的是可以在运行时改变类或者改变类的属性。

要使用 Decorator 得安装 Babel 的 @babel/plugin-proposal-decorators 插件用于转译装饰器代码

## @babel/plugin-proposal-decorators

将类和对象装饰器编译为ES5

#### 安装

```shell
npm install --save-dev @babel/plugin-proposal-decorators
```

#### 配置

配置 config-overrides.js 文件

```js
/* config-overrides.js */

const {addDecoratorsLegacy} = require('customize-cra');
module.exports = override(
    // 添加装饰器
    addDecoratorsLegacy(),
);
```

## 使用装饰器

### 装饰器后面跟类组件不传参

装饰器的使用非常简单，其本质上就是一个函数

> 注意：
> 
> @装饰器，后面必须是类组件

#### One 组件

- 输入高阶组件：`import Hoc from '../hoc'`
- 语法：@Hoc
   - @：装饰器标识符
      - 装饰器标识符后面为装饰器
   - Hoc：

```js
// src/components/one/index.jsx

import React, {Component} from 'react';
import Hoc from '../hoc'

@Hoc // 使用装饰器

class One extends Component {
    constructor(props) {
        super(props);
        this.state = {}
    }

    render() {
        return (
            <div>
                One
            </div>
        );
    }
}

// export default Hoc(One) // 之前使用高阶组件
export default One
```

#### Hoc 组件

```js
// src/components/hoc/index.jsx

import React, {Component, Fragment} from 'react';

const Hoc = (Com) => {
    return class extends Component {
        render() {
            return (
                <div>
                    <Com {...this.props}/>
                    2020 &copy; GML
                </div>
            );
        }
    }
};

export default Hoc
```

### 装饰器后面跟类组件传参

- 使用函数柯里化的方式传承

#### One 组件

```js
// src/components/one/index.jsx

import React, {Component} from 'react';
import Hoc from '../hoc'

@Hoc(18) // 使用装饰器

class One extends Component {
    constructor(props) {
        super(props);
        this.state = {}
    }

    render() {
        return (
            <div>
                One
            </div>
        );
    }
}

// export default Hoc(One) // 之前使用高阶组件
export default One
```

#### Hoc 组件

- 使用函数柯里化的方式传承

```js
// src/components/hoc/index.jsx

import React, {Component, Fragment} from 'react';

const Hoc = (jf) => (Com) => {
    return class extends Component {
        render() {
            if (jf > 10) {
                return (
                    <div>
                        积分：{jf}
                        <Com {...this.props}/>
                        2020 &copy; GML
                    </div>
                );
            } else {
                return (<div>积分不足 </div>);
            }
        }
    }
};

export default Hoc
```

# 配置代理

- 正向代理，跨越请求数据

## http-proxy-middleware

Node.js代理变得简单。 轻松配置代理中间件，以进行连接，表达，浏览器同步等等。

#### 安装

```shell
npm i http-proxy-middleware -D
```

#### 配置

src 目录下新建 setupProxy.js 文件

##### 方法一

- use 使用 `http-proxy-middleware` 模块，接收 2 个参数：
   - 第 1 个参数：请求名
   - 第 2 个参数：`http-proxy-middleware` 模块，是 1 个函数，传入 1 个对象
- target：指代理地址
- changeOrigin：开启代理
- pathRewrite：重写地址

```js
// src/setupProxy.js

const proxy = require('http-proxy-middleware'); // 需要 http-proxy-middleware 模块

// 相当于增加了 1 个服务
module.exports = (app) => {
    // 代理设置
    app.use('/api', proxy({
        target: 'http://127.0.0.1',
        changeOrigin: true,
        pathRewrite: {
            '^/api': ''
        }
    }));

    // 开启服务测试用
    app.get('/test', (req, res) => {
        res.json({
            ok: 1,
        })
    })
};
```

##### 方法二

```js
// src/setupProxy.js

const {createProxyMiddleware} = require('http-proxy-middleware');

module.exports = function (app) {
    app.use('/api',
        createProxyMiddleware({
                target: 'https://cnodejs.org/api/v1',
                changeOrigin: true,
                pathRewrite: {
                    "^/api": "/"
                }
            }
        ));
};
```

#### 使用

One 组件

```js
// src/components/one/index.jsx

import React, {Component} from 'react';

class One extends Component {

    componentDidMount() {
        // 使用代理
        fetch("/api/topics").then((res) => res.json()).then((res) => {
            console.log(res)
        })
    }

    render() {
        return (
            <div>
                One
            </div>
        );
    }
}

export default One
```

# 汇总

#### 按需加载需要安装的依赖包

```shell
npm i -D customize-cra react-app-rewired babel-plugin-import
```

1. package.json 配置

```json
  "scripts": {
    "start": "react-app-rewired start",
    "build": "react-app-rewired build",
    "test": "react-app-rewired test",
    "eject": "react-scripts eject"
  },
```

2. 项目文件下新建 config-overrides.js 配置

```js
/* config-overrides.js */

const {override, fixBabelImports} = require('customize-cra');

module.exports = override(
    fixBabelImports('import', {
        libraryName: 'antd',
        libraryDirectory: 'es',
        style: 'css',
    }),
);
```

#### 配置  @ 指向 src 目录

修改 config-overrides.js 文件

```js
/* config-overrides.js */

const {override, fixBabelImports, addWebpackAlias} = require('customize-cra');
const {resolve} = require('path'); // 需要 path 模块，解构 resolve 方法

module.exports = override(
    fixBabelImports('import', {
        libraryName: 'antd',
        libraryDirectory: 'es',
        style: 'css', // 设置 css 或者 less 。 true 为 less ； 'css' 为 css
    }),
    // 配置 @ 指向 src 目录
    addWebpackAlias({
        '@': resolve('src'), // 需要 resolve 方法
    }),
);
```

#### 自定义配置主题需要安装的依赖包

```shell
npm i -D less less-loader
```

config-overrides.js 配置

```js
/* config-overrides.js */

const {override, fixBabelImports, addLessLoader} = require('customize-cra');

module.exports = override(
    fixBabelImports('import', {
        libraryName: 'antd',
        libraryDirectory: 'es',
        style: true, // 值为 true 指 less ；指为 'css' 指 css
    }),
    addLessLoader({
        javascriptEnabled: true,
        // 通过修改 modifyVars 对象内属性的值修改主题颜色
        modifyVars: {'@primary-color': '#1DA57A'},
    }),
);
```

#### 配置装饰器依赖包

```shell
npm install --save-dev @babel/plugin-proposal-decorators
```

配置 config-overrides.js 文件

```js
/* config-overrides.js */

const {override, fixBabelImports, addLessLoader, addWebpackAlias, addDecoratorsLegacy} = require('customize-cra');
const {resolve} = require('path');
module.exports = override(
    fixBabelImports('import', {
        libraryName: 'antd',
        libraryDirectory: 'es',
        style: true, // 值为 true 指 less ；指为 'css' 指 css
    }),
    addLessLoader({
        javascriptEnabled: true,
        modifyVars: {'@primary-color': 'red'},
    }),
    addWebpackAlias({
        '@': resolve('src'),
    }),
    addDecoratorsLegacy(),
);
```

使用方法：
@高阶组件(参数)
class 组件 extends Component { }
等价于  高阶组件(参数)(组件)

#### 配置代理依赖包

```shell
npm i http-proxy-middleware -D
```

新建 src/setupProxy.js 文件进行配置

```js
// src/setupProxy.js

const {createProxyMiddleware} = require('http-proxy-middleware');

module.exports = function (app) {
    app.use('/api',
        createProxyMiddleware({
                target: 'https://cnodejs.org/api/v1',
                changeOrigin: true,
                pathRewrite: {
                    "^/api": "/"
                }
            }
        ));
};
```

#### 一共需要下载的依赖

##### 创建项目

```shell
npx create-react-app my-app
```

##### 生产环境（4）

- react-router-dom：路由router
- redux：全局状态管理
- react-redux：垂直状态管理
- antd：ui

```shell
npm i react-router-dom redux react-redux antd
```

##### 开发环境（7）

- react-app-rewired：不用弹射就可以配置 webpack
- customize-cra：自定义脚手架环境
- babel-plugin-import：按需加载组件，js 和 css
- less：less 语法
- less-loader：less 转 css
- @babel/plugin-proposal-decorators：装饰符转 ES5
- http-proxy-middleware：代理，解决跨域

```shell
npm i -D customize-cra react-app-rewired babel-plugin-import less less-loader @babel/plugin-proposal-decorators http-proxy-middleware
```

##### 项目目录下 package.json ， scripts 对象 value 修改为

```shell
"scripts": {
    "start": "react-app-rewired start",
    "build": "react-app-rewired build",
    "test": "react-app-rewired test",
    "eject": "react-scripts eject"
  },
```

##### 项目目录下新建 config-overrides.js

```js
const {override, fixBabelImports, addLessLoader, addWebpackAlias, addDecoratorsLegacy} = require('customize-cra');
const {resolve} = require('path');
module.exports = override(
    // antd 配置
    fixBabelImports('import', {
        libraryName: 'antd',
        libraryDirectory: 'es',
        style: true, // 值为 true 指 less ；指为 'css' 指 css
    }),
    // 自定义主题
    addLessLoader({
        javascriptEnabled: true,
        modifyVars: {'@primary-color': 'red'},
    }),
    // @ 指向 src
    addWebpackAlias({
        '@': resolve('src'),
    }),
    // 添加 @ 装饰符
    addDecoratorsLegacy(),
);
```

##### src 目录下新建 setupProxy.js

```js
const {createProxyMiddleware} = require('http-proxy-middleware');

module.exports = function (app) {
    app.use('/api',
        createProxyMiddleware({
                target: 'https://cnodejs.org/api/v1',
                changeOrigin: true,
                pathRewrite: {
                    "^/api": "/"
                }
            }
        ));
};
```