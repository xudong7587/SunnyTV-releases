# SunnyTV 1.2.6 解码组件和 FFmpeg 换库

SunnyTV 1.2.6 的音视频解码适配源码及 FFmpeg 共享库沿用 1.2.3。四个架构共16个 FFmpeg 共享库以正式 APK 的发布核验记录为准，对应以下源码和构建配置。

- [FFmpeg n6.0.1 对应源码](../v1.2.3/FFmpeg-n6.0.1-source.tar.gz)
- [Apache-2.0 解码适配源码、构建脚本及换库工具](../v1.2.3/SunnyTV-v1.2.3-decoder-source.tar.gz)
- [上述源码校验值](../v1.2.3/SHA256SUMS.txt)
- [本版 APK 对象代码](https://github.com/xudong7587/SunnyTV-releases/releases/download/v1.2.6/SunnyTV-v1.2.6.apk)
- [FFmpeg 换库、重签和运行说明](../v1.2.3/FFMPEG-RELINK.md)
- [应用分发条款](../v1.2.3/SunnyTV-distribution.txt)

对本版换库时，将工具的 `--apk` 指向上面的1.2.6正式包，勿将旧版 unsigned APK 当成新版完整应用。换库工具支持从原始正式 APK 替换FFmpeg动态库、使用用户自己的现有密钥重新签名并安装运行，不修改原始正式包。FFmpeg采用 LGPL-3.0-or-later，音视频适配采用Apache-2.0。

本次更新涉及关于页、自动更新默认下载选择、设置拨块与聚焦显示，未修改音视频解码器源码。Android主程序原创部分沿用其安装包分发条款，旧版对应资料继续保留。本目录 `BUILD.json` 记录本版已核验的正式APK身份、包大小、SHA256及对应组件信息；28个native库与1.2.5逐字节一致，其中16个FFmpeg共享库继续匹配原公开源码和构建配置。
