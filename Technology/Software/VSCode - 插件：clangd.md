# 1 安装
## 1.1 安装 clangd 程序
```Bash
sudo apt-get install clangd-18
```

将 `clangd-18` 设置为默认 `clangd`：

```Bash
sudo update-alternatives --install /usr/bin/clangd clangd /usr/bin/clangd-18 100
```

## 1.2 安装 clangd 插件
在 VSCode 插件市场中安装如下几个插件：
![](<./assets/VSCode - 插件：clangd/file-20260302224701009_2.png>)

![](<./assets/VSCode - 插件：clangd/file-20260302224701009.png>)


## 1.3 修改相关配置
修改相关配置，关闭官方 c/c++ 插件的相关功能
- 搜索 `C_Cpp.intelliSenseEngine`，将其设置为 `Disabled`。这会禁用官方插件的IntelliSense引擎，让 clangd 接管诊断、补全等功能
- 搜索 `C_Cpp.autocomplete`，将其设置为 `Disabled`
- 搜索 `C_Cpp.errorSquiggles`，将其设置为 `Disabled`

打开配置及要修改的配置见下边的截图：
![](<./assets/VSCode - 插件：clangd/file-20260302224701008_1.png>)

![](<./assets/VSCode - 插件：clangd/file-20260302224701008.png>)

![](<./assets/VSCode - 插件：clangd/file-20260302224701007_1.png>)

![](<./assets/VSCode - 插件：clangd/file-20260302224701007.png>)

# 2 配置
## 2.1 配置`compile_commands.json`
在 `CMakeLists.txt` 文件中新增配置以生成 `compile_commands.json` 文件：
```CMake
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

// 或者

add_definitions(-DCMAKE_EXPORT_COMPILE_COMMANDS 1)
```

这样项目构建完成后，会自动在 build 文件夹下生成 `compile_commands.json` 文件，这个文件中包含所有要编译文件的编译指令（包含头文件路径等），clangd 要根据这个文件生成所有代码的 index，方便后续的代码补全和跳转操作。

## 2.2 配置参数
个人配置参数如下：
![](<./assets/VSCode - 插件：clangd/file-20260302224701006_2.png>)

> **注意**
> 
> --compile-commands-dir 后边需要设置为 2.1 节中 `compile_commands.json` 文件的位置

下表汇总了 Clangd 的主要命令行参数及其作用：

| **配置项 / 参数**                | **类别** | **说明与常用值**                                                                |
| --------------------------- | ------ | ------------------------------------------------------------------------- |
| --background-index          | 索引     | 启用后台索引。在后台为项目构建索引并持久化到磁盘（.cache/clangd/index/），从而提供更快的代码补全和跳转。            |
| --completion-style          | 补全     | 控制补全建议的显示风格。可选 detailed（为每个重载显示一项）或 bundled（将重载函数组合显示）。                   |
| --clang-tidy                | 静态分析   | 启用 clang-tidy 静态代码分析。提供代码风格、潜在错误、性能问题等诊断提示。可使用 --clang-tidy-checks指定检查规则。 |
| --pretty                    | 日志输出   | 使 JSON 格式的日志输出更易读。                                                        |
| --compile-commands-dir      | 编译命令   | 指定 compile_commands.json文件所在的目录。Clangd 依赖此文件来准确理解项目的编译参数。                 |
| --header-insertion          | 头文件    | 控制是否在接受补全时自动插入 `#include` 指令。推荐值 iwyu（Include What You Use）。              |
| --all-scopes-completion     | 补全     | 允许补全包含所有作用域（如全局、命名空间）的符号。可能会自动插入作用域限定符。                                   |
| --query-driver              | 系统头文件  | 指定一个编译器路径列表（支持通配符）。Clangd 会执行这些编译器来获取系统的头文件搜索路径，对于交叉编译或非标准工具链至关重要。        |
| --function-arg-placeholders | 补全     | 控制函数补全时是否生成参数占位符。启用后，补全函数会产生带参数名的占位符，按 Tab 可依次跳转。                         |
| --pch-storage               | 性能     | 控制预编译头文件的存储方式。可选 memory（性能好，内存占用高）或 disk（内存占用低）。                          |
| --log                       | 日志     | 设置日志详细程度。用于调试，可选 error, info, verbose。                                    |
| -j                          | 性能     | 限制 clangd 使用的后台工作线程数。例如 -j=4。                                             |

## 2.3 其他配置
### 2.3.1 类型提示
clangd 默认会显示变量类型，截图如下：
![](<./assets/VSCode - 插件：clangd/file-20260302224701006_1.png>)

可以将配置修改为下图配置，这样可以通过 `Ctrl + Alt` 快捷键控制变量类型是否显示
![](<./assets/VSCode - 插件：clangd/file-20260302224701006.png>)


# 3 参考文档
- [官方文档](https://clangd.llvm.org/installation)
- [VS Code 插件 clangd的用法](https://www.cnblogs.com/newtonltr/p/18867195)
- [Clangd 常用参数和配置](https://blog.csdn.net/weixin_47820972/article/details/148178780)