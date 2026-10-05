# SafeGas AI — Intelligent LPG Cylinder Safety & Monitoring System

> An IoT + AI powered device that detects LPG leaks and fire, automatically shuts off the gas regulator, alerts the user in real time, and predicts refill dates using consumption analytics.


## Track
🏥 HealthTech (Public Safety) · 🌱 Sustainability (Resource Efficiency)

## Problem Statement
LPG cylinders are widely used in homes, restaurants, and small businesses. Gas leaks can lead to fires, explosions, and loss of life. Existing gas detectors usually only sound an alarm — they cannot stop the leak or provide comprehensive monitoring.

## Proposed Solution
SafeGas AI is an IoT-enabled smart safety device that continuously monitors an LPG cylinder and its surrounding environment. When a leak is detected, the system automatically takes protective action and immediately notifies the user, while an AI layer predicts refill needs and flags abnormal usage.

## System Architecture

```
 [MQ-6 Gas Sensor]  ─┐
 [Load Cell + HX711] ─┼──►  ESP32 (Wi-Fi)  ──►  Servo Motor (auto shut-off)
 [Flame Sensor]      ─┘        │                Buzzer + LEDs
                                │                Mobile App (Wi-Fi alert)
                                ▼
                     Cloud + AI Engine (consumption analysis, refill prediction)
                                │
                                ▼
                           Data Storage
```

See [`docs/architecture.md`](docs/architecture.md) for the full breakdown and [`docs/working.md`](docs/working.md) for the step-by-step operating flow.

## Features
- Real-time LPG gas leakage detection (MQ-2 / MQ-6)
- Flame / fire detection
- Cylinder weight monitoring to estimate remaining gas
- Automatic gas regulator shut-off via servo motor
- Buzzer + warning LED alerts
- Instant push notifications to the user's phone
- Live gas level & safety status on a mobile/web dashboard
- AI-based refill date prediction from consumption history
- Abnormal usage / slow-leak detection

## Hardware
| Component | Purpose |
|---|---|
| ESP32 (or Arduino Uno + Wi-Fi module) | Main controller |
| MQ-2 / MQ-5 Gas Sensor | Leak detection |
| Flame Sensor | Fire detection |
| Load Cell + HX711 | Cylinder weight measurement |
| Servo Motor | Rotates regulator valve to shut off gas |
| Buzzer + LEDs | Local alarm |
| OLED / LCD Display | On-device status |
| Rechargeable battery | Power backup |

## Software Stack
- Arduino IDE (firmware)
- MQTT / Blynk (device ↔ cloud messaging)
- Firebase (optional, data sync)
- Flutter / Web dashboard (monitoring UI)
- Python (AI refill prediction)

## Repository Structure
```
safegas-ai/
├── firmware/          ESP32 Arduino sketch — sensor reads, threshold logic, actuation
├── ai-model/           Python script for refill-date prediction from usage history
├── dashboard/          Web dashboard stub for live status + alerts
├── hardware/           Wiring notes / pin mapping
├── docs/               Architecture, working flow, future scope
├── LICENSE
└── README.md
```

## Getting Started
1. Flash `firmware/SafeGasAI_ESP32/SafeGasAI_ESP32.ino` to an ESP32 via Arduino IDE (update `WIFI_SSID` / `WIFI_PASSWORD` and MQTT broker in the config block).
2. Wire the sensors per [`hardware/wiring.md`](hardware/wiring.md).
3. Install Python deps and run the prediction script:
   ```bash
   cd ai-model
   pip install -r requirements.txt
   python refill_prediction.py
   ```
4. Open `dashboard/index.html` in a browser to view the mock live dashboard.

## Expected Impact
- Reduce accidents caused by LPG leaks
- Improve household and commercial kitchen safety
- Minimize gas wastage
- Increase user awareness through real-time monitoring
- Affordable, scalable to homes and small businesses

## Future Scope
- Integration with smart home platforms
- Voice assistant support
- GSM/SMS alerts for areas without Wi-Fi
- Automatic emergency call integration
- Multi-cylinder monitoring for restaurants/industries
- Insurance & maintenance analytics from safety history

## Team
| Role | Name |
|---|---|
| Team Leader | SENPAKAPRIYA D |
| Member | SHANJHENA V |
| Member | TANISSKA S|



