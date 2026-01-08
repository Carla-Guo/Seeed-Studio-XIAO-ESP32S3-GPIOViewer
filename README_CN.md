# XIAO ESP32-S3 (Sense) GPIO Viewer

[English](README.md) | [简体中文](README_CN.md)

**XIAO ESP32-S3 (Sense) GPIO Viewer** 是一个基于 **MicroPython** 的实时 GPIO 监控工具，可在浏览器中通过本地 Web 界面显示 XIAO 板的 GPIO 状态（HIGH/LOW/TOUCH）。 

---

## 📌 Information Displayed on the Web Page

实时网页界面显示以下信息：

* **GPIO & I/O Monitoring:** 实时显示数字 GPIO 状态、ADC 读数以及清晰的 GPIO 引脚映射。
* **Runtime Information:** 当前 CPU 频率与系统运行时间。
* **Memory & Storage:** 堆内存使用情况、文件系统使用百分比、闪存大小与 PSRAM 可用性。
* **Network Information:** 网络诊断信息（IP 地址、Wi-Fi SSID、RSSI、MAC、网关与 DNS）。
* **Firmware & System:** 芯片型号、CPU 核心数、MicroPython 版本与固件信息。 

---

## ⭐ Features

该项目具有以下亮点：

* 在浏览器中显示实时 GPIO 数字状态与 ADC 读数。
* 作为嵌入式 Web 服务器运行于 XIAO，部署后无需额外软件或云服务。
* 同一局域网内任意设备可访问实时监控界面。
* 有助于快速验证传感器、继电器、外围模块等硬件状态。
* 基于 MicroPython 构建，便于阅读与快速迭代。

---

## 🛠 Build Process

这是一个适合初学者的完整工作流程，从准备开发环境到在 XIAO 板上运行 GPIO Viewer。 

---

### 1. Prepare Your Computer

在连板之前，需要安装 Thonny IDE：

1. 打开浏览器（Chrome / Safari 等）。
2. 访问 [https://thonny.org](https://thonny.org) 并下载对应系统的安装程序。
3. 按提示安装 Thonny。

> Thonny 是你用于编写并上传 Python 代码到 XIAO 的 IDE。 

---

### 2. Install Python Tools Needed (Esptool)

要烧写 MicroPython 固件，需要安装 `esptool`：

```bash
pip install esptool
```

这将允许你将 MicroPython 固件写入 XIAO 板。 

---

### 3. Download the MicroPython Firmware

1. 访问：[https://micropython.org/download/ESP32_GENERIC_S3/](https://micropython.org/download/ESP32_GENERIC_S3/)
2. 下载最新的 `.bin` 固件文件（如 `ESP32_GENERIC_S3-xxxxx.bin`）。
3. 保存到桌面或方便的位置。 

---

### 4. Connect Your XIAO ESP32-S3 (Sense) to Your Computer

1. 使用 USB-C 数据线连接 XIAO 到电脑。
2. 若板子未显示，可在插入同时按住 **BOOT** 按钮。
3. 电脑将为 XIAO 分配一个端口（Windows 上如 `COMX`，Mac/Linux 上如 `/dev/ttyUSB0`). 

---

### 5. Flash (Install) MicroPython onto the Board

**清除旧固件：**

```bash
esptool --chip esp32s3 --port COMX erase-flash
```

> 替换 `COMX` 为实际端口名称。 

**写入 MicroPython 固件：**

```bash
cd Desktop
esptool.py --chip esp32s3 --port COMX write_flash -z 0x0 ESP32_GENERIC_S3-xxxx.bin
```

确保 `.bin` 文件名与下载文件匹配。 

---

### 6. Open Thonny and Connect to the Board

1. 断开 XIAO，等待 5 秒后重新插入。
2. 在 Thonny 中打开：**Run → Configure Interpreter**。
3. 选择 **MicroPython (ESP32)**，并选中对应的端口。
4. 点击 **OK**，此时应能看到 MicroPython REPL 提示符。
5. 测试示例：

```python
print("Hello from XIAO!")
```

 

---

### 7. Download the GPIOViewer Project Files

1. 打开浏览器访问项目仓库：
   [https://github.com/TuzaaBap/Seeed-Studio-XIAO-ESP32S3-GPIOViewer/tree/main](https://github.com/TuzaaBap/Seeed-Studio-XIAO-ESP32S3-GPIOViewer/tree/main)
2. 点击 **Code → Download ZIP**。
3. 解压 ZIP 到本地文件夹。 

---

### 8. Upload the Project to Your Board

在 Thonny：

1. 打开 **Files** 侧边栏 (View → Files)。
2. 定位到解压的项目文件夹。
3. 右键点击 `boot.py` → **Upload to / (root)**。
4. 对 `main.py` 重复上传。 

上传后程序将设置为启动时运行。 

---

### 9. Configure Your Wi-Fi (inside `boot.py`)

编辑 `boot.py`：

```python
# 修改为你的 Wi-Fi SSID 和密码
ssid = "Your_WiFi_SSID"
password = "Your_WiFi_Password"
```

保存更改。 

---

### 10. Run and View the GPIO Monitor

1. 在 Thonny 中点击 **Run**（绿色 ▶ 按钮）。
2. 等待 XIAO 连接 Wi-Fi。
3. 在 Thonny 输出中查看分配的 IP 地址。
4. 在浏览器中打开该 IP（示例：`http://192.168.6.80:8080`）。
5. 你将看到实时 GPIO 状态板。 

> 提示：如果无法打开网页，可按 **Reset** 重启 XIAO 或关闭 Thonny。 

---

## ✨ Reference

该项目是 https://github.com/TuzaaBap/Seeed-Studio-XIAO-ESP32S3-GPIOViewer 的分支。

---


