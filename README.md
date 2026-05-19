# 🚨 SOC Alert Detection Lab using Splunk

![Tool](https://img.shields.io/badge/Tool-Splunk-FF6600?style=for-the-badge&logo=splunk&logoColor=white)
![Type](https://img.shields.io/badge/Type-SOC%20Alert%20Triage-blue?style=for-the-badge)
![MITRE](https://img.shields.io/badge/MITRE-T1059%20%7C%20T1053-red?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

> **Simulated SOC alert triage workflow** — ingested Linux system logs into Splunk, built SPL queries to analyze kernel activity, identify top log sources, map host behavior, and visualize event timelines to detect anomalous system patterns.

---

## 🎯 Objective

SOC analysts don't just investigate network attacks — they monitor system-level activity for signs of malware execution, privilege escalation, and unauthorized system changes. This lab replicates that workflow using real Linux system logs and Splunk SIEM.

---

## 🛠️ Tools & Environment

| Component | Details |
|---|---|
| **SIEM Platform** | Splunk Enterprise (Free Trial) |
| **Log Source** | Linux System Logs (`Linux_2k.log.txt`) |
| **Log Type** | Kernel, CRON, SSH, System events |
| **Query Language** | SPL (Search Processing Language) |
| **Focus** | System activity monitoring & alert triage |

---

## 📋 Investigation Methodology

### Phase 1 — Log Ingestion
```
Splunk → Settings → Add Data → Upload
→ File: Linux_2k.log.txt
→ Source type: linux_syslog
→ Index: main
```

### Phase 2 — SPL Queries Built

**Query 1 — Kernel activity analysis (detect driver/hardware anomalies):**
```spl
index=main kernel
```

**Query 2 — Identify top log sources (find noisiest systems):**
```spl
index=main
| top source
```

**Query 3 — Host activity breakdown:**
```spl
index=main
| stats count by host
```

**Query 4 — Event timeline visualization:**
```spl
index=main
| timechart count
```

**Query 5 — CRON job monitoring (detect scheduled task abuse):**
```spl
index=main CRON
| stats count by host
| sort -count
```

**Query 6 — SSH event monitoring:**
```spl
index=main sshd
| stats count by host
```

---

## 🔍 Key Findings

| # | Finding | Severity | Implication |
|---|---|---|---|
| 1 | Kernel generating highest event volume | 🟡 Medium | System-level activity spike — investigate driver errors |
| 2 | Single host generating 80%+ of logs | 🟡 Medium | Potential misconfiguration or active compromise |
| 3 | CRON activity detected at irregular intervals | 🟠 High | Possible scheduled task abuse (T1053) |
| 4 | Spike in events at specific time window | 🔴 High | Off-hours automated activity — investigate source |

---

## 🛡️ MITRE ATT&CK Mapping

| Tactic | Technique | ID | Evidence |
|---|---|---|---|
| Execution | Command and Scripting Interpreter | T1059 | Shell activity in kernel logs |
| Persistence | Scheduled Task/Job: Cron | T1053.003 | Irregular CRON entries detected |
| Discovery | System Information Discovery | T1082 | Host enumeration via log analysis |

---

## 📸 Investigation Screenshots

> Screenshots in `/screenshots` folder:
> - `splunk-kernel-activity.png` — Kernel event analysis
> - `splunk-top-log-sources.png` — Top log source identification
> - `splunk-host-activity-analysis.png` — Host activity breakdown
> - `splunk-event-timeline.png` — Event timeline visualization

---

## 💡 Skills Demonstrated

- ✅ Splunk log ingestion (syslog format)
- ✅ Kernel & system event analysis
- ✅ SPL: top, stats, timechart commands
- ✅ Alert triage prioritization
- ✅ MITRE ATT&CK T1053 & T1059 mapping
- ✅ SOC Level 1 alert workflow simulation

---

## 🔗 Related Projects

| Project | Description |
|---|---|
| [Splunk SOC Incident Investigation](https://github.com/vivek-sh45/splunk-soc-incident-investigation) | Brute-force detection via auth logs |
| [Threat Hunting Lab](https://github.com/vivek-sh45/threat-hunting-lab) | Proactive threat hunting with Wireshark |
| [Nmap Vulnerability Scan Lab](https://github.com/vivek-sh45/nmap-vulnerability-scan-lab) | Network reconnaissance & port scanning |

---

## 👤 Author

**Vivek Sharma** — Cybersecurity Analyst (Fresher) | SOC Operations

[![LinkedIn](https://img.shields.io/badge/LinkedIn-vivek--sharma--cybersec-0077B5?style=flat&logo=linkedin)](https://linkedin.com/in/vivek-sharma-cybersec)
[![GitHub](https://img.shields.io/badge/GitHub-vivek--sh45-181717?style=flat&logo=github)](https://github.com/vivek-sh45)
[![Email](https://img.shields.io/badge/Email-thecybervivek@gmail.com-D14836?style=flat&logo=gmail)](mailto:thecybervivek@gmail.com)
