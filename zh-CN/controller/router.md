---
name: 路由
---

# 路由

路由支持两种方式，首先是直接路由模式，然后是路由参数模式。

## 直接路由模式

例如

```golang
Router("/hello/world", f)
```
当访问URI`/hello/world`时，命中该路由

## 路由参数模式

例如

```golang
Router("/hello/:world", f)
```
当访问下列URI

```
/hello/123
/hello/abc
/hello/h2
```
时，命中该路由，并且可以通过`ctx.GetURIParam("world")`获取参数。

## 路由方法

### 初始化安装路由

有些应用希望能够实现自动化安装数据库等，因此程序启动后会根据某一标记判定程序是否已经安装/初始化，若未安装则所有的请求将会自动跳转到指定的安装uri，因此开发者可以在`BeforeRouter`中定义跳转。
但是有些uri确不能执行`BeforeRouter`中的跳转逻辑，因此，这些请求应当使用`InstallRouter`来定义路由，因为，`InstallRouter`定义的路由将不会执行`BeforeRouter`和`AfterRouter`中定义的控制器方法。

```golang
InstallRouter("/install", controller.Install)
```

### BeforeRouter

`BeforeRouter`中定义的控制器将会在住控制器执行之前执行，他对于所有的patter（路由规则）都有效。
```golang
BeforeRouter(controller.Before)
```

### AfterRouter

`AfterRouter`中定义的控制器将会在住控制器执行之后执行，他对于所有的patter（路由规则）都有效。
```golang
AfterRouter(controller.After)
```

### Router

`Router`用于定义主路由，其中可以定义多个控制器，路由将会依次执行，但是若前面的某个控制器执行了`ctx.Write`将响应流已写入，那么之后的控制器讲不会再执行。

- 单个控制器

```golang
Router("/", controller.Index)
```

- 多个控制器

```golang
Router("/publis", controller.CheckUser, controller.Publish)
```

若未定义控制器，将会报404错误。
