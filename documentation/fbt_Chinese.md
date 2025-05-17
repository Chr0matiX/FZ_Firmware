# 配置变量：

- VERBOSE：打印完整命令（是|否）
    - 默认：False
    - 实际：False

- FORCE：强制执行目标动作（支持的目标）（是|否）
    - 默认：False
    - 实际：False

- DEBUG：启用调试构建（是|否）
    - 默认：True
    - 实际：True

- LIB_DEBUG：启用库调试构建（是|否）
    - 默认：False
    - 实际：False

- COMPACT：优化大小（是|否）
    - 默认：False
    - 实际：False

- TARGET_HW：硬件目标（7|18）
    - 默认：7
    - 实际：7

- DIST_SUFFIX：构建输出中二进制文件后缀
    - 默认：local
    - 实际：local

- UPDATE_VERSION_STRING：更新包版本字符串
    - 默认：local
    - 实际：local

- COPRO_CUBE_VERSION：`Cube`版本
    - 默认：
    - 实际：1.20.0

- COPRO_STACK_ADDR：`Core2`固件地址
    - 默认：0
    - 实际：0x0

- COPRO_STACK_BIN：`Core2`固件文件名
    - 默认：
    - 实际：stm32wb5x_BLE_Stack_light_fw.bin

- COPRO_DISCLAIMER：传递给打包脚本以确认危险操作的值
    - 默认：
    - 实际：

- COPRO_OB_DATA：`OB`参考数据路径（/path/to/COPRO_OB_DATA）
    - 默认：
    - 实际：scripts/ob.data

- COPRO_STACK_BIN_DIR：`ST`提供的栈路径（/path/to/COPRO_STACK_BIN_DIR）
    - 默认：
    - 实际：lib/stm32wb_copro/firmware

- COPRO_CUBE_DIR：`Cube`根路径（/path/to/COPRO_CUBE_DIR）
    - 默认：
    - 实际：lib/stm32wb_copro

- COPRO_STACK_TYPE：`Core2`栈类型（`ble_full`|`ble_light`|`ble_basic`）
    - 默认：ble_light
    - 实际：ble_light

- SVD_FILE：`SVD`文件路径（/path/to/SVD_FILE）
    - 默认：
    - 实际：/STM32WB55_CM4.svd

- OTHER_ELF：用于调试的预构建`ELF`文件路径（/path/to/OTHER_ELF）
    - 默认：
    - 实际：

- FBT_TOOLCHAIN_VERSIONS：白名单工具链版本（留空不检查）
    - 默认：[]
    - 实际：12.3. 13.2.

- OPENOCD_OPTS：传递给`OpenOCD`的选项
    - 默认：
    - 实际：-f interface/stlink.cfg -c transport select hla_swd -f /stm32wbx.cfg -c stm32wbx.cpu configure -rtos auto

- BLACKMAGIC：`Blackmagic`探针位置
    - 默认：auto
    - 实际：auto

- SWD_TRANSPORT：`SWD`接口适配器类型（auto|cmsis-dap|stlink|blackmagic_usb|blackmagic_wifi）
    - 默认：auto
    - 实际：auto

- SWD_TRANSPORT_SERIAL：`SWD`接口适配器序列号
    - 默认：auto
    - 实际：auto

- UPDATE_SPLASH：安装更新包后渲染的幻灯片框架目录名
    - 默认：update_default
    - 实际：update_default

- LOADER_AUTOSTART：`Flipper`启动时自动运行的应用程序名
    - 默认：
    - 实际：

- FIRMWARE_APPS：配置名到应用程序列表的映射
    - 默认：
        ```json
        {
            'default': (
                'basic_services', 
                'main_apps', 
                'system_apps', 
                'settings_apps'
            )
        }
        ```
    - 实际：
        ```json
        {
            'default': [
                'basic_services', 
                'main_apps', 
                'system_apps', 
                'settings_apps'
            ], 
            'unit_tests': [
                'basic_services', 
                'updater_app', 
                'radio_device_cc1101_ext', 
                'unit_tests', 
                'js_app', 
                'archive'
            ]
        }
        ```

- FIRMWARE_APP_SET：使用的应用程序集，来自`FIRMWARE_APPS`
    - 默认：default
    - 实际：default

- APPSRC：要构建和上传的应用程序源目录
    - 默认：
    - 实际：

