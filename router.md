### 作用 ###

    Router是整个路由系统的顶层组件，用来保持URL和路由的同步。

### 原理 ###
`react-router`引入了第三方模块[`history`](https://github.com/ReactTraining/history)和[`path-to-regexp`](https://github.com/pillarjs/path-to-regexp),这两个模块也是`react-router`中最重要的两个模块。
`history`模块主要用来操作`javascript`中`history`以实现路由的变更,`path-to-regexp`主要用来匹配`url`地址。
`Router`作为路由最顶层的组件，利用`React`中的`context`的特性，向子组件提供了一个`router`对象
```js
router = {
    history: {...},
    route: {
      location: {...},
      match: {
          path: '/',
          url: '/',
          params: {},
          isExact: true  //or false
      }
    }
}
```
`router`中的`history`对象来自于`history`模块，提供了一些操作路由的方法，和当前路由的信息，`location`对象里面存储着当前`url`的信息，`match`来自于`Router`组件的`state`对象。
`Router`组件会监听路由的改变，然后调用`setState`方法改变match,将会触发子组件的`componentWillReceiveProps`方法，子组件会通过`componentWillReceiveProps`方法接受到新的`context`。
```js
    //当路由改变时，子组件会得到新的context中的router对象,
componentWillReceiveProps(nextProps, nextContext) {
    
}
```
总之，`Router`组件作为顶层组件，监听者路由的变化，然后提供给子组件。
###Props###
#####history: `object`
`Router`组件接受一个`history`的`props`,向`Router`组件提供`history`对象,最终提供给子组件。

```js
import createBrowserHistory from 'history/createBrowserHistory'

const customHistory = createBrowserHistory()
<Router history={customHistory}><App/></Router>
```
