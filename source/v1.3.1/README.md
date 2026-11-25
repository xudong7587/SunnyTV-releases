# Sunny 1.3.1 解码组件和 FFmpeg 换库

Sunny 1.3.1 沿用 1.2.3 对应的音视频解码适配源码和 FFmpeg 共享库。与 [1.3.0 正式包](../v1.3.0/BUILD.json)相比，四种架构共 8 个 JNI 适配库随本版重建，其余 20 个原生库逐字节一致。FFmpeg 采用 LGPL-3.0-or-later，音视频解码适配采用 Apache-2.0。

- [FFmpeg n6.0.1 对应源码](../v1.2.3/FFmpeg-n6.0.1-source.tar.gz)
- [Apache-2.0 解码适配源码、构建脚本及换库工具](../v1.2.3/SunnyTV-v1.2.3-decoder-source.tar.gz)
- [源码资料校验值](../v1.2.3/SHA256SUMS.txt)
- [Sunny 1.3.1 正式 APK](https://github.com/xudong7587/SunnyTV-releases/releases/download/v1.3.1/SunnyTV-v1.3.1.apk)
- [FFmpeg 换库、重签和运行说明](../v1.2.3/FFMPEG-RELINK.md)
- [应用分发条款](../v1.2.3/SunnyTV-distribution.txt)

对本版换库时，将工具的 `--apk` 指向 1.3.1 正式包，再使用自己的密钥为替换后的安装包签名。

[BUILD.json](BUILD.json) 记录本版 APK 的应用标识、版本、大小、SHA-256 和组件信息。
