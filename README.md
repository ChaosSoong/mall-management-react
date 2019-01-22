## 项目技术栈

react@16.5.2 + redux@3.7.2 + react-router@3.2.0 + webpack@3.10.0 + axios@0.18.0 + less@2.7.1 + antd@3.10.1

## 项目运行

```
git clone
cd react

npm install

npm start

```

欢迎下载
想要体验聊天室功能 先开启 socket 服务 运行命令

```
npm run chat

```

最后的构建命令

```
npm run build (打包，部署)

```

对了，服务端返回的格式我们是这样子一个数据结构

```
{
  data: {
    totalCount: 100,
    currentPage: 1,
    pageSize: 10,
    'list': [
    ],
  },
  msg: '',
  status: 1,
}

```

所有异步请求返回都会经过 configs 里面的 ajax.js 做处理，如果请求没有任何问题，那 status 返回值是 1；
如果请求错误，比如说参数错误或者其他报错之类的，那 status 返回值就是 0；
如果 status 值是-1，表示登录超时，那么就会跳出登录。
这些参数都可以根据实际情况进行调整，报错或者成功的提示信息放在 msg 里面返回。
当前项目集成了完整的用户管理、角色管理、模块管理等基本的权限管理功能，小伙伴们一定要同时启动 npm run mock 才可以看到噢

这个 react 的项目我有在跟 nodejs 的 express 框架配合做接口的开发，可以不靠后端输出数据库真实的数据，仓库地址在

基本功能差不多，目前实现了注册登录以及获取用户信息等 3 个接口的真实 api

## 说明

> 开发环境 macos Chrome 63.0.3239.132（正式版本） （32 位） nodejs 8.7.0

> 如果 npm install 太慢导致有些 npm 依赖包下载失败 你可以看控制台的报错信息，再手动 npm install 具体的开发包，推荐使用淘宝的注册源，直接运行，

```
npm install -g cnpm --registry=https://registry.npm.taobao.org

```

### 取消 http 请求示例：

```
import axios from 'axios'
const axiosHandle = axios.CancelToken.source()

login(){
  this.props.dispatch(fetchLogin(values, (res) => {},(error)=>{},axiosHandle)
  取消请求的操作
  setTimeout(() => {
    axiosHandle.cancel('手动取消。')
  }, 3000)
}

```

## 功能一览

- [√] 项目按路由模块加载
- [√] 登录，以及登录权限控制
- [√] 退出
- [√] 欢迎主页
- [√] 左侧菜单，正常 mini 切换
- [√] redux 完整示范
- [√] mockjs 模拟后端返回接口
- [√] 页面高度 flex 自适应
- [√] axios 数据跨域的设置
- [√] 实时的 webpack 包大小预览,方便优化
- [√] draftjs 编辑器
- [√] 聊天室
