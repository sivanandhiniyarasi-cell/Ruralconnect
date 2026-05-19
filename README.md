# 🌐 RuralConnect
### Smart Multi-Network SIM Device for Rural Communities

> **Status:** Early Stage — Customer Discovery Phase  
> **Version:** 1.0 | May 2026  
> **Author:** RuralConnect Founding Team

---

## 📡 What is RuralConnect?

RuralConnect is a portable, battery-powered smart hotspot device that **automatically detects and connects to the strongest available mobile network** (3G, 4G, or 5G) in rural and low-coverage areas.

It uses a **Multi-IMSI eSIM** to hold profiles from multiple carriers simultaneously and switches between them in real time — based on signal strength, network speed, and availability — without any action required from the user.

**One device. Every available network. Always the best signal.**

---

## 🚨 The Problem

Rural communities are consistently underserved by mobile carriers:

- A farmer in rural Bihar gets 2G in one corner of their field and nothing in another
- A student loses their online class every 20 minutes due to signal drops
- A health worker switches SIM cards 3–4 times a day just to stay connected
- Over **900 million rural Indians** suffer from unreliable or inconsistent mobile connectivity

Existing solutions — single-carrier SIMs, urban-optimised eSIM products, expensive satellite internet — either don't reach rural areas or are too costly and complex for everyday rural users.

---

## ✅ Our Solution

A plug-and-play device that:

- 📶 Scans all available carrier networks every 30 seconds
- 🔄 Switches to the strongest carrier automatically (under 10 seconds)
- 📡 Shares connection via Wi-Fi hotspot to up to 10 devices
- 🔋 Runs for 8–10 hours on battery
- 🌧️ Weatherproof (IP65) for outdoor/agricultural use
- ⚙️ Zero configuration — works straight out of the box

---

## 🔧 Hardware Stack

| Component | Part | Purpose |
|---|---|---|
| Main Processor | Raspberry Pi Zero 2W | Runs switching logic & hotspot |
| LTE/5G Modem | Quectel RM500Q-GL | Multi-band 5G/4G/3G modem |
| eSIM Chip | Infineon SLx9670 | Multi-IMSI eSIM |
| SIM Platform | Twilio Super SIM | Access to 200+ carrier networks |
| Battery | 3.7V 5000mAh LiPo | 8–10 hours operation |
| Power Management | Adafruit PowerBoost 1000C | Charging + power regulation |
| Antenna | LTE External SMA Antenna | Improved signal in weak areas |
| Enclosure | IP65 Plastic Project Box | Weatherproof casing |
| Display | 0.96" OLED I2C | Signal strength + active carrier |

**Estimated BOM:** ~$113/unit (prototype) → ~$75 at scale (500+ units)

---

## 💻 Software Stack

| Layer | Technology |
|---|---|
| OS | Raspberry Pi OS Lite (64-bit) |
| Modem Control | ModemManager + mmcli |
| eSIM Management | lpac (open source LPA) |
| Network Monitor | Python 3 daemon |
| Hotspot | hostapd + dnsmasq |
| Status Display | Python + Luma.OLED |
| Config Interface | Flask (local web UI) |

---

## 🧠 Network Switching Algorithm

The core of RuralConnect is a Python daemon that runs this loop every 30 seconds:

```
1. SCAN   → Query modem for all visible networks (RSSI, RAT type, carrier)
2. SCORE  → Score = (RSSI × 0.5) + (Network Generation × 0.3) + (Latency × 0.2)
3. COMPARE → Is best available score > current + hysteresis buffer?
4. SWITCH  → Load new eSIM carrier profile, reconnect modem, restore hotspot
5. LOG     → Save switch event to local SQLite database
```

### Network Scoring Weights

| Network Type | Score Weight | Min Acceptable RSSI |
|---|---|---|
| 5G (NR) | 10 | -85 dBm |
| 4G LTE | 7 | -95 dBm |
| 3G UMTS | 4 | -100 dBm |
| 2G GSM (fallback) | 1 | -105 dBm |

---

## 🗺️ Prototype Build Roadmap

| Phase | Timeline | Milestone |
|---|---|---|
| Phase 1 | Month 1–2 | Bench prototype — switching logic working |
| Phase 2 | Month 3 | Integrated prototype in enclosure, battery-powered |
| Phase 3 | Month 4 | Software polish — OLED display, web config UI |
| Phase 4 | Month 5–6 | Field testing — 10 devices in rural communities |
| Phase 5 | Month 7–9 | Pilot production — 50 units |

---

## 🎯 Target Market

**Primary:** Rural India — 900M people, 4 major carriers (Jio, Airtel, Vi, BSNL), world's cheapest data at ₹9/GB

**Secondary:** Sub-Saharan Africa, Rural USA, Southeast Asia, Rural Australia

**Entry Strategy:**
- Government procurement via BharatNet last-mile device programme
- NGO partnerships for subsidised distribution
- Kisan (farmer) cooperative networks
- Common Service Centres (500,000+ across India)

---

## 📊 Current Status

- [x] Problem validated through research
- [x] Technical specification drafted
- [x] Business plan drafted
- [ ] Customer discovery interviews (target: 30 rural families)
- [ ] Bench prototype built
- [ ] Field testing
- [ ] Regulatory certification (BIS India)
- [ ] Seed funding raised

---

## 📁 Repository Structure

```
RuralConnect/
├── README.md                          ← You are here
├── docs/
│   ├── RuralConnect_Tech_Spec.docx    ← Full prototype specification
│   └── RuralConnect_Business_Plan.docx← Full business plan
├── hardware/                          ← Schematics & BOM (coming soon)
├── firmware/                          ← Switching daemon source code (coming soon)
└── research/                          ← Customer discovery notes (coming soon)
```

---

## 🤝 Contributing

This project is in early stage. Contributions, feedback, and ideas are welcome — especially from:

- 🔌 Embedded systems / LTE modem engineers
- 🐍 Python / Linux networking developers
- 🌾 Anyone with rural connectivity field experience
- 📡 Telecom industry insiders

Open an issue or reach out directly to discuss.

---

## 📬 Contact

**Email:** founders@ruralconnect.io  
**Project Stage:** Pre-seed / Customer Discovery  
**Location:** India 🇮🇳

---

## 📄 License

This project is currently **All Rights Reserved** pending IP filing.  
Licensing terms will be updated once patent application is submitted.

---

> *"The child who walks to a neighbour's house to catch a signal — that is the reason this exists."*
# Ruralconnect