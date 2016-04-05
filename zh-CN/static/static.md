---
name: 静态文件路由配置
---

# 静态文件路由配置

## 默认模式
配置文件
```
[static]
path = "staticfiles"
```
当配置文件不存在此项时，默认`path = "static"`。
此时，路由规则是，首先处理用户定义的Router中的控制器相关的路由，若找不到，则在path路径下查找静态文件路由，例如，request uri:/ , Router中若没有定义，则查找`staticfiles`目录下的`index.html`文件, request uri:/test/file.html , 则查找`staticfiles`目录下的`test/file.html`文件。

## alias模式
配置文件
```
[static]
path = "staticfiles"
alias = "static"
```
此时，路由规则是，首先查找request uri中是否包含alias开头，此例中`/static`，若请求request uri中包含`/static`，则为静态文件路由规则。例如，request uri:/static/index.html，为`/static`开头，静态路由规则将会查找`staticfiles`目录下的`index.html`文件；请求request uri:/static/test/file.html，则查找`staticfiles`目录下的`test/file.html`。
