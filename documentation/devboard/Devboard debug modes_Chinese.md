# 开发板调试模式 {#dev_board_debug_modes}

Flipper Zero 的 Wi-Fi 开发板支持 **Black Magic** 和 **DAPLink** 调试模式，可根据需要切换。支持的模式取决于连接方式：

- **Wi-Fi**：仅支持 **Black Magic** 模式。
- **USB**：可在 **Black Magic**（默认）与 **DAPLink** 之间切换。以下介绍 USB 连接的模式切换方法。

> **注意**：Black Magic 模式不支持 RTOS 线程，但可执行其他调试操作。

***

## USB 连接的调试模式切换

通过 USB 切换调试模式需无线操作。根据开发板的 Wi-Fi 配置（**Wi-Fi 接入点模式**或 **Wi-Fi 客户端模式**），步骤如下：

1. 若开发板未连接 Flipper Zero，关闭 Flipper Zero，连接开发板，然后重新开机。

2. 访问开发板的 Web 界面：
   - [Wi-Fi 接入点模式](#wifi-access-point)
   - [Wi-Fi 客户端模式](#wifi-client-mode)

3. 在 **WiFi** 选项卡中，点击 **USB mode**，选择 **BlackMagicProbe** 或 **DapLink**。

4. 点击 **SAVE**，然后点击 **REBOOT** 应用更改。

![切换调试模式](https://cdn.flipperzero.one/Flipper_Zero_WiFi_devboard_switching_modes_CDN.jpg)

> **注意**：切换开发板调试模式后，需在 VS Code 的 **Run and Debug** 面板中选择对应的调试器，并点击 ▷ **Start Debugging** 按钮。