### 作用 ###

    Router是整个路由系统的顶层组件，用来保持URL和路由的同步。

### 原理 ###
`react-router`引入了第三方模块[`history`](https://github.com/ReactTraining/history)和[`path-to-regexp`](https://github.com/pillarjs/path-to-regexp),这两个模块也是`react-router`中最重要的两个模块。
`history`模块主要用来操作`javascript`中`history`以实现路由的变更,`path-to-regexp`主要用来匹配`url`地址。