- APPDIRS：搜索固件组件和外部应用程序的目录
    - 默认：
        ```json
        [
            ('applications',            False), 
            ('applications/services',   True), 
            ('applications/main',       True), 
            ('applications/settings',   False), 
            ('applications/system',     False), 
            ('applications/debug',      False), 
            ('applications/examples',   False), 
            ('applications/drivers',    False), 
            ('applications_user',       False)
        ]
        ```
    - 实际：
        ```
        applications            False 
        applications/services   True 
        applications/main       True 
        applications/settings   False 
        applications/system     False 
        applications/debug      False 
        applications/examples   False 
        applications/drivers    False 
        applications_user       False
        ```

- PVSNOBROWSER：生成错误报告后不打开浏览器（是|否）
    - 默认：False
    - 实际：False

- FIRMWARE_ORIGIN：固件来源。如果遵循上游API结构为`'Official'`，否则为分支名称。此设置还将创建一个C定义`FW_ORIGIN_<origin>`，以便应用程序检查构建版本。
    - 默认：Official
    - 实际：Official

- FLIP_PORT：当多个`Flipper`连接时，使用的Flipper完整端口名
    - 默认：auto
    - 实际：auto

- LANG_SERVER：用于`vscode_dist`的语言服务器类型（cpptools|clangd）
    - 默认：clangd
    - 实际：clangd

- STRICT_FAP_IMPORT_CHECK：启用`.faps`的严格导入检查（是|否）
    - 默认：True
    - 实际：True

- ARGS：传递给支持的某些脚本的额外参数
    - 默认：
    - 实际：

# 任务：
## 固件与应用程序：
- firmware_all, fw_dist：
    构建固件；创建分发包
- faps, fap_dist：
    构建所有`FAP`应用程序
- fap_{APPID}, build APPSRC={APPID}; launch APPSRC={APPID}：
    构建`appid={APPID}`的`FAP`应用程序；通过`USB`上传并启动
- fap_deploy：
    构建并通过`USB`上传所有`FAP`应用程序

## 烧录与调试：
- flash, jflash：
    使用`SWD`探针将固件烧录到目标。另见`SWD_TRANSPORT`, `SWD_TRANSPORT_SERIAL`
- flash_usb, flash_usb_full：
    使用自更新包安装固件
- debug, debug_other, blackmagic：
    启动`GDB`

## 其他：
- cli：
    通过`USB`打开`Flipper CLI`会话
- firmware_cdb, updater_cdb：
    生成`compilation_database.json`
- lint, lint_py：
    运行代码检查工具
- format, format_py：
    运行代码格式化工具
- firmware_pvs：
    生成`PVS-Studio`报告

- 如何打开带有工具链环境和其他构建工具的shell：
    在shell中输入`source ./fbt -s env`。也可以使用`.`代替`source`。

- 使用`scons -H`查看SCons内置命令行选项帮助。

























# Flipper 构建工具 {#fbt}

