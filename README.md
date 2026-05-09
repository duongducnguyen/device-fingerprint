# Device Fingerprint

> Android research tool that surfaces device identification signals.
> Package: `com.wowsoftware.devicefingerprint` · Version: **1.0.0**

**Languages / 语言 / Языки:** [English](#english) · [中文](#中文) · [Русский](#русский)

Latest signed APK: [`releases/device-fingerprint-v1.0.0.apk`](releases/device-fingerprint-v1.0.0.apk)

---

## English

### Overview

**Device Fingerprint** is an Android application built for security research and educational purposes. It collects and displays the wide range of identification signals an Android device exposes — hardware identifiers, network adapters, installed packages, input peripherals, advertising IDs, and emulator-detection markers — all in a single multi-tab interface.

The app is intentionally read-only with respect to your data: nothing is transmitted off-device except an optional IP-geolocation lookup (`ip-api.com`) that fires only when you open the **Location** tab.

### Features

Nine inspection tabs, each backed by a dedicated reader module:

| Tab | What it shows |
|---|---|
| **Dashboard** | Android ID, IMEI, device serial, MediaDRM ID, MAC address, build/system properties |
| **Applications** | Installed packages with filters (system / user / sideloaded) |
| **SIM** | Phone numbers, subscription info, carrier data |
| **WiFi** | Visible networks (SSID, BSSID, RSSI, channel) |
| **LAN** | Local subnet host scan |
| **Bluetooth** | Classic + BLE device discovery |
| **Location** | GPS fix and IP-based geolocation |
| **Input** | Keyboards, mice, touchpads, gamepads, sensors |
| **Accounts** | Accounts registered via `AccountManager` |

Additional capabilities:

- **Emulator detection** via a native C++ scanner (JNI) inspecting build/system properties for known emulator markers.
- **Google Advertising ID** (GAID), **AppSet ID**, and `Settings.Global.AD_AAID` exposure.
- **Root-aware permission grant** through [libsu](https://github.com/topjohnwu/libsu) — when the device is rooted, runtime permissions can be auto-granted to unblock research scenarios.

### Requirements

- Android **9.0** (API 28) or newer
- Architectures: `arm64-v8a`, `armeabi-v7a`, `x86_64`, `x86`
- Approx. 5 MB free storage

### Installation

1. Download [`releases/device-fingerprint-v1.0.0.apk`](releases/device-fingerprint-v1.0.0.apk).
2. On your Android device, enable **Install unknown apps** for the browser/file manager you used.
3. Open the APK and tap **Install**.
4. Grant the runtime permissions when prompted — the app will list which signals each permission unlocks.

### Permissions

The manifest declares 16 permissions covering phone state, network adapters, location, contacts, and advertising IDs:

- `READ_PHONE_STATE`, `READ_PHONE_NUMBERS`, `READ_PRIVILEGED_PHONE_STATE`
- `ACCESS_WIFI_STATE`, `CHANGE_WIFI_STATE`, `NEARBY_WIFI_DEVICES`
- `BLUETOOTH`, `BLUETOOTH_ADMIN` (≤ Android 11), `BLUETOOTH_SCAN`, `BLUETOOTH_CONNECT`
- `ACCESS_COARSE_LOCATION`, `ACCESS_FINE_LOCATION`
- `READ_CONTACTS`
- `com.google.android.gms.permission.AD_ID`
- `QUERY_ALL_PACKAGES`, `INTERNET`

Skipping a permission only disables the related tab; the rest of the app remains usable.

### Disclaimer

This tool is published for **research, education, and self-audit** only. It is not intended for surveilling other people's devices. The maintainer assumes no liability for misuse. Use it on hardware you own or are explicitly authorised to inspect.

---

## 中文

### 概述

**Device Fingerprint** 是一款面向安全研究与教学的 Android 应用，集中展示设备暴露的各类标识信号——硬件标识、网络适配器、已安装应用、输入外设、广告 ID 以及模拟器特征——全部呈现在一个多标签页界面中。

该应用对用户数据保持只读：除非用户打开 **Location** 标签触发 IP 定位查询（`ip-api.com`），否则不会向设备外发送任何数据。

### 功能

应用提供 9 个检测标签，每个标签对应一个独立的读取模块：

| 标签 | 显示内容 |
|---|---|
| **Dashboard** | Android ID、IMEI、设备序列号、MediaDRM ID、MAC 地址、构建/系统属性 |
| **Applications** | 已安装应用（系统应用 / 用户应用 / 旁加载应用筛选） |
| **SIM** | 电话号码、订阅信息、运营商数据 |
| **WiFi** | 可见网络（SSID、BSSID、RSSI、信道） |
| **LAN** | 局域网主机扫描 |
| **Bluetooth** | 经典蓝牙 + BLE 设备发现 |
| **Location** | GPS 定位与 IP 地理位置 |
| **Input** | 键盘、鼠标、触摸板、手柄、传感器 |
| **Accounts** | 通过 `AccountManager` 注册的账号 |

其他特性：

- **模拟器检测**：通过 JNI 调用 C++ 原生扫描器，检查构建/系统属性中已知的模拟器特征。
- **Google 广告 ID** (GAID)、**AppSet ID** 与 `Settings.Global.AD_AAID` 展示。
- **Root 感知的权限授予**：使用 [libsu](https://github.com/topjohnwu/libsu)。在已 root 的设备上，可自动授予运行时权限以加速研究流程。

### 系统要求

- Android **9.0**（API 28）或更高版本
- 支持架构：`arm64-v8a`、`armeabi-v7a`、`x86_64`、`x86`
- 约需 5 MB 存储空间

### 安装步骤

1. 下载 [`releases/device-fingerprint-v1.0.0.apk`](releases/device-fingerprint-v1.0.0.apk)。
2. 在 Android 设备上为所用的浏览器或文件管理器开启 **允许安装未知应用**。
3. 打开 APK，点击 **安装**。
4. 应用启动后按提示授予运行时权限——每个权限对应解锁的功能会有说明。

### 权限说明

清单文件共声明 16 项权限，覆盖电话状态、网络适配器、定位、联系人与广告 ID：

- `READ_PHONE_STATE`、`READ_PHONE_NUMBERS`、`READ_PRIVILEGED_PHONE_STATE`
- `ACCESS_WIFI_STATE`、`CHANGE_WIFI_STATE`、`NEARBY_WIFI_DEVICES`
- `BLUETOOTH`、`BLUETOOTH_ADMIN`（仅 Android 11 及以下）、`BLUETOOTH_SCAN`、`BLUETOOTH_CONNECT`
- `ACCESS_COARSE_LOCATION`、`ACCESS_FINE_LOCATION`
- `READ_CONTACTS`
- `com.google.android.gms.permission.AD_ID`
- `QUERY_ALL_PACKAGES`、`INTERNET`

拒绝某项权限只会禁用对应标签页，应用其余功能仍可正常使用。

### 免责声明

本工具仅用于 **研究、教学与自查**，不得用于监控他人设备。维护者不对滥用承担任何责任。请仅在您拥有或获得明确授权的设备上使用。

---

## Русский

### Обзор

**Device Fingerprint** — Android-приложение для исследований и обучения в области безопасности. Оно собирает и показывает широкий набор идентификационных сигналов устройства: аппаратные идентификаторы, сетевые адаптеры, установленные пакеты, устройства ввода, рекламные ID и маркеры обнаружения эмулятора — всё это в едином интерфейсе с несколькими вкладками.

Приложение работает с вашими данными только в режиме чтения: за пределы устройства ничего не отправляется, кроме опционального запроса IP-геолокации (`ip-api.com`), который выполняется только при открытии вкладки **Location**.

### Возможности

Девять диагностических вкладок, каждая опирается на отдельный модуль-считыватель:

| Вкладка | Что отображается |
|---|---|
| **Dashboard** | Android ID, IMEI, серийный номер, MediaDRM ID, MAC-адрес, свойства сборки/системы |
| **Applications** | Установленные пакеты (фильтры: системные / пользовательские / sideload) |
| **SIM** | Номера телефонов, информация о подписке, оператор |
| **WiFi** | Видимые сети (SSID, BSSID, RSSI, канал) |
| **LAN** | Сканирование хостов локальной подсети |
| **Bluetooth** | Обнаружение классических и BLE-устройств |
| **Location** | GPS-координаты и IP-геолокация |
| **Input** | Клавиатуры, мыши, тачпады, геймпады, сенсоры |
| **Accounts** | Аккаунты, зарегистрированные через `AccountManager` |

Дополнительные возможности:

- **Обнаружение эмулятора** через нативный C++ сканер (JNI), анализирующий свойства сборки/системы на известные маркеры эмуляторов.
- Отображение **Google Advertising ID** (GAID), **AppSet ID** и `Settings.Global.AD_AAID`.
- **Выдача разрешений с поддержкой root** через [libsu](https://github.com/topjohnwu/libsu): на устройствах с root-доступом runtime-разрешения могут автоматически предоставляться для ускорения исследований.

### Требования

- Android **9.0** (API 28) или новее
- Архитектуры: `arm64-v8a`, `armeabi-v7a`, `x86_64`, `x86`
- Около 5 МБ свободной памяти

### Установка

1. Скачайте [`releases/device-fingerprint-v1.0.0.apk`](releases/device-fingerprint-v1.0.0.apk).
2. На устройстве Android включите **«Установка из неизвестных источников»** для браузера или файлового менеджера, через который вы открываете APK.
3. Откройте APK и нажмите **«Установить»**.
4. Предоставьте runtime-разрешения по запросу — приложение покажет, какие сигналы открывает каждое разрешение.

### Разрешения

Манифест объявляет 16 разрешений, охватывающих состояние телефона, сетевые адаптеры, геолокацию, контакты и рекламные идентификаторы:

- `READ_PHONE_STATE`, `READ_PHONE_NUMBERS`, `READ_PRIVILEGED_PHONE_STATE`
- `ACCESS_WIFI_STATE`, `CHANGE_WIFI_STATE`, `NEARBY_WIFI_DEVICES`
- `BLUETOOTH`, `BLUETOOTH_ADMIN` (Android 11 и ниже), `BLUETOOTH_SCAN`, `BLUETOOTH_CONNECT`
- `ACCESS_COARSE_LOCATION`, `ACCESS_FINE_LOCATION`
- `READ_CONTACTS`
- `com.google.android.gms.permission.AD_ID`
- `QUERY_ALL_PACKAGES`, `INTERNET`

Отказ от какого-либо разрешения отключит лишь соответствующую вкладку; остальное приложение продолжит работать.

### Отказ от ответственности

Этот инструмент опубликован исключительно для **исследований, обучения и самоаудита**. Он не предназначен для слежки за чужими устройствами. Сопровождающий не несёт ответственности за злоупотребление. Используйте его только на оборудовании, которым вы владеете или которое вам разрешено инспектировать.
