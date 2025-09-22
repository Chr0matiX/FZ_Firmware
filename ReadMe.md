# Flipper Zero 固件

- [Flipper Zero 官方网站](https://flipperzero.one)：向朋友介绍 Flipper Zero 功能的简易方式。
- [Flipper Zero 固件更新](https://flipperzero.one/update)：最新固件版本及 PC/移动设备升级工具。
- [用户文档](https://docs.flipper.net)：了解设备规格、使用指南及常见问题。
- [开发者文档](https://developer.flipper.net/flipperzero/doxygen)：深入了解固件源码、构建系统及结构。

# 贡献

我们的目标是围绕 Flipper 构建健康、可持续的社区，欢迎新想法和贡献。请仔细阅读本页及[行为准则](/CODE_OF_CONDUCT.md)。

## 需要帮助

优先查阅[用户文档](https://docs.flipper.net)。如未找到答案，可访问[Discord 服务器](https://flipp.dev/discord)或[论坛](https://forum.flipperzero.one/)。若想参与固件开发或自定义，参考[开发者文档](https://developer.flipper.net/flipperzero/doxygen)。

## 报告问题

发现问题请访问[Issues](https://github.com/flipperdevices/flipperzero-firmware/issues)页面。描述需包含固件版本、平台及重现步骤。

## 贡献代码

提交 PR 前，确认更改是否必须包含在固件中。许多想法可作为外部应用实现并发布到[Flipper 应用目录](https://github.com/flipperdevices/flipper-application-catalog)。如不确定，请在[Discord 服务器](https://flipp.dev/discord)或[Issues](https://github.com/flipperdevices/flipperzero-firmware/issues)咨询。

阅读[贡献指南](/CONTRIBUTING.md)、[编码规范](/CODING_STYLE.md)，确保代码符合[项目许可](/LICENSE)。

最后，提交[Pull Request](https://github.com/flipperdevices/flipperzero-firmware/pulls)，确保 CI/CD 状态全绿。

# 开发

Flipper Zero 固件主要用 C 编写，部分使用 C++ 和 armv7m 汇编。建议具备中级 C 编程知识。支持 Flipper 应用的语言包括 C、C++ 和 armv7m 汇编。

# 固件路线图

[固件路线图 Miro 板](https://miro.com/app/board/uXjVO_3D6xU=/)

## 要求

支持的开发平台：
- Windows 10+（带 PowerShell 和 Git，x86_64）
- macOS 12+（带命令行工具，x86_64/arm64）
- Ubuntu 20.04+（带 build-essential 和 Git，x86_64）

支持的在线调试器（可选但强烈推荐）：
- [Flipper Zero Wi-Fi 开发板](https://shop.flipperzero.one/products/wifi-devboard)
- CMSIS-DAP 兼容：Raspberry Pi Debug Probe 等
- ST-Link（v2、v3、v3mods）
- J-Link

Flipper 构建系统会处理其他依赖。

## 克隆源码

确保空间充足，克隆源码：
```shell
git clone --recursive https://github.com/flipperdevices/flipperzero-firmware.git
```

## 构建

使用 Flipper Build Tool 构建固件：
```shell
./fbt
```

## 使用在线调试器刷写固件

连接在线调试器，使用 Flipper Build Tool 刷写固件：
```shell
./fbt flash
```

## 使用 USB 刷写固件

确保 Flipper Zero 开机且固件正常，连接 USB 线，使用 Flipper Build Tool 刷写：
```shell
./fbt flash_usb
```

## 文档

- [Flipper Build Tool](/documentation/fbt.md)：构建、刷写和调试 Flipper 软件
- [应用](/documentation/AppsOnSDCard.md)、[应用清单](/documentation/AppManifests.md)：开发、构建、部署和调试 Flipper 应用
- [硬件组合与修复](/documentation/KeyCombo.md)：从严重问题中恢复设备
- [Flipper 文件格式](/documentation/file_formats)：设备数据存储及操作
- [通用遥控](/documentation/UniversalRemotes.md)：为通用遥控数据库贡献红外遥控
- [固件路线图](https://miro.com/app/board/uXjVO_3D6xU=/)
- 更多内容见[开发者文档](https://developer.flipper.net/flipperzero/doxygen)

# 项目结构

- `applications`：固件使用的应用和服务
- `applications_users`：用户添加的应用和服务
- `assets`：应用和服务使用的资源
- `documentation`：文档生成系统配置和输入文件
- `furi`：Furi 核心，操作系统级原语和辅助工具
- `lib`：自有及第三方库、驱动、工具等
- `site_scons`：构建系统配置和模块
- `scripts`：辅助脚本和 Python 库
- `targets`：固件目标，平台特定代码

详情见各目录下的 `ReadMe.md` 文件。

# 链接

- Discord: [flipp.dev/discord](https://flipp.dev/discord)
- 网站: [flipperzero.one](https://flipperzero.one)
- 论坛: [forum.flipperzero.one](https://forum.flipperzero.one/)
- Kickstarter: [kickstarter.com](https://www.kickstarter.com/projects/flipper-devices/flipper-zero-tamagochi-for-hackers)

## SAST 工具

- [PVS-Studio](https://pvs-studio.com/pvs-studio/?utm_source=website&utm_medium=github&utm_campaign=open_source)：C、C++、C# 和 Java 代码静态分析工具。

------------------------------------------------------------------------------------------

# Flipper Zero Firmware

- [Flipper Zero Official Website](https://flipperzero.one). A simple way to explain to your friends what Flipper Zero can do.
- [Flipper Zero Firmware Update](https://flipperzero.one/update). Improvements for your dolphin: latest firmware releases, upgrade tools for PC and mobile devices.
- [User Documentation](https://docs.flipper.net). Learn more about your dolphin: specs, usage guides, and anything you want to ask.
- [Developer Documentation](https://developer.flipper.net/flipperzero/doxygen). Dive into the Flipper Zero Firmware source code: build system, firmware structure, and more.

# Contributing

Our main goal is to build a healthy and sustainable community around Flipper, so we're open to any new ideas and contributions. We also have some rules and taboos here, so please read this page and our [Code of Conduct](/CODE_OF_CONDUCT.md) carefully.

## I need help

The best place to search for answers is our [User Documentation](https://docs.flipper.net). If you can't find the answer there, check our [Discord Server](https://flipp.dev/discord) or our [Forum](https://forum.flipperzero.one/). If you want to contribute to the firmware development or modify it for your own needs, you can also check our [Developer Documentation](https://developer.flipper.net/flipperzero/doxygen).

## I want to report an issue

If you've found an issue and want to report it, please check our [Issues](https://github.com/flipperdevices/flipperzero-firmware/issues) page. Make sure the description contains information about the firmware version you're using, your platform, and a clear explanation of the steps to reproduce the issue.

## I want to contribute code

Before opening a PR, please confirm that your changes must be contained in the firmware. Many ideas can easily be implemented as external applications and published in the [Flipper Application Catalog](https://github.com/flipperdevices/flipper-application-catalog). If you are unsure, reach out to us on the [Discord Server](https://flipp.dev/discord) or the [Issues](https://github.com/flipperdevices/flipperzero-firmware/issues) page, and we'll help you find the right place for your code.

Also, please read our [Contribution Guide](/CONTRIBUTING.md) and our [Coding Style](/CODING_STYLE.md), and make sure your code is compatible with our [Project License](/LICENSE).

Finally, open a [Pull Request](https://github.com/flipperdevices/flipperzero-firmware/pulls) and make sure that CI/CD statuses are all green.

# Development

Flipper Zero Firmware is written in C, with some bits and pieces written in C++ and armv7m assembly languages. An intermediate level of C knowledge is recommended for comfortable programming. C, C++, and armv7m assembly languages are supported for Flipper applications.

# Firmware RoadMap

[Firmware RoadMap Miro Board](https://miro.com/app/board/uXjVO_3D6xU=/)

## Requirements

Supported development platforms:

- Windows 10+ with PowerShell and Git (x86_64)
- macOS 12+ with Command Line tools (x86_64, arm64)
- Ubuntu 20.04+ with build-essential and Git (x86_64)

Supported in-circuit debuggers (optional but highly recommended):

- [Flipper Zero Wi-Fi Development Board](https://shop.flipperzero.one/products/wifi-devboard)
- CMSIS-DAP compatible: Raspberry Pi Debug Probe and etc...
- ST-Link (v2, v3, v3mods)
- J-Link

Flipper Build System will take care of all the other dependencies.

## Cloning source code

Make sure you have enough space and clone the source code:

```shell
git clone --recursive https://github.com/flipperdevices/flipperzero-firmware.git
```

## Building

Build firmware using Flipper Build Tool:

```shell
./fbt
```

## Flashing firmware using an in-circuit debugger

Connect your in-circuit debugger to your Flipper and flash firmware using Flipper Build Tool:

```shell
./fbt flash
```

## Flashing firmware using USB

Make sure your Flipper is on, and your firmware is functioning. Connect your Flipper with a USB cable and flash firmware using Flipper Build Tool:

```shell
./fbt flash_usb
```

## Documentation

- [Flipper Build Tool](/documentation/fbt.md) - building, flashing, and debugging Flipper software
- [Applications](/documentation/AppsOnSDCard.md), [Application Manifest](/documentation/AppManifests.md) - developing, building, deploying, and debugging Flipper applications
- [Hardware combos and Un-bricking](/documentation/KeyCombo.md) - recovering your Flipper from the most nasty situations
- [Flipper File Formats](/documentation/file_formats) - everything about how Flipper stores your data and how you can work with it
- [Universal Remotes](/documentation/UniversalRemotes.md) - contributing your infrared remote to the universal remote database
- [Firmware Roadmap](https://miro.com/app/board/uXjVO_3D6xU=/)
- And much more in the [Developer Documentation](https://developer.flipper.net/flipperzero/doxygen)

# Project structure

- `applications`        - Applications and services used in firmware
- `applications_users`  - Place for your additional applications and services
- `assets`              - Assets used by applications and services
- `documentation`       - Documentation generation system configs and input files
- `furi`                - Furi Core: OS-level primitives and helpers
- `lib`                 - Our and 3rd party libraries, drivers, tools and etc...
- `site_scons`          - Build system configuration and modules
- `scripts`             - Supplementary scripts and various python libraries
- `targets`             - Firmware targets: platform specific code

Also, see `ReadMe.md` files inside those directories for further details.

# Links

- Discord: [flipp.dev/discord](https://flipp.dev/discord)
- Website: [flipperzero.one](https://flipperzero.one)
- Forum: [forum.flipperzero.one](https://forum.flipperzero.one/)
- Kickstarter: [kickstarter.com](https://www.kickstarter.com/projects/flipper-devices/flipper-zero-tamagochi-for-hackers)

## SAST Tools

- [PVS-Studio](https://pvs-studio.com/pvs-studio/?utm_source=website&utm_medium=github&utm_campaign=open_source) - static analyzer for C, C++, C#, and Java code.
