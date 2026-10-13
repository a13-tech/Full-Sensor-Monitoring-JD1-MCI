# Full-Sensor-Monitoring-JD1-MCI


# 📡 ESP32 Multi-Sensor IoT Monitoring System

![ESP32](https://img.shields.io/badge/Board-ESP32_DevKit_V1-red?style=flat&logo=espressif)
![Framework](https://img.shields.io/badge/Framework-Arduino-blue?style=flat&logo=arduino)
![IDE](https://img.shields.io/badge/IDE-VS_Code_%2B_PlatformIO-orange?style=flat&logo=visualstudiocode)
![License](https://img.shields.io/badge/License-MIT-green)

Sistem pemantauan lingkungan dan keamanan lokal berbasis **ESP32 DevKit V1**. Project ini mengintegrasikan 4 jenis sensor dengan tampilan visual pada **OLED 1.3" (SH1106)** serta **Web Dashboard Real-Time** yang diakses secara nirkabel melalui jaringan **Wi-Fi Access Point (AP)** tanpa memerlukan router eksternal.

---

## 🚀 Fitur Utama

- **Autonomous Access Point**: ESP32 memancarkan jaringan Wi-Fi mandiri (`ESP32-Monitoring`).
- **Real-Time Web Dashboard**: Antarmuka web modern dengan fitur *auto-refresh* (AJAX/Fetch API) tiap 1 detik tanpa membuat layar *blink* / *reload*.
- **On-Board Display Integration**: Menampilkan data telemetry secara *live* pada layar OLED 1.3 inci SH1106 via bus I2C.
- **Multi-Sensor Integration**:
  - Pemantauan suhu presisi via **DS18B20**.
  - Pengukuran jarak ultrasonik via **HC-SR04**.
  - Deteksi pergerakan presisi via **HC-SR501 (PIR)**.
  - Deteksi objek jarak dekat via **Sensor IR Obstacle**.

---

## 🛠️ Modul & Komponen Hardware

| Komponen | Spesifikasi / Deskripsi | Pin ESP32 |
| :--- | :--- | :--- |
| **Microcontroller** | ESP32 DevKit V1 (30-pin) | - |
| **Display** | OLED 1.3" I2C (SH1106 Driver) | SDA: GPIO 23, SCL: GPIO 22 |
| **Suhu** | DS18B20 Waterproof Probe (+ Resistor 4.7kΩ) | Data: GPIO 4 |
| **Ultrasonik** | HC-SR04 | Trig: GPIO 5, Echo: GPIO 18 |
| **Gerak PIR** | HC-SR501 Motion Sensor | Out: GPIO 25 |
| **IR Obstacle** | Modul Sensor Inframerah Digital | Out: GPIO 21 |

---

## 🔌 Skema Rangkaian (Pinout)

```text
                  +-------------------------------+
                  |        ESP32 DevKit V1        |
                  +-------------------------------+
                  |                               |
       (3.3V) ----| 3V3                     GPIO23|---- SDA [OLED 1.3"]
       (GND)  ----| GND                     GPIO22|---- SCL [OLED 1.3"]
       (5V)   ----| VIN                     GPIO21|---- OUT [Sensor IR]
                  |                         GPIO25|---- OUT [HC-SR501 PIR]
                  |                         GPIO18|---- Echo [HC-SR04]
                  |                         GPIO5 |---- Trig [HC-SR04]
                  |                         GPIO4 |---- DATA [DS18B20]
                  +-------------------------------+
