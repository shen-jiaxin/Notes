# 1 安装
安装插件
![](<./assets/VSCode - 插件：background/file-20260302224656367.png>)

# 2 配置
## 2.1 打开 setting.json 文件
快捷键：`Ctrl`+`,` 打开 Settings 选项卡
打开配置文件：
![](<./assets/VSCode - 插件：background/file-20260302224656368.png>)

## 2.2 修改配置项
窗口位置说明：
![](<./assets/VSCode - 插件：background/file-20260302224656369.png>)

主要配置项说明：  

| **Name**   | **Type**   | **Default** | **Description**                                                                                                                 |
| ---------- | ---------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `images`   | `string[]` | `[]`        | Custom images, supports online and local images, as well as folders.                                                            |
| `opacity`  | `number`   | `0.1`       | Opacity of the images, alias to [opacity](https://developer.mozilla.org/docs/Web/CSS/opacity), `0.1 ~ 0.3` recommended.         |
| `size`     | `string`   | `cover`     | Alias to [background-size](https://developer.mozilla.org/docs/Web/CSS/background-size), `cover` to self-adaption (recommended). |
| `position` | `string`   | `center`    | Alias to [background-position](https://developer.mozilla.org/docs/Web/CSS/background-position), default `center`.               |
| `interval` | `number`   | `0`         | Seconds of interval for carousel, default `0` to disabled.                                                                      |
| `random`   | `boolean`  | `false`     | Whether to randomly display images.                                                                                             |

在 `settings.json` 文件最后新增如下配置项：

```JSON
"background.fullscreen": {
    "useFront": true,
    "style": {
        "background-position": "100% 100%",
        "background-size": "auto",
        "opacity": 0.9
    },
    "styles": [
        {},
        {},
        {}
    ],
    "images": ["/home/shenjiaxin/Pictures/vscode/wallpaper"],
    "interval": 30,
    "random": true
},
"background.panel": {
    "useFront": true,
    "style": {
        "background-position": "100% 100%",
        "background-size": "auto",
        "opacity": 0.6
    },
    "styles": [
        {},
        {},
        {}
    ],
    "images": ["/home/shenjiaxin/Pictures/vscode/panel"],
    "interval": 30,
    "random": false
},
"background.enabled": true
```

图片路径换成自己的，保存配置并重新启动窗口

# 3 问题
## 3.1 read-only file system - 各种无权限问题
需要 `vscode` 位于一个有可写权限的位置.
- windows:
    - 右键 `vscode` 图标，选择 `以管理员身份运行`。

- mac:
    - 把 vscode 从 `Download/下载` 目录移动到 `Application/应用` 目录.
    - 执行 `sudo chmod -R a+rw '/Applications/Visual Studio Code.app'` 来提升权限.
        
- linux:
    - 执行 `sudo chmod -R a+rw /usr/share/code`。
    - 一些 Arch Linux: `sudo chmod -R a+rw /opt/visual-studio-code`
    - Code Server (docker): `sudo chmod -R a+rw '/usr/lib/code-server'`
        - code-server 需要强制刷新浏览器（避免缓存）来使配置生效。

# 4 参考文档
- [官方 github](https://github.com/shalldie/vscode-background/tree/master)
- [官方 issue 解决](https://github.com/shalldie/vscode-background/blob/master/docs/common-issues.zh-CN.md)
- 图片下载：[欧莱凯设计网](https://www.2008php.com/)

# 5 附件

| 位置        | 图片                                                                                                                                                                                                                                                                                                                                                                    |
| --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| wallpaper | ![](<./assets/VSCode - 插件：background/file-20260302224656387.png>)<br><br>![](<./assets/VSCode - 插件：background/file-20260302224656388.png>)<br><br>![](<./assets/VSCode - 插件：background/file-20260302224656388_1.png>)<br><br>![](<./assets/VSCode - 插件：background/file-20260302224656389.png>)<br><br>![](<./assets/VSCode - 插件：background/file-20260302224656390.png>) |
| panel     | ![](<./assets/VSCode - 插件：background/file-20260302224656390_1.png>)<br><br>![](<./assets/VSCode - 插件：background/file-20260302224656391.png>)                                                                                                                                                                                                                            |

