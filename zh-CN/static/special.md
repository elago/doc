---
name: 特殊静态文件
---

# 特殊静态文件

在web应用中有些约定俗成的文件，例如`favicon.ico`, `robots.txt`等。它们约定的uri是`/favicon.ico`, `/robots.txt`，你可以直接将`favicon.ico`放置于你定义的static-path目录中即可，它不遵循alias静态路由规则。
