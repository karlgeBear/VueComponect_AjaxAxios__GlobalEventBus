# APP_baseAjax
### 1、在vue的mounted方法中发ajax，有以下两种方法
* vue-resource
  * 1、下载yarn add vue-resource
  * 2、 在入口文件(index)引入并且
  * 2.1、声明使用插件：Vue.use(VueResource)
  * 2.2、因此组件对象都有了一个属性$http对象（此对象有get、post等方法）
  * 3、在组件发Ajax：this.this.$http.get(url,..)
* axios
  * 下载yarn add axios
  * 组件引入,即可发Ajax
# Ajax-demo
* 实现兄弟组件之间的通信：全局事件总线
  * 在入口文件index.js设置Vue.prototyoe.$globalEventBus或者this.__proto__.$globalEventBus = this(this就是new Vue)
  * 自定义事件：在search(获取)搜索数据,分发事件，在Main(数据响应渲染界面)绑定监听事件从而触发事件
  * 使用axios在 绑定监听事件的 回调函数 发Ajax
* 实现在 域名相同，端口号不同 的时候进行跨域请求，
  * 需要在webpack上的devtool上配置即可
  ```
  proxy: {  // http://localhost:3000/api
  //'/api': 'http://localhost:4000'    //==> httlocalhost:4000/ api/xxx
  '/api': {  //匹配处理以/api开头的请求
    target: 'http://localhost:4000',  //转发的目标地址
    pathRewrite: { '^/api': '' }  //在转发请求前去除路径中/api  //  htpp://localhost:4000/xxx
    //changeOrigin: true  //支持跨域，如果协议/主机也不相同，必须加上
  }
  ```
  * 一些接口的理解
    * 在html发Ajax请求时，显示的xhr是当前端口号的url，可实际上是请求的另一个端口号的url，
* 配置async/await的编译环境(在发送ajax时)
  * 下载包：
        yarn add @babel/runtime-corejs2
  * 配置:
  ```
  presets: [
    ['@babel/preset-env', {
      useBuiltIns: 'usage',
      'corejs': 2 // 处理一些新语法的实现
    }]
  ]
  ```