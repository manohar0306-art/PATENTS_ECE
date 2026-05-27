
# 🚑 Smart Ambulance System
### **Integrated Emergency Response System (IERS)**
**Official Patent Portfolio | Innovation #01**

[![Patent-Pending](https://img.shields.io/badge/Status-Patent--Pending-blue?style=for-the-badge)](https://iprsearch.ipindia.gov.in)
[![Publication-No](https://img.shields.io/badge/Publication--No-IN202641011997_A1-success?style=for-the-badge)](https://iprsearch.ipindia.gov.in)
[![Tech-Stack](https://img.shields.io/badge/Tech-Embedded_C_|_IoT_|_DSP-orange?style=for-the-badge)]()

---

## 🌟 The Vision
Traditional emergency transit suffers from a **"Double Delay"**: physical traffic gridlock and a medical information blackout. The **IERS** attacks both by integrating live health telemetry with automated traffic pre-emption.

## ⚡ Technical Core & Innovations

### 🩺 1. Real-Time Health Telemetry
* **Digital Signal Processing:** Implements a **2nd order IIR bandpass filter** on-chip to strip 50Hz electrical hum and baseline drift from raw ECG signals.
* **Multi-Sensor Array:** Synchronous monitoring of ECG (AD8232), SpO2 (MAX30100), Blood Pressure, and GSR (Stress Sensing).
* **Cloud Sync:** Formats data into **JSON packets** for live hospital-side visualization via Blynk/Cloud dashboards.

### 🚦 2. Intelligent Traffic Override
* **GPS-Based Geofencing:** Uses the **Haversine Formula** to calculate the precise great-circle distance between the ambulance and upcoming junctions.
* **Independent RF Link:** Uses a dedicated **nRF24L01+ transceiver** (2.4 GHz) to trigger a "Green Corridor," bypassing unreliable cellular networks.
* **Concurrent Operation:** The Health and Traffic modules work in parallel, powered by the vehicle's 12V battery through an LM2596 conditioning stage.

---
## 📁 Repository Contents
* [📄 View Official Publication](./01-PUBLICATION.pdf)
* [🖼️ Technical Schematics](./01-DRAWINGS.pdf)
---
  
## 🏗️ System Architecture & Logic Flow


```mermaid
graph TD
    A[Start: Emergency Run] --> B{Parallel Process}
    B --> H[Health Monitoring]
    B --> T[Traffic Pre-emption]
    H -->|JSON via WiFi| Cloud[Hospital ER Dashboard]
    T -->|Within 800m| Radio[nRF24L01 Priority Signal]
    Radio --> JCU[Junction Control Unit]
    JCU -->|Override| Light[Traffic Signal: GREEN]
    Goal((Saved Lives))
    Cloud --> Goal
    Light --> Goal
