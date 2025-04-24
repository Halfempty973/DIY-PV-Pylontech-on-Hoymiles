# ☀️ Home Assistant Energy Management with Zendure Hyper2000 and a Hoymiles HM600 connected to a Pylontech US5000 via OpenDTU on Battery

This project describes a smart energy management system using Home Assistant. It integrates photovoltaic power generation, battery storage, and intelligent AC charging to maximize self-consumption and ensure energy availability during nighttime.

---

## 🔧 Components Used

### ⚡ AC Charger

- **RD6018W**
  - Integrated via **ESPHome**
  - Controlled through a smart current controller (via MQTT)
  - Charges the **Pylontech battery** based on solar surplus and SOC levels

### ☀️ PV System

- **Zendure Inverter**
  - Total module capacity: **4 × 500 W = 2000 W**
  - Storage: **Zendure 4 kWh battery**
  - Directly connected to the solar panels
  - Main power supply during the day and optional AC charging source

### 🔋 Nighttime Power System

- **Hoymiles HM600**

  - Microinverter connected to the **Pylontech US5000 battery**
  - Controlled via a smart switch
  - Only active if SOC > minimum threshold (configurable)

- **Pylontech US5000**

  - LiFePO4 battery with 4.8 kWh capacity
  - Powers the home during the night
  - Charged via RD6018W depending on solar input and SOC

### 📡 Communication & Control

- **OpenDTU on Battery**

  - Open-source DTU firmware
  - Monitors and regulates the Hoymiles inverter
  - Communicates via **MQTT** with Home Assistant
  - Controls the Pylontech US5000 over CAN

- **Home Assistant**

  - Central control unit
  - Manages:
    - AC charging activation
    - Dynamic charge current adjustment
    - Inverter control based on battery SOC
    - Automatic day/night mode switching
  - Utilizes:
    - **Input Number Helpers** for configurable thresholds
    - **Template Sensors** to calculate power surplus
    - **Automations** to control AC/Battery interaction

---

## 📊 System Logic Overview

- **AC Charging** is enabled when:

  - Solar power > configurable threshold
  - SOC < maximum value
  - Calculated surplus > base load + storage charging

- **Hoymiles Inverter** is enabled when:

  - SOC > minimum threshold
  - Only if AC charging is not active

- **AC Charging and Hoymiles Inverter** are never active at the same time

---

## 📷 Optional Dashboard Screenshots

> Include screenshots of your Home Assistant dashboard here
> "Yet to complete the Project"
---

## 🛠️ Setup Instructions

1. Install Home Assistant (e.g., on Raspberry Pi or Proxmox)
2. Configure MQTT integration
3. Flash ESPHome firmware onto the RD6018W LAB-Bench Supply
4. Set up OpenDTU with Hoymiles inverter and MQTT
5. Add input\_number helpers via the UI
6. Import the YAML configurations and dashboard

---

## 🤝 Contributing

Pull requests are welcome! Open an issue for suggestions or improvements.

---

## 📜 License

MIT License – free to use and modify.

