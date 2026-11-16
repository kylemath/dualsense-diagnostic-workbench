# DualSense 3D Diagnostic & Calibration Workbench

A **zero-install, single-page WebHID + Three.js hardware diagnostic, potentiometer carbon-track scanner, and Sony NVS flash calibration workbench** for PlayStation 5 **DualSense** (`0x054c:0x0ce6`) and **DualSense Edge** (`0x054c:0x0df2`) controllers.

### 🌐 Live Zero-Install Web App
👉 **[https://kylemath.github.io/dualsense-diagnostic-workbench/](https://kylemath.github.io/dualsense-diagnostic-workbench/)**  
*(Open in desktop **Google Chrome**, **Microsoft Edge**, or **Brave** with your DualSense plugged in via a USB data cable.)*

---

## Key Features

1. **Persistent Interactive 3D DualSense View (Three.js)**
   - Articulated 3D DualSense mesh where all 19 buttons, `L2`/`R2` triggers, `LX`/`LY`/`RX`/`RY` thumbsticks, `L3`/`R3` clicks, touchpad 2-finger capacitive touches, and RGB lightbar animate in real time at 250 Hz.
   - Includes **Front / Angle / Triggers / Back** camera presets, **3D Live Gyro/Accelerometer Pose**, and **White / Midnight Black / Cosmic Red** shell finishes.
2. **256-Bucket Potentiometer Carbon Track & Skip Scanner (Tab 1)**
   - Maps every `0..255` ADC bucket along the potentiometer resistive track as you sweep the stick slowly from Left (`0`) to Right (`255`).
   - Automatically highlights **healthy read buckets in Green** and **skipped/dead wiper dropout buckets in Crimson Red** (e.g. detecting micro-wear or collector-ring oxidation in the `88..155` center zone).
   - Tracks **Left vs. Right Return-to-Center Hysteresis** and plots a **250 Hz 4-channel oscilloscope** (`LX`, `LY`, `RX`, `RY`) with automatic glitch spike detection.
3. **2D Stick Scopes & Circularity Analyzer (Tab 2)**
   - High-precision 2D circular scopes with an 8% game deadzone ring, live trail plotting, and 36-sector outer circularity error calculation.
4. **Sony NVS Hardware Stick Center & Range Calibration (Tab 3)**
   - Implements the low-level DualSense USB Feature Report calibration state machine (`0x80`, `0x81`, `0x82`, `0x83`):
     - **NVS Unlock / Lock (`0x80 [3,2,101,50,64,12]` / `0x80 [3,1]`):** Writes calibration permanently to the controller's non-volatile flash memory so it persists on a PS5 console.
     - **Stick Center Calibration (`0x82 [1,1,1] → [3,1,1] → [2,1,1]`):** Locks the current resting voltage as exact `(128, 128)`.
     - **Stick Outer Range Calibration (`0x82 [1,1,2] → [2,1,2]`):** Samples full circular min/max boundaries.
     - **12-Word Factory Finetune Register Inspector (`0x80 [12,2]`):** Reads and displays `LX/LY/RX/RY Min, Max, Center` 12-bit words from NVS.
5. **Buttons, Analog Triggers & 2-Point Capacitive Touchpad Tester (Tab 4)**
   - 19-button check-off matrix, `L2`/`R2` 8-bit analog progress meters, and a `1920 × 1080` 2-point multi-touch visualizer.
6. **Adaptive Trigger Servo, Haptic Rumble, RGB Lightbar & Register Suite (Tab 5)**
   - Sends native USB Output Report `0x02` to test `L2`/`R2` stepper servos (**Pistol Break**, **Heavy Shotgun**, **SMG Vibration**, **Bow Resistance**), dual haptic rumble motors, and custom RGB lightbar colors.
   - Reads Feature Reports `0x09` (Bluetooth MAC & Paired PS5 Host MAC) and `0x20` (Board Revision `BDM-010`..`BDM-050`, Firmware Build Date, Main/Update Firmware versions).
7. **Illustrated Zero-Solder Potentiometer Cleaning & Repair Guide (Tab 6)**
   - Includes macro anatomy diagrams and step-by-step photos showing how to unclip the green Alps `RKJXV` potentiometer housing on its soldered bottom legs, inspect the `3 o'clock`/`9 o'clock` collector ring and `12 o'clock` carbon track, clean and re-tension the twin brass wiper springs, and re-verify on Tab 1.

---

## Credits & Licenses
- **3D DualSense Model:** Adapted from *PS5 Controller* by [Taohid Animation](https://sketchfab.com/3d-models/ps5-controller-b7bb9c5102a04cb0b1966c6d02bad7d6) (CC BY 4.0) and segmented control rig from [SafaElmali/dualsense-studio](https://github.com/SafaElmali/dualsense-studio).
- **NVS Calibration Protocol Research:** Adapted from [DualShock Calibration GUI](https://github.com/dualshock-tools/dualshock-tools.github.io) (MIT).
- **Repair Guide Photography:** [iFixit DualSense Guides](https://www.ifixit.com/Device/DualSense) (CC BY-NC-SA).
