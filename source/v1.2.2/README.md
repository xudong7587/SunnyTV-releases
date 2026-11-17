# SunnyTV 1.2.2 解码器源码与 FFmpeg 源码

这份资料覆盖 SunnyTV 1.2.2 音视频解码组件及其构建材料，取自产品提交 `c3dd333738b1e22ff0f52fe0e1e7f587c61051cd`。**整个 APK 的对应源码尚未提供。**

## 文件

- [`SunnyTV-v1.2.2-decoder-source.tar.gz`](SunnyTV-v1.2.2-decoder-source.tar.gz)：音频和视频解码器生产源码、JNI、构建脚本、构建配置、FFmpeg 公共头文件、版权及许可证。[`FILES.txt`](FILES.txt) 列出归档中的文件。
- [`FFmpeg-n6.0.1-source.tar.gz`](FFmpeg-n6.0.1-source.tar.gz)：FFmpeg n6.0.1 上游固定提交 `c41ff724ede7da657762d61097e26fac296c53bf` 的完整源码树，未包含 Git 历史。
- [`SHA256SUMS.txt`](SHA256SUMS.txt)：上述文件及说明的 SHA-256。

## 来源与许可

视频 renderer 基于 Anil Kumar Beesetti 及贡献者的 [NextLib](https://github.com/anilbeesetti/nextlib/tree/175beb9811ce5712ddb0003e0d6cfb6845f8bdcc) 修改；随源码保留 GPL-3.0-or-later 版权和许可证。音频 Java/JNI 适配来自 [AndroidX Media3 1.9.4](https://github.com/androidx/media/tree/75ccb55ec085d76cbbf12e2f1af8241d378a753a)，保留 Apache-2.0 声明。

音视频复用由 [FFmpeg n6.0.1](https://github.com/FFmpeg/FFmpeg/tree/c41ff724ede7da657762d61097e26fac296c53bf) 构建的共享库。本版配置启用 `--enable-version3`，相关 FFmpeg 运行库适用 LGPL-3.0-or-later。具体文件中的版权声明和所附许可证仍然有效；上游链接用于追溯，不能替代 SunnyTV 修改后版本的对应源码。

## 构建材料

源码归档中的 `scripts/build-shared-ffmpeg-macos.sh` 是 1.2.2 使用的 FFmpeg 构建脚本，记录了完整的解码器白名单、四种 ABI、SIMD 与链接参数。脚本使用 Android NDK `26.1.10909125`、Android API 24 和 NASM 3.02；设置 `ANDROID_HOME` 与 NASM 所在的 `PATH`，再向脚本传入 FFmpeg 源码目录和输出目录。

脚本会核对 FFmpeg Git 提交和工作树；因为本页提供的 FFmpeg 归档不含 `.git`，运行原脚本须使用官方 Git 仓库中该固定提交的干净检出。源码归档本身可供离线阅读和按脚本中的参数构建。构建出的四 ABI 共享库需分别放在 `decoder-video/src/main/cpp/vendor/lib/<ABI>/` 后，供解码器模块的 CMake 使用。Gradle 版本为 8.11.1，Android Gradle Plugin 为 8.9.2，JDK 为 17；具体依赖声明保留在构建文件中。源码快照不包含主应用，原 `settings.gradle.kts` 中的 `:app` 不存在，因此不能直接据此构建完整 APK。

只编译两个解码模块时，请在解包副本的 `settings.gradle.kts` 中移除 `include(":app")`，然后执行 `gradle :decoder-ffmpeg:assembleRelease :decoder-video:assembleRelease`。已核对归档文件，尚未验证独立重建和播放。

发行 APK 为 1.2.2 / 116，可在[正式发行页](https://github.com/xudong7587/SunnyTV-releases/releases/tag/v1.2.2)查看。
