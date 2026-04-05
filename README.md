# 🔍 SOC Lab: Network Discovery Detection – Hunting Reconnaissance Activity

[![Platform](https://img.shields.io/badge/Platform-TryHackMe-black?style=flat&logo=tryhackme)](https://tryhackme.com)
[![Path](https://img.shields.io/badge/Path-SOC%20Level%201-blue?style=flat)](https://tryhackme.com/path/outline/soclevel1)
[![Topic](https://img.shields.io/badge/Topic-Network%20Discovery%20%26%20Scanning%20Detection-007ACC?style=flat)](https://tryhackme.com/room/networkdiscoverydetection)
[![Difficulty](https://img.shields.io/badge/Difficulty-Medium-orange?style=flat)](https://tryhackme.com/room/networkdiscoverydetection)
[![Status](https://img.shields.io/badge/Status-Completed-success?style=flat)]()

**Hands-on SOC detection lab** focused on identifying and analyzing network discovery (reconnaissance) activity from raw SIEM-exported logs.

In this investigation, I worked directly with real-world style CSV logs to detect scanning behavior, differentiate between external reconnaissance and internal lateral scanning, and practice turning noisy data into actionable threat intelligence.

## 📌 Investigation Summary
**Room**: Network Discovery Detection  
**Objective**: Detect and classify various network scanning techniques during the reconnaissance phase.

**What I Did**:
- Parsed and analyzed large, messy SIEM-exported CSV log files using Linux CLI tools
- Identified external scanning activity targeting the perimeter
- Detected high-volume internal scanning activity (2,276 events)
- Classified horizontal and vertical scanning patterns
- Identified specific scan techniques (Ping Sweep and TCP SYN Scan)
- Used Kibana to validate findings and explore logs interactively

## 🔎 Key Detections
- **External Scanning**: IP `203.0.113.25` performing reconnaissance against internal assets
- **Internal Scanning (High Severity)**: 2,276 scanning events in `log-session-2.csv` — strong indicator of potential compromised host inside the network
- **Horizontal Scan**: Activity across the `203.0.113.0/24` range (same port scanned on multiple hosts)
- **Vertical Scan**: Targeted enumeration against single host `192.168.230.145`
- **Targeted Ports**: `80, 445, 3389` (HTTP, SMB, RDP — commonly exploited services)
- **Ping Sweep**: Subnet-wide host discovery from `192.168.230.127`
- **TCP SYN Scan**: Stealth scanning with `conn_state = S0`

## 🛠 Tools & Techniques Used
- Terminal log analysis (`head`, `cut`, `wc`)
- Column extraction from malformed CSV data
- Pattern recognition and behavioral analysis
- Kibana for interactive log exploration and validation

## 🔎 Evidence – Investigation Screenshots

### 1. Internal Scanning Log File (`log-session-2.csv`)
<img width="1366" height="724" alt="image" src="https://github.com/user-attachments/assets/e36cdc2d-9887-4f48-a8f8-5001e09b291f" />


### 2. Internal Scanning Event Count (2,276 entries)
<img width="1366" height="729" alt="image" src="https://github.com/user-attachments/assets/18838d1f-51de-40f7-a757-2f2d8489475c" />


### 3. External Scanning IP Identification
<img width="1366" height="726" alt="image" src="https://github.com/user-attachments/assets/56060489-fd6f-4e4f-8931-0b35dfcbdc2f" />


### 4. Horizontal Scan Range (`203.0.113.0/24`)
<img width="1366" height="722" alt="image" src="https://github.com/user-attachments/assets/6a7c83bd-4721-4fd5-ad8c-a4a7755e04e6" />


### 5. Vertical Scan Target (`192.168.230.145`)
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/a25c1b3b-488a-47df-9648-9c5954b2ab0b" />


### 6. Targeted Ports on Scanned Host
<img width="1366" height="728" alt="image" src="https://github.com/user-attachments/assets/737a8b40-52cc-43f3-baf3-135e47128acc" />


### 7. Ping Sweep Source (`192.168.230.127`)
<img width="1366" height="722" alt="image" src="https://github.com/user-attachments/assets/9780d2d7-b16a-4181-b527-e8855ba3fdf6" />


### 8. TCP SYN Scan Detection (`conn_state = S0`)
<img width="1366" height="726" alt="image" src="https://github.com/user-attachments/assets/dd459281-8187-47b0-b675-0bd11e42f570" />


## 📌 SOC Insights
Network discovery is typically the **earliest observable stage** of an attack.  
This lab reinforced how critical it is to:
- Quickly differentiate external reconnaissance from internal lateral scanning
- Recognize that internal scanning is high severity (indicates potential foothold)
- Use simple CLI tools to analyze raw, unstructured logs effectively

**Hands-on experience detecting network discovery techniques** — practical skills for SOC Analyst and Threat Hunting roles.

Full investigation with screenshots and detailed analysis is available in this repository.

Feel free to fork, star, or reach out with questions. Open to feedback!

**Completed:** April 2026

MIT License – see the [LICENSE](LICENSE) file for details.
