# 1 背景
VSCode升级到1.86后，不再支持远程链接 glibc2.28 以下的Linux服务器，想要远程老版本的服务器（不升级服务器版本），又不想要降级本地 VSCode 版本，可以下载使用 VSCode 便携版，可以与本地已经安装的 VSCode 共存。

# 2 下载
下载指定版本，参考官方网页
https://code.visualstudio.com/docs/supporting/faq#_previous-release-versions

比如，要下载 Linux 平台 1.85.2 版本的链接为：
https://update.code.visualstudio.com/1.85.2/linux-x64/stable

即可获得如下压缩包：
![](<./assets/VSCode - 便携模式/file-20260302224638062.png>)

# 3 使用
解压上一步得到的安装包，并在解压得到的主文件夹新建一个名为 `data` 的文件夹：![](<./assets/VSCode - 便携模式/file-20260302224638063.png>)

然后给可执行文件赋可执行权限：

```Bash
chmod +X code
```

然后在命令行执行主程序：
```Bash
./code
```

然后根据需要登录 VSCode 账号，并安装相应插件即可。

# 4 参考文档
- 官方文档：[便携模式 - VSCode 编辑器](https://vscode.js.cn/docs/editor/portable)
- [避坑必备：免安装便携版VSCode](https://techdiylife.github.io/blog/blog.html?category1=c03&blogid=0024)
