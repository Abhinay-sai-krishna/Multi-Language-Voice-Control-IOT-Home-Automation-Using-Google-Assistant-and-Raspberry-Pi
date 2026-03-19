# Multi-Language Voice Control IoT Home Automation 🏠🌐



This project demonstrates a state-of-the-art **IoT Home Automation System** that allows users to control electrical appliances using voice commands in multiple languages (English, Hindi, etc.) via **Google Assistant** and a **Raspberry Pi**.

---

## 🚀 Overview

In the era of smart homes, language should never be a barrier. This project leverages the power of **Google Assistant Routines** and a local **Raspberry Pi Web Server** to create a seamless, voice-controlled environment. Whether you say *"Turn on the lights"* or *"Light jalado"*, the system responds instantly.

### Key Features
- **Multi-Language Support**: Control your home in Hindi, English, Bengali, Marathi, and more.
- **Google Assistant Integration**: Uses the familiar Google Assistant interface and Routines.
- **Local Control**: Raspberry Pi acts as a fast, local web server (Apache/PHP).
- **Custom Android App**: Includes a dedicated app with a WebView interface for manual control.

---

## 🛠️ Components Required

| Component | Quantity | Purpose |
| :--- | :---: | :--- |
| **Raspberry Pi Zero W** | 1 | Main Controller & Web Server |
| **2-Channel Relay Module** | 1 | Switching AC Appliances |
| **Switch Box** | 1 | Physical Housing/Mounting |
| **Connecting Wires** | - | Circuit Interconnections |

---

## 📐 Circuit Diagram

The Raspberry Pi is connected to the relay board to facilitate high-voltage switching.

**Connections:**
- **Pin 5V** (RPi) → **VCC** (Relay Board)
- **Pin GND** (RPi) → **GND** (Relay Board)
- **GPIO 22** (RPi) → **IN1** (Relay Board) *(Note: GPIO may vary; check your source code)*


---

## ⚙️ Setup Instructions

### 1. Raspberry Pi Configuration 🍓

First, set up an Apache server with PHP support on your Raspberry Pi:

```bash
# Update and install Apache
sudo apt-get update
sudo apt-get install apache2 -y

# Install PHP and Apache Module
sudo apt-get install php libapache2-mod-php -y
```

Move the PHP control files (`lightson.php` and `lightsoff.php`) to `/var/www/html/`.

**`lightson.php` Code Snippet:**
```php
<?php
  system("gpio -g mode 22 out"); 
  system("gpio -g write 22 1");
?>
```

---

### 2. Google Assistant Routines 🎙️

1. Open the **Google Home** app.
2. Navigate to **Routines** and tap the **+** (plus) icon.
3. **Add Command**: Enter phrases in your preferred language (e.g., *"Lights On"*, *"Bijli chalu karo"*).
4. **Add Action**: Use the "Browse to URL" action or trigger a web request to:
   `http://[Your_RPi_IP]/lightson.php`

---

### 3. Android Application 📱

The project includes a custom Android application developed in Android Studio.

- **Manifest**: Ensure `<uses-permission android:name="android.permission.INTERNET" />` is added.
- **WebView**: Configure the main activity to load the Raspberry Pi's local IP address.




---

## 📂 Project Structure

```text
CODE/
├── Code/
│   ├── APP/                 # Android Studio Project & APK
│   │   ├── Home automation.apk
│   │   └── src/
│   ├── lightsoff.php        # Logic to turn GPIO OFF
│   └── lightson.php         # Logic to turn GPIO ON
└── README.md                # This documentation
```

---

## 🖼️ Figure

![WhatsApp Image 2026-03-19 at 11 50 34 AM](https://github.com/user-attachments/assets/4d0bef66-7b5b-4e56-ba3a-eedfd41ea4b2)


---

