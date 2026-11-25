# 版本记录

## Sunny 1.3.1 /125

- 手机连续播放剧集时，手动滑动调节的亮度和音量会延续到下一集，退出播放后恢复手机原有设置。
- 改善续播和片尾自动换集时的进度保存。应用内检查更新超时后会提示重试。
- 修复媒体来源读取异常时的恢复入口、设置二级菜单的遥控焦点，以及选择弹窗在屏幕阅读器中的选中提示。

[发行说明](https://github.com/xudong7587/SunnyTV-releases/releases/tag/v1.3.1) · [下载最新版](https://github.com/xudong7587/SunnyTV-releases/releases/latest) · [解码组件源码与许可](source/v1.3.1/README.md)

## Sunny 1.3.0 /124

- 维护版本，延续按设备档位调整弹出卡片和外接显示器适配。
- 沿用现有安装包身份和签名。可从 1.2.9 覆盖升级，保留媒体来源、偏好和播放记录。

[发行说明](https://github.com/xudong7587/SunnyTV-releases/releases/tag/v1.3.0) · [下载最新版](https://github.com/xudong7587/SunnyTV-releases/releases/latest) · [解码组件源码与许可](source/v1.3.0/README.md)

## Sunny 1.2.9 /123

- 设置、片源、字幕、音轨和播放选项按当前窗口的可用宽高和界面缩放布局。手机横竖屏分别留边，较长的选项列表可滚动。
- 电视和外接屏的 4K 窗口按电视布局比例显示。分辨率设置显示实际生效的档位，设备诊断可查看应用窗口和外接显示器信息。
- 「优先外接显示器」可在支持多屏应用且仅有一块可用外接屏的设备上，把 Sunny 打开在该屏幕。
- 沿用原包身份和签名，可覆盖安装 1.2.8 并保留媒体来源、偏好和播放记录。

[发行说明](https://github.com/xudong7587/SunnyTV-releases/releases/tag/v1.2.9) · [下载最新版](https://github.com/xudong7587/SunnyTV-releases/releases/latest) · [解码组件源码与许可](source/v1.2.9/README.md)

## Sunny 1.2.8 /122

- Android 桌面、应用内界面与官网统一使用 Sunny。
- 可直接覆盖安装旧版，保留媒体来源、偏好设置和播放进度。

[下载最新版](https://github.com/xudong7587/SunnyTV-releases/releases/latest)

## 1.2.7 /121

- Banner 在新背景加载期间保留上一张图和最近一次成功的 Monet 取色。新图到位后平滑过渡，蒙版色随新取色渐变，修复切换时的紫红色闪屏。
- 同一剧集切换单集时沿用画面裁切或适应。手动选择的字幕在可匹配的轨道中沿用，关闭字幕的选择也随剧集保存。
- 续播以总时长的 95% 判断是否接近播完，并保留有效的毫秒级观看进度，修复一两分钟的短剧容易提前跳到下一集的问题。

[发行说明](https://github.com/xudong7587/SunnyTV-releases/releases/tag/v1.2.7) · [下载最新版](https://github.com/xudong7587/SunnyTV-releases/releases/latest) · [解码组件源码与许可](source/v1.2.7/README.md)

## 1.2.6 /120

- 关于页简化介绍，分层展示当前与最新版本、四种更新渠道、自动更新和开发者说明。
- 开启自动更新前选择官网或 GitHub 默认下载方式，官网提示可能较慢；取消不启用，开启后可修改，版本查询来源与下载选择分别保存。
- 设置及灯带的开启/关闭项统一为随当前主题变化的拨块，适配现有16种材质；多选设置继续使用选择器，媒体库成员继续勾选。
- 纸页暗纹改为水平横线；金属采用细密不规则拉丝，大理石采用天然不规则主脉、次脉及分支。金属和亚麻凹槽不叠纹理，拨块保留材质。
- 大理石、金属、浮雕、瓷面、纸页、亚麻增加克制的槽凹、块凸层次；设置聚焦框统一在卡片内部留出间隙，四角均为圆角。
- 保留原有默认档位、已保存偏好、Banner横竖槽位及正常图片优先级，播放器与液态玻璃光学路径保持。

[发行说明](https://github.com/xudong7587/SunnyTV-releases/releases/tag/v1.2.6) · [实际最新版](https://github.com/xudong7587/SunnyTV-releases/releases/latest)

## 1.2.5 /119

- 版本检查默认使用官方服务器，不可用时回退 GitHub，支持手动保存 GitHub 查询选择。
- 更新页提供官方服务器、GitHub、官网和夸克等渠道，沿用下载校验与系统安装确认。
- 多季详情完整显示所有季，选集以 S/E 季集号区分。
- Banner 按实际显示区域与图片比例请求图片；保留正常槽位横竖方向、优先级和季集归属，仅对应方向缺失或加载失败时允许另一方向裁切补位；同图最多一次质量补充，源图低清不反复重试。
- 保留多个原生背景索引和父级缩略图；缺少方向时有界补充最新单集候选，失败或超时仍保留已有图片。

[完整发行说明](https://github.com/xudong7587/SunnyTV-releases/releases/tag/v1.2.5) · [下载最新版](https://github.com/xudong7587/SunnyTV-releases/releases/latest)

## 1.2.4 /118

- 支持未加密蓝光 ISO 的单片段正片播放，支持续播与进度跳转。
- 修复 Emby 播放地址缺少 ISO 格式信息时出现的3003错误，保留认证作用域与原画入口。

[发行说明](https://github.com/xudong7587/SunnyTV-releases/releases/tag/v1.2.4)

更早的发行说明和安装包继续保留在 [Releases](https://github.com/xudong7587/SunnyTV-releases/releases)。
