---
name: 错误控制器
---

# 错误控制器

当服务器发生500或404错误时，用户可以通过定义错误控制器来决定发生错误时显示什么。若没有定义错误控制器，将会显示默认的错误信息。

### 错误控制路由定义
```golang
ela.Router("@500", controller.Error500)
ela.Router("@404", controller.Error404)
```
