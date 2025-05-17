# 通过 Wi-Fi 开发板调试 {#dev_board_debugging_guide}

本页介绍如何使用 Wi-Fi 开发板调试 Flipper Zero 固件。我们将以 VS Code 和 Flipper Build Tool（FBT）为例，展示调试流程。

***

## 概述

Wi-Fi 开发板作为调试探针，连接主机 IDE（运行调试器）与 Flipper Zero 的目标微控制器（STM32WB55）。用户通过 [Wi-Fi](#dev_board_wifi_connection) 或 [USB](#dev_board_usb_connection) 控制调试。

![Wi-Fi Developer Board](https://cdn.flipperzero.one/Flipper_Zero_WiFi_hardware_CDN.jpg)

数据通过 Serial Wire Debug（SWD）接口传输，使用以下 GPIO 引脚：
- **Pin 10**：SWCLK（串行时钟）
- **Pin 12**：SWDIO（串行数据 I/O）

了解更多 Flipper Zero 引脚信息，请访问 [GPIO & modules](https://docs.flipper.net/gpio-and-modules)。

***

## 前提条件

### 步骤 1：安装 Git
需安装 Git 以克隆固件仓库。参考 [Git 安装指南](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)。

### 步骤 2：构建固件
调试前需克隆并构建 Flipper Zero 固件：
1. 打开 **终端**（Linux/macOS）或 **PowerShell**（Windows）。
2. 克隆仓库：
   ```bash
   git clone --recursive https://github.com/flipperdevices/flipperzero-firmware.git
   cd flipperzero-firmware
   ```
3. 使用 FBT 构建固件：
   ```bash
   ./fbt
   ```

***

## 调试固件

在 `flipperzero-firmware` 目录下运行：
```bash
./fbt flash
```
通过开发板将固件刷入 Flipper Zero，然后开始调试。推荐使用 VS Code 配合推荐扩展。

在 **VS Code** 中调试：
1. 打开 `flipperzero-firmware` 目录。
2. 安装推荐扩展（搜索 `@recommended` 或根据通知安装）。
3. 运行 `./fbt vscode_dist` 生成调试配置文件。
4. 打开 **Run and Debug** 面板，选择调试器：
   - **Attach FW (blackmagic)**：支持 Wi-Fi 或 USB。
   - **Attach FW (DAP)**：仅支持 USB。
   > **注意**：通过 USB 调试时，需确保开发板的 USB 模式与所选调试器匹配。查看或更改模式，请参考 [开发板调试模式](#dev_board_debug_modes)。
5. 如需刷机，运行 `./fbt flash`，然后点击 **Start Debugging** 按钮开始调试。
6. 调试会暂停固件执行，点击顶部工具栏的 **Continue** 按钮继续运行。

![VS Code Debugging](https://cdn.flipperzero.one/Flipper_Zero_Wi-Fi_devboard_VS_Code.jpg)

> **注意**：
> - 更改开发板调试模式，请参考 [开发板调试模式](#dev_board_debug_modes)。
> - 查看开发板日志，请参考 [通过开发板读取日志](#dev_board_reading_logs)。
> - 了解 VS Code 调试，参考 [VS Code 调试指南](https://code.visualstudio.com/docs/editor/debugging)。