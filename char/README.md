# 说明

## 脚本根目录

脚本工程的Resources\Script目录

## 脚本接口改动

* 去掉repeat until语法
* 添加continue语法
* 去掉io和package库
* 去掉module
* 去掉setfenv和getfenv
* 去掉_G，新增globals(name, ...)可以获取全局变量，**没有设置全局变量的方式**
* os库去掉大多数接口，只保留clock/date/difftime/time/setlocale
* 新增bit和lpeg库

## 脚本封装

每个脚本文件都具有自己单独的环境表，只有全局函数可以直接引用

### 引用系统库

要使用math/string等系统库，需要在脚本中先进行导出，如
```
local math = require "math"
```
之后就可以使用math库了

### 引用其他文件

要使用脚本目录下的其他文件，需要在脚本中先进行导出，如
```
local test = require "test"
```
之后test就指向test.lua的全局环境表，可以直接读取变量，调用函数等