# renalog

renalog是一个C++的轻量化日志创建和读取库 目前在MinGW上完成测试

## 安装与链接

以MinGW环境举例：

renalog有四个编译选项 分别是：

| 编译选项 | 作用 | 默认值 |
| --- | --- | --- |
| BUILD_RELEASE | 编译发布版库 | `ON` (不勾选则编译调试版库) |
| BUILD_SHARED | 编译动态库 | `ON` |
| BUILD_STATIC | 编译静态库 | `ON` |
| BUILD_LOGREADER_FUNCTION | 编译renalog的日志读取库 | `ON` |

完成CMake配置后 在CMake输出的build文件夹下执行

```
mingw32-make
mingw32-make install
```

随后前往安装文件夹 便可找到编译完成的renalog库 使用时直接链接库文件即可

## 引入

若编译了renalog的日志读取库 则在引入库时应如此包含头文件：

```CPP
#include"renalog/renalog.h"
```

若没有编译renalog的日志读取库 则应如此包含头文件：

```CPP
#include"renalog/renalog_core.h"
```

