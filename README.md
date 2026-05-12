# 🌐 NetWatch AI — Network Anomaly Detector

A real-time network threat detection dashboard powered by AI. Analyzes network flow data, scores threats from 0–100, classifies attack types, and provides plain-English incident analysis — like having an AI security operations analyst watching your network.

---

## 🔍 What It Does

- **Classifies** network flows as Normal, DDoS, Port Scan, Brute Force, or Lateral Movement
- **Scores** every flow with a 0–100 threat severity score
- **Live dashboard** with real-time traffic chart, threat dial, and scrolling alert feed
- **Auto-monitoring mode** — simulates a live network stream, detecting attacks as they happen
- **AI Analyst panel** — explains every detection and recommends specific actions
- **Attack breakdown** — tracks counts per attack type across the session

---

## 🚀 Live Demo

👉 [**Try it live →**](https://yourusername.github.io/netwatch-ai)

**Quick start in the demo:**
1. Click any attack scenario button (DDoS, Port Scan, Brute Force, Lateral Movement)
2. Hit **Analyze Flow** — get instant AI classification
3. Or hit **▶ Start Live Scan** to watch the dashboard detect attacks automatically in real time

---

## 📸 Features

| Feature | Description |
|---|---|
| 🎯 Flow Analysis | Submit any network flow — get threat score + attack classification |
| 📡 Live Monitoring | Auto-injects flows every 4s simulating a real network stream |
| 📊 Traffic Chart | 60-second rolling window of packets/s vs threat score |
| 🚨 Alert Feed | Timestamped log of every detected threat with severity |
| 🤖 AI Analyst | Plain-English incident summary + remediation recommendations |
| ⚡ Attack Scenarios | One-click presets for DDoS, Port Scan, Brute Force, Lateral Movement |

---

## 🧠 How It Works

```
Network Flow Input (src IP, dst IP, protocol, port, packets/s, bytes/s, flags)
    ↓
Feature Extraction & Normalization
    ↓
Isolation Forest → Anomaly Score (-1.0 to 1.0)
Autoencoder → Reconstruction Error
    ↓
Random Forest Classifier → Attack Type Label
    ↓
Ensemble → Threat Score (0–100) + Severity + Confidence
    ↓
AI Analyst → Plain-English Summary + Recommended Action
```

### Attack Types Detected

| Attack | How It's Detected |
|---|---|
| **DDoS** | Extremely high packet rate (>10k pps), small packet size, single destination |
| **Port Scan** | Sequential port targeting, SYN-only flags, very short flow duration |
| **Brute Force** | Repeated flows to port 22/3389, medium rate, long duration |
| **Lateral Movement** | Internal east-west traffic (RFC1918→RFC1918), SMB/RDP protocols |
| **Normal** | Traffic within learned baseline distributions |

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| AI Engine | Claude AI (claude-sonnet-4) via Anthropic API |
| ML Approach | Isolation Forest + Autoencoder + Ensemble classification |
| Visualization | Chart.js (real-time line chart) |
| Frontend | Vanilla HTML/CSS/JavaScript |
| Deployment | GitHub Pages (static, no backend needed) |
| Dataset Reference | CICIDS 2017/2018 (Canadian Institute for Cybersecurity) |

---

## 📂 Project Structure

```
netwatch-ai/
├── NetWatchAI.html       # Full app — dashboard + AI engine in one file
└── README.md
```

---

## ⚙️ Run Locally

No install needed. Just open `NetWatchAI.html` in your browser.

```bash
git clone https://github.com/yourusername/netwatch-ai
cd netwatch-ai
open NetWatchAI.html
```

---

## 🎯 Why I Built This

Enterprise SOC teams deal with thousands of alerts per day — most tools just dump raw data. I wanted to build a detector that not only flags anomalies but tells you what type of attack it is, how severe it is, and what to do about it — all in real time.

This project demonstrates:
- ML anomaly detection techniques (Isolation Forest, Autoencoders)
- Real-time data visualization and streaming UI
- Multi-class attack classification
- Applied AI in a security operations context
- Reference to production-grade datasets (CICIDS 2017/2018 — used by UNB's own CIC lab)

---

## 📊 Example Detection

```
Flow:    192.168.100.5 → 10.0.0.1:80 · UDP · 12,500 pps · 1.45MB/s
Result:  DDoS ATTACK DETECTED
Score:   96 / 100  [CRITICAL]
Anomaly: -0.847 (Isolation Forest)

Indicators:
  → Packet rate 297x above baseline (12,500 vs ~42 pps)
  → Packet size 64 bytes — consistent with UDP flood
  → Single destination IP targeted across all flows
  → No TCP handshake — stateless volumetric attack pattern

Action:  Block source IP at perimeter firewall. Enable rate limiting on port 80.
Pattern: UDP Flood / Volumetric Layer 3 DDoS
```

---

## 🗺️ Roadmap

- [ ] PCAP file upload — analyze real captured traffic
- [ ] Export incident report as PDF
- [ ] GeoIP mapping — visualize source countries on world map
- [ ] Multi-flow batch analysis
- [ ] Webhook alerts (Slack / email integration)

---

## 👤 Author

**Harshith Pankaja Mahendra**  
CS Student @ University of New Brunswick  
[LinkedIn](https://www.linkedin.com/in/harshith-mahendra-b61aa02a1)

---

> Part of a two-project AI Cybersecurity Portfolio — see also [PhishGuard AI](https://github.com/yourusername/phishguard-ai)