FBT 是固件相关命令和工具的入口点。
通过在固件项目根目录下运行 `./fbt` 调用。它内部是对 [scons](https://scons.org/) 构建系统的封装。

如果不需要 `fbt` 的全部功能（如构建整个固件），只想构建和调试单个应用程序，可使用 [ufbt](https://pypi.org/project/ufbt/)。

## 环境

使用 `fbt` 仅需系统中安装 `git`。

`fbt` 默认下载并解压预构建的工具链，然后修改环境变量以供自身使用，不会污染系统的全局路径。
> 如果想在 `fbt` 外使用工具链提供的工具，可打开 *fbt shell*，配置好环境：
>    - Windows：运行 `scripts/toolchain/fbtenv.cmd`。
>    - Linux & MacOS：在新 shell 中运行 `source scripts/toolchain/fbtenv.sh`。
>    - 也可以在 shell 中输入 ```. `./fbt -s env` ```（保留开头的“.”）。

如果系统不支持预构建工具链或想使用自定义依赖版本，可设置 `FBT_NOENV=1`。`fbt` 将跳过工具链和环境配置，期望所有工具在系统 `PATH` 中可用。（此选项在 Windows 上不可用）

如果设置了 `FBT_TOOLCHAIN_PATH` 变量，`fbt` 将使用该目录解压工具链。默认情况下，工具链下载到仓库根目录的 `toolchain` 子目录。

若需启用 `fbt` 和工具链管理脚本的额外调试输出，可设置 `FBT_VERBOSE=1`。

`fbt` 启动时始终执行 `git submodule update --init`，除非在环境中设置 `FBT_NO_SYNC=1`：
  - Windows：在运行 `fbt` 的 shell 中执行 `set "FBT_NO_SYNC=1"`。
  - *nix：执行 `$ FBT_NO_SYNC=1 ./fbt ...`。

> 更多控制 `fbt` 基础行为的变量，请参阅 `fbt` 和 `fbtenv` 脚本源代码。

## 调用 FBT

使用 FBT 构建时，调用它并指定配置选项和构建目标。例如：

`./fbt COMPACT=1 DEBUG=0 VERBOSE=1 updater_package copro_dist`

要清理指定目标（类似 `make clean`），添加 `-c` 选项。

## 构建目录

`fbt` 在 `build` 目录的子目录中分别构建更新器和固件，目录名取决于优化设置（`COMPACT` 和 `DEBUG` 选项）。为方便与 IDE 集成，最新构建的变体目录始终链接为 `built/latest`。此外，该文件夹中会生成 `compile_commands.json`（用于 IDE 代码补全支持）。

`build/latest` 符号链接和编译数据库仅在 *固件构建目标* 时更新，即重新构建固件本身时。运行其他任务（如固件烧录或为不同调试/发布配置或硬件目标构建更新包）不会更新 `built/latest` 指向的目录。

## VSCode 集成

`fbt` 提供 VS Code 的基本开发环境配置。运行 `./fbt vscode_dist` 部署，将初始环境配置复制到 `.vscode` 文件夹。之后，启动 VS Code 并在“文件 > 打开文件夹”菜单中选择固件根文件夹即可使用该配置。

若需使用非默认的 VS Code C/C++ 语言服务器，运行 `./fbt vscode_dist LANG_SERVER=<language Characteristics>server>`。目前 `fbt` 支持默认语言服务器（`cpptools`）和 `clangd`。

- 首次启动时，会提示安装推荐插件。强烈建议安装以获得最佳开发体验。插件列表见 `.vscode/extensions.json`。
- 基本构建任务在 Ctrl+Shift+B 菜单中调用。
- 调试需要支持的探针，包括：
  - 带原厂固件的 Wi-Fi 开发板（blackmagic）。
  - ST-Link 及兼容设备。
  - J-Link 用于烧录和调试（仅限 VSCode）。_注意：J-Link 工具未包含在工具链中，需自行从 [下载](https://www.segger.com/downloads/jlink/) 并放入系统 PATH。_
- 无支持探针时，可通过 USB 安装方式在 Flipper 上安装固件。

## FBT 目标

`fbt` 跟踪内部依赖，只需构建所需最高级别目标，`fbt` 会确保其依赖项是最新的。

### 高级目标（最常用）

- `fw_dist` — 构建并发布固件到 `dist` 文件夹，无其他目标时为默认目标。
- `fap_dist` — 构建外部插件并发布到 `dist` 文件夹。
- `updater_package`, `updater_minpackage` — 构建自更新包。最小版本仅包含固件的 DFU 文件；完整版本还包括无线电栈和 SD 卡资源。
- `copro_dist` — 为 qFlipper 打包 Core2 FUS+栈二进制文件。
- `flash` — 通过 SWD 接口使用支持的探针烧录到连接设备。探针自动检测，可通过 `SWD_TRANSPORT=...` 变量覆盖。若连接多个探针，可用 `SWD_TRANSPORT_SERIAL=...` 指定探针序列号。
- `flash_usb`, `flash_usb_full` — 通过 USB 构建、上传和安装更新包。详情见 `updater_package` 和 `updater_minpackage`。
- `debug` — 构建并烧录固件，然后使用 gdb 附加，加载固件的 .elf 文件。
- `debug_other`, `debug_other_blackmagic` — 附加 GDB 但不加载任何 `.elf` 文件，允许在 GDB 中用 `add-symbol-file` 手动添加外部 `.elf` 文件。
- `updater_debug` — 附加 GDB 并加载更新器的 `.elf` 文件。
- `devboard_flash` — 更新 WiFi 开发板。支持 `ARGS="..."` 传递额外参数到更新脚本，例如 `ARGS="-c dev"`。
- `blackmagic` — 使用 Blackmagic 探针（WiFi 开发板）调试固件。
- `openocd` — 仅启动 OpenOCD。可用 `ARGS="..."` 传递额外参数。
- `get_blackmagic` — 以 GDB 远程格式输出 blackmagic 地址，便于 IDE 集成。
- `get_stlink` — 输出连接的 STLink 探针序列号，用于通过 `SWD_TRANSPORT_SERIAL=...` 指定适配器。
- `lint`, `format` — 对 C 源代码运行 clang-format，检查并根据 `.clang-format` 规范重新格式化。支持 `ARGS="..."` 传递额外参数给 clang-format。
- `lint_py`, `format_py` — 对 Python 源代码、构建系统文件和应用清单运行 [black](https://black.readthedocs.io/en/stable/index.html)。支持 `ARGS="..."` 传递额外参数给 black。
- `lint_img`, `format_img` — 检查图像资源错误并格式化，强制执行颜色深度并去除元数据。
- `lint_all`, `format_all` — 运行所有检查和格式化工具。
- `firmware_pvs` — 为固件生成 PVS Studio 报告，需 PVS Studio 在系统 `PATH` 中可用。
- `doxygen` — 为固件生成 Doxygen 文档。`doxy` 目标还会打开浏览器查看生成文档。
- `cli` — 通过 USB 启动 Flipper CLI 会话。

### 固件目标

- `faps` — 构建所有外部和插件应用为 [`.faps`](AppsOnSDCard.md)。
- `fbt` 还为每个应用定义目标。例如，应用 `appid=snake_game` 的目标名为：
  - `fap_snake_game` 等 — 按应用 ID 构建单个应用为 `.fap`。
  - 查看 [--extra-ext-apps](#command-line-parameters) 以强制添加额外应用到外部构建。
  - `fap_snake_game_list` 等 — 为应用的 `.fap` 生成源代码和汇编列表。
- `flash`, `firmware_flash` — 通过 SWD 将当前版本烧录到连接设备。
- `jflash` — 使用 J-Link 探针通过 JFlash 将当前版本烧录到连接设备。JFlash 可执行文件必须在 `$PATH` 中。
- `firmware_all`, `updater_all` — 构建基本二进制文件集。
- `firmware_list`, `updater_list` — 生成源代码和汇编列表。
- `firmware_cdb`, `updater_cdb` — 为外部工具和 IDE 生成 `compilation_database.json` 文件，可在不实际构建固件的情况下创建。

### 资源

- `resources` — 构建资源及其清单文件
  - `dolphin_ext` — 处理 SD 卡的海豚动画
- `icons` — 从 PNG 资源生成 `.c+.h` 文件
- `proto` — 为 `.proto` 源文件生成 `.pb.c+.pb.h` 文件
- `proto_ver` — 生成包含 protobuf 版本的 `.h` 文件
- `dolphin_internal`, `dolphin_blocking` — 为对应的海豚资源生成 `.c+.h` 文件

## 命令行参数 {#command-line-parameters}

- `--options optionfile.py`（默认值 `fbt_options.py`）— 加载包含多个配置值的文件
- `--extra-int-apps=app1,app2,appN` — 强制指定应用随 `firmware` 目标构建为内部应用
- `--extra-ext-apps=app1,app2,appN` — 强制指定应用随 `firmware_extapps` 目标构建为外部应用
- `--extra-define=A --extra-define=B=C` — 传递给 C/C++ 编译器的额外全局定义，可多次指定
- `--proxy-env=VAR1,VAR2` — 暴露给 `fbt` 启动的子进程的额外环境变量。默认情况下，`fbt` 会清理执行环境，不转发所有继承的环境变量。可在 `environ.scons` 文件中查看始终转发的变量列表。

## 配置

默认配置变量在配置文件 `fbt_options.py` 中设置。
命令行中设置的值优先级高于配置文件。

可创建 `fbt_options_local.py` 文件，在加载默认选项文件时评估，允许在不修改默认配置的情况下持久覆盖默认选项。

运行 `./fbt -h` 可查看可用选项。

### 固件应用集

通过修改包含在构建中的应用列表，可创建自定义固件构建。应用预设通过 `FIRMWARE_APPS` 选项配置，格式为 `map(configuration_name:str → application_list:tuple(str))`。要指定构建中使用的应用集，将 `FIRMWARE_APP_SET` 设置为对应的名称。
例如，要构建包含单元测试的固件镜像，运行 `./fbt FIRMWARE_APP_SET=unit_tests`。

详情请查看 `fbt_options.py`。