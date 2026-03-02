# 1 背景
VSCode 更新到 1.92.0 版本以后，出现 ContextMenu 显示内容间距过大的问题，包括 editor 中右键菜单的显示同样发生了变化，个人感觉美观和可读性均受到了影响，比较如下，上边是原始版本，下边是新版本的外观：
![](<./assets/VSCode - 菜单栏显示问题/file-20260302224649960.png>)

![](<./assets/VSCode - 菜单栏显示问题/file-20260302224649961.png>)

# 2 解决方案
快捷键 `Ctrl`+`,` 打开配置项，搜索 `window.titleBarStyle`，将该配置项从 `native` 改为 `custom`，然后根据提示重启窗口即可生效
![](<./assets/VSCode - 菜单栏显示问题/file-20260302224649961_1.png>)

修改配置之后的效果如下，整体更加紧凑
![](<./assets/VSCode - 菜单栏显示问题/file-20260302224649962.png>)

# 3 参考文档
- Github Issue: [Context menu gets too small depending on the cursor position](https://github.com/microsoft/vscode/issues/224515#issuecomment-2267264540)
