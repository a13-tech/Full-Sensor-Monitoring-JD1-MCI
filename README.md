# Full-Sensor-Monitoring-JD1-MCI


# 📡 MCI JD1 - Telemetry & Multi-Sensor IoT System

![Board](https://img.shields.io/badge/Board-ESP32_DevKit_V1-red?style=flat&logo=espressif)
![Framework](https://img.shields.io/badge/Framework-Arduino-blue?style=flat&logo=arduino)
![IDE](https://img.shields.io/badge/IDE-VS_Code_%2B_PlatformIO-orange?style=flat&logo=visualstudiocode)
![Team](https://img.shields.io/badge/System-MCI_JD1-cyan)

Sistem telemetry dan pemantauan nirkabel lokal dikembangkan untuk project **MCI JD1**. Mengintegrasikan 4 sensor telemetry (suhu, jarak, gerak, dan obstacle) dengan antarmuka **OLED 1.3" (SH1106)** serta **Web Dashboard Real-Time** mandiri via **Access Point (AP)**.

---

## 🚀 Fitur Utama

- **Autonomous Access Point**: Memancarkan SSID Wi-Fi bawaan `MCI JD1` tanpa ketergantungan router luar.
- **MCI Real-Time Web Dashboard**: Interface telemetry modern berbasis AJAX/Fetch API yang diperbarui otomatis setiap detik tanpa reload layar.
- **On-Board Display Integration**: Menampilkan ringkasan telemetry pada OLED 1.3 inci SH1106 via I2C.
- **Multi-Sensor Integration**:
  - Pemantauan suhu presisi via **DS18B20**.
  - Pengukuran jarak ultrasonik via **HC-SR04**.
  - Deteksi pergerakan presisi via **HC-SR501 (PIR)**.
  - Deteksi halangan jarak dekat via **Sensor IR Obstacle**.

---

## 📖 Cara Akses Web Telemetry

1. Nyalakan board ESP32.
2. Sambungkan HP/Laptop ke Wi-Fi:
   - **SSID**: `MCI JD1`
   - **Password**: `CREATIVETEAM`
3. Buka browser dan ketik alamat IP: `http://192.168.4.1`

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
                  +-------------------------------+
