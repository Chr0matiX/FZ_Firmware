# 开发板固件更新 {#dev_board_fw_update}

定期更新 Wi-Fi 开发板固件以获取最新功能和修复 bug。本页将指导你完成更新开发板固件的步骤。

> **注意**：本指南假设你熟悉命令行基础。如不熟悉，建议查看 [Windows](https://learn.microsoft.com/en-us/powershell/scripting/learn/ps101/01-getting-started?view=powershell-7.4) 或 [macOS/Linux](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview) 命令行教程。

***

## 步骤 1：安装 micro Flipper Build Tool

[micro Flipper Build Tool (uFBT)](https://pypi.org/project/ufbt/) 是一个跨平台工具，支持 Flipper Zero 的开发任务，如构建、调试、刷写固件及生成 VS Code 配置。

**Linux & macOS：**

在终端运行：
```bash
python3 -m pip install --upgrade ufbt
```

**Windows：**

1. 下载最新版 Python。
2. 在 PowerShell 运行：
   ```bash
   py -m pip install --upgrade ufbt
   ```

***

## 步骤 2：连接开发板到电脑

更新固件需将开发板切换至 Bootloader 模式，通过 USB-C 线连接电脑，并确保电脑识别开发板：

1. 列出电脑的串口设备：
   - **macOS**：运行 `ls /dev/cu.*`。
   - **Linux**：运行 `ls /dev/tty*`。
   - **Windows**：打开 **设备管理器**，展开 **端口 (COM & LPT)**。
2. 使用 USB-C 线连接开发板到电脑。
   ![有线连接](https://cdn.flipperzero.one/Flipper_Zero_Wi-Fi_devboard_update_wired_connection.jpg)
3. 切换开发板至 Bootloader 模式：
   1. 按住 **BOOT** 按钮。
   2. 按下 **RESET** 按钮，同时保持 **BOOT** 按住。
   3. 松开 **BOOT** 按钮。
   ![切换到 Bootloader](https://cdn.flipperzero.one/Flipper_Zero_Wi-Fi_devboard_reboot_to_bootloader.png)
4. 重复步骤 1，查看开发板在设备列表中的名称。

***

## 步骤 3：刷写固件

**Linux & macOS：**
```bash
python3 -m ufbt devboard_flash
```

**Windows：** 在 PowerShell 运行：
```bash
py -m ufbt devboard_flash
```

成功后会显示：`WiFi board flashed successfully`。

### 如果刷写失败

可能遇到错误，如：
```
A fatal error occurred: Serial data stream stopped: Possible serial noise or corruption.
```
或
```
FileNotFoundError: [Errno 2] No such file or directory: '/dev/cu.usbmodem01'
```

**解决方法**：
- 断开并重新连接开发板，重新切换至 Bootloader 模式。
- 更换电脑的 USB 端口。
- 更换 USB-C 线。

***

## 步骤 4：完成安装

1. 按 **RESET** 按钮重启开发板。
   ![刷写后重启](https://cdn.flipperzero.one/Flipper_Zero_Wi-Fi_devboard_reboot_after_flashing.jpg)
2. 断开并重新连接 USB-C 线。

开发板固件更新完成！

若已完成 **开发板入门指南**，可继续 [步骤 3：将开发板插入 Flipper Zero](#dev_board_get_started_step-3)。