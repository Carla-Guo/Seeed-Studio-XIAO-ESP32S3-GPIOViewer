# XIAO ESP32-S3 GPIO Viewer

[English](README.md) | [简体中文](README_CN.md)

The **XIAO ESP32-S3 (Sense) GPIO Viewer** is a lightweight, MicroPython-based tool that turns your XIAO board into a real-time GPIO monitoring dashboard accessible directly from a web browser.

It is designed to help developers quickly visualize GPIO states, ADC values, and system information during prototyping, debugging, and education—without the need for additional software or cloud services.

---

## 🚀 Overview

Once deployed, the XIAO ESP32-S3 runs a local web server that provides a live hardware status page over Wi-Fi. Any device on the same network (PC, tablet, or phone) can access the dashboard via a browser.

---

## 📊 Information Displayed

The web interface provides real-time visibility into:

### GPIO & I/O

* Digital GPIO status (HIGH / LOW)
* ADC readings
* Clear GPIO pin mapping for XIAO ESP32-S3

### Runtime & System

* CPU frequency
* System uptime
* Chip model and core count
* MicroPython firmware version

### Memory & Storage

* Heap memory usage
* Flash size
* File system usage
* PSRAM availability (if present)

### Network

* IP address
* Connected Wi-Fi SSID
* Signal strength (RSSI)
* MAC address
* Gateway and DNS information

---

## ✨ Key Features

* 📡 **Real-time GPIO & ADC monitoring** via a browser
* 🌐 **Built-in web server** running directly on the XIAO
* 🔌 **No external software required** after deployment
* 📱 **Multi-device access** from the same local network
* 🧪 Ideal for **sensor testing, relay debugging, and rapid prototyping**
* 🐍 Fully implemented in **MicroPython**, easy to understand and extend

---

## 🛠 Getting Started

### 1. Prepare Your Computer

Install **Thonny IDE**, which will be used to upload MicroPython code:

1. Go to: [https://thonny.org](https://thonny.org)
2. Download the installer for your operating system
3. Complete the installation

---

### 2. Install Required Python Tool (esptool)

`esptool` is required to flash MicroPython firmware:

```bash
pip install esptool
```

---

### 3. Download MicroPython Firmware

1. Visit: [https://micropython.org/download/ESP32_GENERIC_S3/](https://micropython.org/download/ESP32_GENERIC_S3/)
2. Download the latest `.bin` firmware file
   (e.g. `ESP32_GENERIC_S3-xxxx.bin`)
3. Save it to a known location (Desktop recommended)

---

### 4. Connect the XIAO ESP32-S3 (Sense)

1. Connect the board to your computer using a USB-C cable
2. If the board is not detected, press and hold the **BOOT** button while plugging it in
3. Note the assigned serial port:

   * Windows: `COMx`
   * macOS/Linux: `/dev/ttyUSBx` or `/dev/ttyACMx`

---

### 5. Flash MicroPython Firmware

**Erase existing firmware:**

```bash
esptool --chip esp32s3 --port COMx erase-flash
```

**Flash MicroPython:**

```bash
esptool.py --chip esp32s3 --port COMx write_flash -z 0x0 ESP32_GENERIC_S3-xxxx.bin
```

> Replace `COMx` and the firmware filename with your actual values.

---

### 6. Configure Thonny

1. Unplug and reconnect the XIAO board
2. Open Thonny
3. Go to **Run → Configure Interpreter**
4. Select **MicroPython (ESP32)**
5. Choose the correct serial port and click **OK**

Test the connection:

```python
print("Hello from XIAO!")
```

---

### 7. Download the GPIO Viewer Project

1. Click **Code → Download ZIP**
2. Extract the ZIP file locally

---

### 8. Upload Project Files to the Board

In Thonny:

1. Open **View → Files**
2. Locate the extracted project folder
3. Upload the following files to the device root (`/`):

   * `boot.py`
   * `main.py`

These files will run automatically on boot.

---

### 9. Configure Wi-Fi Credentials

Edit `boot.py` and update your Wi-Fi details:

```python
ssid = "Your_WiFi_SSID"
password = "Your_WiFi_Password"
```

Save the file after editing.

---

### 10. Run and Access the Web Dashboard

1. Click **Run** (▶) in Thonny or reset the board
2. Wait for the XIAO to connect to Wi-Fi
3. Check the Thonny console for the assigned IP address
4. Open a browser and navigate to:

```
http://<XIAO_IP_ADDRESS>:8080
```

You should now see the live GPIO Viewer dashboard.

---

## 🧑‍💻 Reference

The project is a fork of https://github.com/TuzaaBap/Seeed-Studio-XIAO-ESP32S3-GPIOViewer.

