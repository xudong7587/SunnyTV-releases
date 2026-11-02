<p align="center"><img src="assets/sunnytv-logo.svg" width="104" alt="SunnyTV"></p>

# SunnyTV

**让自己的媒体库，回到大屏。**

SunnyTV 是适用于 Android TV、手机和平板的原生媒体客户端。连接自己的 Emby、绿联影视中心或 CloudDrive2 WebDAV，在同一个应用里浏览媒体库、挑选影片、继续播放。

[下载最新版 APK](https://github.com/xudong7587/SunnyTV-releases/releases/latest) · [官方网站](https://sunnytv.dunn.fun:666/) · [版本记录](https://github.com/xudong7587/SunnyTV-releases/releases) · [问题反馈](https://github.com/xudong7587/SunnyTV-releases/issues)

![SunnyTV 首页演示](assets/home.webp)

## 为自己的媒体库留一块好屏幕

- **电视直播**：支持用户提供的 HTTP(S) M3U / M3U8 频道列表，应用不内置任何直播源。
- **浏览与发现**：首页推荐、媒体库分类、海报墙、详情和搜索，优先展示媒体服务器已有的海报、背景和 Logo。
- **接着看**：查看播放进度与收藏，在媒体库中继续上次的观看。
- **按自己的习惯播放**：音轨、字幕和播放设置；支持 STRM 与云端媒体链接，实际可播放格式取决于设备及媒体来源。
- **大屏与触屏**：适配电视遥控器，也支持手机和平板的触摸操作。
- **自己的界面**：深浅主题、字体和外观设置，兼顾客厅大屏与随身设备。

| 海报墙 | 浅色主题 |
| --- | --- |
| ![媒体库海报墙](assets/grid.webp) | ![浅色首页](assets/light.webp) |

以上为原生界面的原创演示截图，片名与海报均为虚构素材，不含用户媒体库。实际界面随版本、设备和设置而变化。

## 安装与升级

1. 使用 Android 7.0 或更高版本的电视、盒子、手机或平板。
2. 打开[最新版下载页](https://github.com/xudong7587/SunnyTV-releases/releases/latest)，在 Assets 中下载 `.apk` 文件。
3. 按系统提示允许该安装来源，安装后添加自己的媒体服务器或云端来源。

**从 1.0.9 或更早版本升级时，需要从这里手动下载一次 1.1.0 或更高版本，并直接覆盖安装。** 从 1.1.0 起，应用内升级改用本仓库。使用官方签名的安装包覆盖安装即可，无需先卸载。

每个版本提供三个附件：APK 安装包、`BUILD_INFO.txt` 版本信息、`SHA256SUMS.txt` 校验文件。应用会检查版本与安装包身份。GitHub 自动显示的 Source code 压缩包不包含应用源码，请下载 APK。

## 使用与反馈

SunnyTV 不提供影视资源，需要使用自己的服务器、账号及有权访问的媒体。不同来源的收藏、进度和播放能力以对应服务支持情况为准。

遇到问题可以到 [Issues](https://github.com/xudong7587/SunnyTV-releases/issues) 描述应用版本、设备型号、Android 版本及复现步骤。截图和日志请先隐藏服务器地址、账号、令牌及私人媒体信息。

这个仓库用于发布安装包、更新说明与收集反馈。产品介绍与更多展示请查看[官方网站](https://sunnytv.dunn.fun:666/)。
