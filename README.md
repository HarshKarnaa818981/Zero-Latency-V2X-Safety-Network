# Zero-Latency V2X Safety Network

**Integrating Wildlife Autodetection and Hairpin Bend Collision Avoidance**

<p align="center">
  <img src="../../assets/project-thumbnails/v2x-safety-network.png" alt="Zero-Latency V2X Safety Network" width="80%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/ESP32-Firmware-blue" />
  <img src="https://img.shields.io/badge/LoRa-SX1278-orange" />
  <img src="https://img.shields.io/badge/Embedded%20C-Arduino%20IDE-green" />
  <img src="https://img.shields.io/badge/Safety-V2X-red" />
  <img src="https://img.shields.io/badge/Status-Ongoing-yellow" />
</p>

---

## 📌 Problem Statement

Blind hairpin bends and wildlife-crossing zones are high-risk road regions where drivers may not see approaching vehicles, animals or road hazards in time. In hilly, forested or low-connectivity areas, cloud-dependent warning systems may not work reliably.

This project aims to create a low-latency embedded safety network that can detect hazards locally and send real-time alerts directly between roadside and vehicle units.

---

## 💡 Proposed Solution

The system uses ESP32-based embedded nodes for roadside and vehicle communication. A Roadside Unit detects possible wildlife movement using a piezo vibration sensor and sends warning messages through SX1278/Ra-02 LoRa communication. The On-Board Unit receives the alert and warns the driver using an OLED display and buzzer.

The extended concept also includes hairpin-bend collision avoidance using OBU and RPU nodes to coordinate vehicle movement at blind curves.

---

## ✨ Key Features

- ESP32-based RSU–OBU prototype for low-connectivity road safety.
- SX1278/Ra-02 LoRa communication at 433 MHz.
- Piezo vibration sensing for wildlife movement detection.
- OLED display and buzzer-based driver warning system.
- Firmware alert states: WILDLIFE, SAFE, WAIT and GO.
- RSU–OBU message acknowledgement logic.
- Threshold tuning to reduce false triggering and unstable alerts.
- Expandable architecture for hairpin-bend vehicle priority control.

---

## 🛠️ Hardware and Tools

| Category | Components / Tools |
|---|---|
| Microcontroller | ESP32 DOIT DevKit V1 |
| Wireless Module | SX1278 / Ra-02 LoRa 433 MHz |
| Sensor | Piezo vibration sensor with LM358 amplifier |
| Display | 0.96-inch SSD1306 OLED |
| Alert Output | 3V buzzer |
| Programming | Embedded C / Arduino IDE |
| Communication | SPI, I2C, LoRa |
| Debugging | Serial Monitor, multimeter, test logs |

---

## 🧠 System Architecture

```text
Wildlife / Road Vibration
          ↓
Piezo Sensor + LM358
          ↓
ESP32 Roadside Unit
          ↓
LoRa 433 MHz Message
          ↓
ESP32 On-Board Unit
          ↓
OLED Warning + Buzzer Alert
```

Add your diagram here:

```md
![System Architecture](./docs/architecture.png)
```

---

## 🔁 Message Flow

```text
RSU detects vibration
        ↓
Detection confirmed by threshold logic
        ↓
RSU sends: WILDLIFE
        ↓
OBU receives alert
        ↓
OBU displays warning and activates buzzer
        ↓
OBU sends acknowledgement
        ↓
RSU continues monitoring
        ↓
RSU sends SAFE when hazard clears
```

---

## 📂 Folder Structure

```text
zero-latency-v2x-safety-network/
├── README.md
├── docs/
│   ├── architecture.png
│   ├── methodology-flowchart.png
│   ├── circuit-diagram.png
│   └── prototype-photos/
├── firmware/
│   ├── fsn/
│   ├── obu1/
|   ├── obu2/
│   └── rpu/
├── simulation/
│   ├── simulation-code/
│   ├── simulation-output.png
|   ├── simulation-flow.png
│   └── simulation-notes.md
├── tests/
│   ├── piezo-readings.md
│   ├── lora-test-results.md
│   └── demo-checklist.md
└── media/
    └── demo-video-link.md
```

