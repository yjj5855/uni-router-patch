# uni-router-patch
mpvue-router-patch 的uni版

操作请看
https://github.com/F-loat/mpvue-router-patch#readme

# 以下是 mpvue-router-patch 的介绍 只用把mpvue看成uni就行
> 在 mpvue 中使用 vue-router 兼容的路由写法

## 安装

使用插件市场安装hbuilder插件 也可下载index.js直接使用

## 使用

``` js
// main.js
import Vue from 'vue'
import MpvueRouterPatch from './js_sdk/yjj5855-uni-router-patch/index.js'

Vue.use(MpvueRouterPatch)
```

## API

> 支持以下列出的方法及属性

### Router 实例

#### 属性

* $router.app

当前页面的 Vue 实例

* $router.mode

路由使用的模式，固定值 `history`

* $router.currentRoute

当前路由对应的路由信息对象，等价于 $route

#### 方法

* $router.push(location, onComplete?, onAbort?, onSuccess?)

跳转到应用内的某个页面，`mpvue.navigateTo`、`mpvue.switchTab` 及 `mpvue.reLaunch` 均通过该方法实现，`location` 参数支持字符串及对象两种形式，跳转至 `tabBar` 页面或重启至某页面时必须以对象形式传入

``` js
// 字符串
router.push('/pages/news/detail')

// 对象
router.push({ path: '/pages/news/detail' })

// 带查询参数，变成 /pages/news/detail?id=1
router.push({ path: '/pages/news/detail', query: { id: 1 } })

// 切换至 tabBar 页面
router.push({ path: '/pages/news/list', isTab: true })

// 重启至某页面，无需指定是否为 tabBar 页面，但 tabBar 页面无法携带参数
router.push({ path: '/pages/news/list', reLaunch: true })
```

* $router.replace(location, onComplete?, onAbort?, onSuccess?)

关闭当前页面，跳转到应用内的某个页面，相当于 `mpvue.redirectTo`，`location` 参数格式与 `$router.push` 相似，不支持 `isTab` 及 `reLaunch` 属性

* $router.go(n)

关闭当前页面，返回上一页面或多级页面，`n` 为回退层数，默认值为 `1`

* $router.back()

关闭当前页面，返回上一页面

### 路由信息对象

#### 属性

* $route.path

字符串，对应当前路由的路径，总是解析为绝对路径，如 `/pages/news/list`

* $route.params

空对象，小程序不支持该属性

* $route.query

一个 key/value 对象，表示 URL 查询参数。例如，对于路径 `/pages/news/detail?id=1`，则有 `$route.query.id == 1`，如果没有查询参数，则是个空对象。

* $route.hash

空字符串，小程序不支持该属性

* $route.fullPath

完成解析后的 URL，包含查询参数和 hash 的完整路径

* $route.name

当前路由的名称，由 `path` 转化而来
