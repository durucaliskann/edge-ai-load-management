# edge-ai-load-management
Edge AI-based proactive smart load management system / Uç birim yapay zekâ destekli akıllı şebeke yük yönetim sistemi.
# Edge AI-Based Proactive Smart Load Management System

[![Language](https://img.shields.io/badge/Language-English-blue.svg)](#) [![Language: TR](https://img.shields.io/badge/Language-T%C3%BCrk%C3%A7e-red.svg)](README_tr.md)
[![Hardware](https://img.shields.io/badge/Hardware-STM32F446RE-green.svg)](#) [![Architecture](https://img.shields.io/badge/Architecture-Edge_AI-orange.svg)](#)

> **Note:** This repository serves as an architectural showcase and academic whitepaper for our engineering graduation project. The source code is closed/proprietary and is not publicly distributed here.

## 📌 Abstract
This project presents a microcontroller-based smart load management system designed for power distribution networks with limited capacity. Instead of traditional reactive protection relays that trigger after a blackout or overload occurs, this system utilizes **Edge AI** and real-time data streaming to foresee potential grid failures seconds before they happen, initiating a "Stepwise Load Shedding" protocol. 

## ⚙️ System Architecture

### Hardware Components
The physical prototype is engineered to industrial standards:
* **Core Controller:** STM32F446RE Nucleo Microcontroller
* **Real-Time SCADA Measurement:** 5x INA219 Current Sensors (I2C Protocol) for independent real-time monitoring.
* **High-Efficiency Switching:** D4184 MOSFET modules with low $R_{DS(on)}$ to minimize switching losses for fan and pump control.
* **Loads:** Water Pump (L1), DC Fan (L2), LED & Laser Groups (L3), Servo Motor Groups.

### Software & AI Layer
* **HMI / SCADA:** A custom Python-based graphical interface communicating via UART for real-time monitoring and control.
* **AI Decision Engine:** Utilizes a **Linear Regression** model processing real-time current data to calculate short-term load trends ($y = mx + b$). 
* **Hysteresis Control:** A hysteresis margin is implemented to prevent relay chattering when the load fluctuates near the capacity limit.

## 🏭 Digital Twin Industrial Scenario
To demonstrate scalability, the loads are mapped to a simulated food processing plant (e.g., Molasses/Yeast factory):
* **L1 - Critical Load (Water Pump):** Main liquid feed pump. Must not be interrupted.
* **L2 - Flexible Load (DC Fan):** Fermentation tank cooling system. Can be temporarily slowed down or stopped.
* **L3 - Low Priority Load (LED/Laser):** Facility perimeter lighting. First to be shed during capacity prediction.

## 📊 System Flowchart & Block Diagrams
<img width="3029" height="6547" alt="Load Forecasting and-2026-07-06-130532" src="https://github.com/user-attachments/assets/0f1666fd-1667-4115-816e-c4a1ed55874b" />


## 🎓 Team & Institution
* **Duru Çalışkan** - Electrical and Electronics Engineer
* **Mehmet Emir Çebi** - Electrical and Electronics Engineer
* **Institution:** Ondokuz Mayıs University (OMÜ)
