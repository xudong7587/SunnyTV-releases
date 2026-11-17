# SunnyTV 1.2.3 解码组件源码和 FFmpeg 换库

SunnyTV 1.2.3 的主程序以 APK 形式提供，适用[安装包分发条款](SunnyTV-distribution.txt)。视频软解渲染器、队列和 JNI 桥依据 Media3、FFmpeg 与 Android NDK 的公开接口重写，采用 Apache-2.0。音频适配来自 AndroidX Media3 1.9.4，沿用 Apache-2.0。两套适配共用 FFmpeg n6.0.1 的四个动态库，发行配置采用 LGPL-3.0-or-later，未启用 GPL 或 nonfree 组件。

- [解码器源码包](SunnyTV-v1.2.3-decoder-source.tar.gz)包含音视频解码器源码、版权和许可证、构建配置、FFmpeg 公开头文件及换库工具。[文件清单](FILES.txt)列出包内条目。
- [FFmpeg 对应源码包](FFmpeg-n6.0.1-source.tar.gz)来自固定上游提交 `c41ff724ede7da657762d61097e26fac296c53bf`。原版和用户修改版的编译脚本均包含在解码器源码包中。
- [可共存的未签名换库 APK](SunnyTV-v1.2.3-ffmpeg-relink-unsigned.apk)包含与正式版对应的应用对象代码，使用独立应用 ID。它需要先按[换库说明](FFMPEG-RELINK.md)重组并用自己的密钥签名。也可直接重组[正式通用 APK](https://github.com/xudong7587/SunnyTV-releases/releases/tag/v1.2.3)。
- [SHA-256 校验文件](SHA256SUMS.txt)包含上述源码、构建说明和未签名 APK 的校验值。

## 构建解码组件

解包后先使用 `scripts/build-shared-ffmpeg-macos.sh` 与 FFmpeg 官方 Git 仓库的固定提交重建原版共享库，或使用 `scripts/build-modified-ffmpeg-macos.sh` 从解压出的源码构建。需要 Android NDK `26.1.10909125`、API 24 和 JDK 17，构建 x86_64 时还需 NASM。将四种 ABI 构建得到的 `libavcodec.so`、`libavutil.so`、`libswresample.so`、`libswscale.so` 分别复制到 `decoder-video/src/main/cpp/vendor/lib/<ABI>/`，运行 `./gradlew :decoder-ffmpeg:assembleRelease :decoder-video:assembleRelease`。Gradle 使用 Android SDK 35 和 CMake 3.22.1。

已在 Android 15 ARM64 模拟器用实际修改并重建的库验证并存、重签、音视频库加载和解码。1.2.2 的源码与许可资料继续保存在[对应版本目录](../v1.2.2/)。
