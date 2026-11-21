# SunnyTV 1.2.7 解码组件和 FFmpeg 换库

SunnyTV 1.2.7 的音视频解码适配源码及 FFmpeg 共享库沿用 1.2.3。本版修复 Banner 背景过渡与剧集续播，并在连续换集时沿用裁切或适应的画面模式及字幕选择。

- [FFmpeg n6.0.1 对应源码](../v1.2.3/FFmpeg-n6.0.1-source.tar.gz)
- [Apache-2.0 解码适配源码、构建脚本及换库工具](../v1.2.3/SunnyTV-v1.2.3-decoder-source.tar.gz)
- [上述源码校验值](../v1.2.3/SHA256SUMS.txt)
- [本版 APK 对象代码](https://github.com/xudong7587/SunnyTV-releases/releases/download/v1.2.7/SunnyTV-v1.2.7.apk)
- [FFmpeg 换库、重签和运行说明](../v1.2.3/FFMPEG-RELINK.md)
- [应用分发条款](../v1.2.3/SunnyTV-distribution.txt)

对本版换库时，将工具的 `--apk` 指向上面的 1.2.7 正式包。工具可从正式 APK 替换 FFmpeg 动态库，再使用用户自己的密钥给替换后的安装包重新签名。FFmpeg 采用 LGPL-3.0-or-later，音视频适配采用 Apache-2.0。

[BUILD.json](BUILD.json) 记录本版公开 APK 的应用标识、版本号、文件大小、SHA-256 及对应组件信息。APK 中的 28 个原生库与 1.2.6 逐字节一致，其中 16 个为 FFmpeg 共享库。
