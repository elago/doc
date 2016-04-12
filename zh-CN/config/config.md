---
name: 配置模块
---

# 配置模块

Config模块用来读写ini配置文件。

- 初始化配置

```golang
import(
	"github.com/elago/ela"
)

conf := ela.NewConfig("config/app.ini")

```

- 读取配置

`Get`方法, 返回interface{}类型

```golang
value,err:=conf.Get("section","key")
```

`GetBool`方法, 返回bool类型

```golang
valueBool,err:=conf.GetBool("section","key")
```

`GetInt`方法, 返回int64类型

```golang
valueInt,err:=conf.GetInt("section","key")
```

`GetFloat`方法, 返回float64类型

```golang
valueFloat,err:=conf.GetFloat("section","key")
```

`GetString`方法, 返回string类型

```golang
valueString,err:=conf.GetString("section","key")
```