---

## 🚀 Setup and Upload Guide

### Required Libraries

Install these libraries in Arduino IDE:

- LoRa
- Adafruit GFX
- Adafruit SSD1306
- Wire
- SPI

### Board Selection

Use:

```text
Board: ESP32 DOIT DevKit V1
Frequency: 240 MHz
```

### LoRa Pin Mapping

| LoRa Pin | ESP32 GPIO |
|---|---|
| SCK | GPIO18 |
| MISO | GPIO19 |
| MOSI | GPIO23 |
| NSS / SS | GPIO5 |
| RST | GPIO14 |
| DIO0 | GPIO26 |

---
## 💻 Software Simulation

Before hardware testing, the system logic was verified using software-based simulation to validate the alert flow, message states and decision behavior of the proposed V2X safety network.

The simulation demonstrates how the Roadside Unit and On-Board Unit respond under different road-safety conditions such as wildlife detection, safe road status, blind-bend vehicle coordination and priority-based movement control.

### Simulation Objectives

- Verify RSU–OBU communication logic before hardware deployment.
- Simulate WILDLIFE, SAFE, WAIT and GO alert states.
- Validate blind-bend collision avoidance decision flow.
- Check priority-based vehicle movement scenarios.
- Observe system response for normal, warning and safe conditions.

### Simulated Scenarios

| Scenario | Description | Expected Output |
|---|---|---|
| Wildlife detected | RSU detects vibration/hazard condition | OBU displays warning and activates buzzer |
| Road safe | Hazard condition clears | OBU displays SAFE and buzzer turns OFF |
| Blind-bend conflict | Two vehicles approach a blind curve | One vehicle receives GO, the other receives WAIT |
| Priority vehicle | Emergency/priority vehicle is detected | Priority vehicle receives movement permission |
| Communication delay/loss | No fresh update received | Vehicle remains in WAIT/SAFE fallback state |

### Simulation Output

Add simulation screenshots or screen recordings here:

```md
<img width="1600" height="801" alt="WhatsApp Image 2026-10-07 at 12 10 33 PM" src="https://github.com/user-attachments/assets/7c526ae8-4b1e-41f6-9c07-d5dea640bd09" />

```

Optional demo video:

```md
[Watch Software Simulation Demo](./media/software-simulation-demo.md)
```

---

## 🧪 Testing Checklist

| Test | Expected Output |
|---|---|
| SX1278 detection | Version register responds correctly |
| RSU detection | Piezo vibration is detected without excessive false triggering |
| LoRa transmission | OBU receives WILDLIFE and SAFE messages |
| OLED display | Correct alert message is shown |
| Buzzer alert | Buzzer activates during warning state |
| Recovery | System returns to SAFE state after hazard clears |

---

## 📊 Current Status

- Software simulation of the V2X alert and priority logic completed.
- RSU–OBU LoRa communication tested.
- OLED alert display implemented.
- Buzzer alert added.
- Piezo-based wildlife detection under tuning.
- Hairpin-bend priority logic under development.
- Hardware prototype testing and demonstration preparation ongoing.

---

## 🔮 Future Improvements

- Add CAN interface for vehicle-level integration.
- Add FreeRTOS-based task separation.
- Add GPS location tagging.
- Add solar-powered roadside deployment.
- Add enclosure and weatherproofing for outdoor testing.
- Add dashboard for logging hazard events.

---

## 👨‍💻 Author

**Harsha K N**  
Electronics and Communication Engineering  
GitHub: `https://github.com/HarshKarnaa818981`  
LinkedIn: `https://linkedin.com/in/harsha-k-n-9096222a3`
