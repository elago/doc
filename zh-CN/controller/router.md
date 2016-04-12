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

