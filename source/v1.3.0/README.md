# Sunny 1.3.0 解码组件和 FFmpeg 换库

Sunny 1.3.0 是维护版本。音视频解码适配源码和 16 个 FFmpeg 共享库继续使用 1.2.3 对应资料。与 [1.2.9 正式包](../v1.2.9/BUILD.json)相比，四种架构的 JNI 适配库共 8 个随本版重建，其余 20 个原生库逐字节一致。

- [FFmpeg n6.0.1 对应源码](../v1.2.3/FFmpeg-n6.0.1-source.tar.gz)
- [Apache-2.0 解码适配源码、构建脚本及换库工具](../v1.2.3/SunnyTV-v1.2.3-decoder-source.tar.gz)
- [上述源码校验值](../v1.2.3/SHA256SUMS.txt)
- [本版 APK 对象代码](https://github.com/xudong7587/SunnyTV-releases/releases/download/v1.3.0/SunnyTV-v1.3.0.apk)
- [FFmpeg 换库、重签和运行说明](../v1.2.3/FFMPEG-RELINK.md)
- [应用分发条款](../v1.2.3/SunnyTV-distribution.txt)

对本版换库时，将工具的 `--apk` 指向 1.3.0 正式包。工具可从正式 APK 替换 FFmpeg 动态库，再使用用户自己的密钥给替换后的安装包签名。FFmpeg 采用 LGPL-3.0-or-later，音视频解码适配采用 Apache-2.0。

[BUILD.json](BUILD.json) 记录本版 APK 的应用标识、版本、大小、SHA-256 和对应组件信息。
