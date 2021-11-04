- github地址： [spdlog](https://github.com/gabime/spdlog)
- 快速，只加头文件编译的C++日志库
-
## 安装
### 头文件版本
- 复制Include文件夹到编译环境，使用C++11编译器
### 静态库版本（作者推荐，编译更快）
-
  ```
  $ git clone https://github.com/gabime/spdlog.git
  $ cd spdlog && mkdir build && cd build
  $ cmake .. && make -j
   ```
-
## 平台
-
  * Linux, FreeBSD, OpenBSD, Solaris, AIX
  * Windows (msvc 2013+, cygwin)
  * macOS (clang 3.5+)
  * Android
-
## 特点
- 快速
- 仅需头文件或者使用已编译的库
- 丰富的格式化，使用 [fmt](https://github.com/fmtlib/fmt) 库
- 异步模式（可选）
- [定制格式化](https://github.com/gabime/spdlog/wiki/3.-Custom-formatting)
- 多线程/单线程日志生成器
- 多种日志目标
  * 循环日志文件
  * 每日日志文件
  * 控制台日志（支持颜色）
  * 系统日志
  * windows事件日志
  * windows debugger(`OutPutDebugString(...)`)
  * 简单地扩展
- 日志过滤 - 日志级别可在运行时和编译时更改
- 支持从传参或环境变量加载日志级别
- Backtrace - 在环形缓存中存储debug信息，在有需要时展示
-
## 使用示例
-