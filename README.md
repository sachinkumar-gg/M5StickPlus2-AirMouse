# 🖱️ M5Stack Stick Plus2 AirMouse (Bluetooth)

Turn your **M5Stack Stick Plus2** into a **Bluetooth AirMouse** that controls your iPhone, iPad, Mac, or PC via motion and buttons.

---

## 📦 Requirements

- **Hardware:**
  - M5Stack Stick Plus2 (ESP32-based)
- **Software:**
  - Arduino IDE
  - ESP32 board core (v2.0.11 recommended)
  - Libraries:
    - [M5Unified](https://github.com/m5stack/M5Unified)
    - [ESP32 BLE Mouse](https://github.com/T-vK/ESP32-BLE-Mouse)

---

## ⚙️ Installation Steps

1. **Install Board:**
   - Open Arduino IDE → *File → Preferences*
   - Add this URL to *Additional Board Manager URLs*:
     ```
     https://espressif.github.io/arduino-esp32/package_esp32_index.json
     ```
   - Go to *Tools → Board → Boards Manager*
   - Search for **esp32**
   - Install version **2.0.11**

2. **Install Libraries:**
   - Go to *Sketch → Include Library → Manage Libraries*
   - Search and install:
     - **M5Unified**
     - **ESP32 BLE Mouse**
   - (If errors appear, patch the BLE Mouse library as per issue #150)

3. **Select Board:**
   - *Tools → Board → M5Stack → M5Stick-C Plus2*

4. **Upload the Code**
   - Connect your M5Stick via USB-C
   - Select correct port under *Tools → Port*
   - Upload the provided `.ino` sketch

---

## 🧠 Working Principle

- The **gyroscope** inside the M5Stick senses motion.
- The **ESP32 BLE** acts as a Bluetooth mouse.
- Movement of the device moves the mouse pointer.
- Buttons:
  - **Button A** → Left Click
  - **Button B** → Right Click

---

## 📲 Connecting to iPhone / Mac

1. Open **Settings → Bluetooth**
2. Turn on M5Stick — it will broadcast as **M5 AirMouse**
3. Tap **“M5 AirMouse”** to pair
4. Move the device to control the cursor
   - On iPhone/iPad, go to **Accessibility → Touch → AssistiveTouch → Devices → Pointing Devices** to enable mouse control.

---

## 🧩 Adjustments

To invert or tune motion sensitivity, modify these lines:

```cpp
int moveX = (int)(-gyroY / 6);
int moveY = (int)(gyroX / 6);
```

Change the divisor (`/6`) to alter sensitivity.

---

## 🧾 Credits

- **Developer:** Sachin  
- **Core Libraries:** [M5Unified](https://github.com/m5stack/M5Unified), [ESP32 BLE Mouse](https://github.com/T-vK/ESP32-BLE-Mouse)
