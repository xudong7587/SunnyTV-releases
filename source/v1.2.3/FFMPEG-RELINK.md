# 使用自行修改的 FFmpeg 重新组合 Android APK

本说明描述一种供使用者尝试替换 FFmpeg 动态库的技术路径：从可取得的 SunnyTV APK 取出应用对象代码，替换指定架构的四个 FFmpeg 共享库，使用使用者自己的密钥签名新 APK。它不需要 SunnyTV 私钥，不修改输入 APK，也不自动安装或卸载应用。

这份说明本身不证明许可证合规或运行兼容性。修改后的库必须与对应应用版本的 ABI、FFmpeg API 和依赖兼容；播放正确性、色彩、性能及设备兼容性需要使用者自行验证。安装和签名的要求取决于设备和分发方式。

## 选择基础 APK

- **独立的 FFmpeg relink APK**：如发行方另外提供与该版对应的未签名 `ffmpegrelink` APK，可用自己的密钥重签；它使用独立应用 ID，可与稳定版并存，应用数据相互隔离。
- **正式 APK**：也可以使用用户已取得的原版通用 APK 作为输入。脚本保留其原包名，用自己的密钥重签后，Android 不允许它覆盖由不同证书签名的已安装稳定版。请使用未安装该包的独立设备或模拟器；脚本不会卸载现有应用或迁移数据。

不要使用 SunnyTV 正式签名密钥。用户自己的密钥与密码由用户保管；此脚本不会生成、下载或记录密钥。用户可为修改后的版本自行决定如何签名与安装。

## 构建用户修改的库

以 FFmpeg n6.0.1 为基线准备用户自己的源码副本并修改。`scripts/build-modified-ffmpeg-macos.sh` 基于 SunnyTV 1.2.2 的共享库配置，不要求源码工作树干净，也接受从源码归档解压的目录。需要 JDK 17、Android NDK `26.1.10909125`、Android API 24 编译工具以及 macOS 终端；构建 x86_64 时还需 NASM。示例只构建 ARM64：

```bash
export ANDROID_HOME=/path/to/Android/sdk
export SUNNYTV_FFMPEG_ABI=arm64-v8a
bash scripts/build-modified-ffmpeg-macos.sh /path/to/modified-ffmpeg /path/to/new-ffmpeg-build
```

例如结果位于 `/path/to/new-ffmpeg-build/install/arm64-v8a/lib/`。完整四架构构建时不设置 `SUNNYTV_FFMPEG_ABI`。请保留自己使用的完整源码、修改、构建配置和工具版本；不要覆盖发行方的原始源码或已安装的 APK。

## 组合并签名

以下示例使用自己的已有密钥。请先设置 Android SDK、解码库目录、输入 APK 和输出位置。密码通过环境变量交给 Android `apksigner`；不要把密码写入命令历史、脚本或公开文件。

```bash
export ANDROID_HOME=/path/to/Android/sdk
read -r -s -p 'Keystore password: ' SUNNYTV_RELINK_STORE_PASS; echo
export SUNNYTV_RELINK_STORE_PASS
python3 scripts/relink-ffmpeg-apk.py \
  --apk /path/to/input.apk \
  --abi arm64-v8a \
  --libs-dir /path/to/new-ffmpeg-build/install/arm64-v8a/lib \
  --out /path/to/new-output.apk \
  --keystore /path/to/your-own-keystore \
  --key-alias your-key-alias \
  --zipalign "$ANDROID_HOME/build-tools/35.0.0/zipalign" \
  --apksigner "$ANDROID_HOME/build-tools/35.0.0/apksigner" \
  --aapt "$ANDROID_HOME/build-tools/35.0.0/aapt" \
  --readelf "$ANDROID_HOME/ndk/26.1.10909125/toolchains/llvm/prebuilt/darwin-x86_64/bin/llvm-readelf"
unset SUNNYTV_RELINK_STORE_PASS
```

密钥条目的密码不同于 keystore 密码时，可将它放在另外一个环境变量中，并通过 `--key-pass-env VARIABLE_NAME` 指定。上例中的 NDK 主机路径适用于 macOS；其他主机需指定本机 NDK 对应的 `llvm-readelf` 路径。`--expected-input-sha256` 可额外核对输入 APK。

脚本要求目标架构的 `libavcodec.so`、`libavutil.so`、`libswresample.so` 和 `libswscale.so` 同时提供；只替换指定 ABI，其他架构保持输入 APK 的内容。它检查 ELF 架构、SONAME、部分依赖、JNI 和共享库所需的 FFmpeg 动态符号及版本、16 KiB 段对齐，生成新的对齐 APK，以用户的密钥签名，再检查签名、包身份和替换库回读。输出路径必须不存在。

这些静态核对不能证明修改库与应用所有接口兼容，也不能证明 Android 设备能播放。使用者应在隔离设备验证；请勿覆盖或卸载含有重要数据的稳定版。
