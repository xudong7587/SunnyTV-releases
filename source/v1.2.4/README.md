# SunnyTV 1.2.4 解码组件和 FFmpeg 换库

SunnyTV 1.2.4 的音视频解码适配源码及 FFmpeg 共享库沿用 1.2.3。四个架构共 16 个 FFmpeg 共享库逐字节相同，对应以下源码和构建配置。

- [FFmpeg n6.0.1 对应源码](../v1.2.3/FFmpeg-n6.0.1-source.tar.gz)
- [Apache-2.0 解码适配源码、构建脚本及换库工具](../v1.2.3/SunnyTV-v1.2.3-decoder-source.tar.gz)
- [上述源码校验值](../v1.2.3/SHA256SUMS.txt)
- [本版 APK 对象代码](https://github.com/xudong7587/SunnyTV-releases/releases/download/v1.2.4/SunnyTV-v1.2.4.apk)
- [FFmpeg 换库、重签和运行说明](../v1.2.3/FFMPEG-RELINK.md)
- [应用分发条款](../v1.2.3/SunnyTV-distribution.txt)

对本版换库时，将工具的输入 APK 指向上面的 1.2.4 正式包。用户可替换 FFmpeg 共享库、重新签名并安装运行。脚本和条款支持该操作。FFmpeg 采用 LGPL-3.0-or-later，音视频适配采用 Apache-2.0。

本次客户端新增 ISO 读取和 Emby 播放识别。Android 主程序原创部分沿用其安装包分发条款。旧版对应资料继续保留。
