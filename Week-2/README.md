# PENETRATION TESTING REPORT

**Footprinting & Network Scanning Phases**  
**W2-PM-FINAL | CYBERSECURITY | NETWORKWALKS**

| Field | Detail |
| :--- | :--- |
| **Pentester Name** | France Kisembo |
| **Program / Batch** |  B082-Networkwalks|
| **Date** | 15 November 2026 |
| **Modules Completed** | W2-PM4 (theHarvester Footprinting), W2-PM5 (Zenmap Network Scanning) |

---

## 1. Executive Summary & Authorization
This report documents passive footprinting and active local network discovery conducted for Week 2 of the NetworkWalks Cybersecurity Internship. All testing activities were strictly non-destructive and performed within authorized boundaries:
* **Authorized Scope:** Public OSINT reconnaissance on `microsoft.com` and active host discovery on the tester's authorized local area network (`192.168.52.0/24`).
* **Prohibited Activities:** No exploitation, brute-force attacks, denial-of-service testing, or unauthorized access attempts were performed.

---

## 2. Module W2-PM4: Footprinting & Reconnaissance with theHarvester

### 2.1 Methodology & Commands Executed
Using `theHarvester v4.7.0`, passive open-source intelligence (OSINT) gathering was executed against `microsoft.com` to enumerate publicly indexed hosts, IP addresses, and email contacts:

* **Task 1 (Baidu Search Engine, Limit 1000):**
  ```bash
  python theHarvester.py -d microsoft.com -l 1000 -b baidu
  ```
* **Task 2 (Multi-Source Public OSINT Scan, Limit 50):**
  ```bash
  python theHarvester.py -d microsoft.com -l 50 -b crtsh,certspotter,hackertarget,rapiddns,urlscan,yahoo -f task2_results
  ```

### 2.2 Findings & Artifacts
* **Task 1 Findings:** Executed passive search across Baidu (`-l 1000`); search engine rate-limiting returned `0` exposed emails, `0` hosts, and `0` IPs. Output archived in `task1_baidu_output.txt`.
* **Task 2 Findings:** Executed multi-engine OSINT queries across Certificate Transparency logs (`crtsh`, `certspotter`), DNS aggregators (`hackertarget`, `rapiddns`), and web scanners (`urlscan`, `yahoo`). Structured XML and JSON reports were generated and saved (`task2_results.xml` and `task2_results.json`).
* **Evidence:** See `screenshots/w2_pm4_theharvester_task1.png` and `screenshots/w2_pm4_theharvester_task2.png`.

---

## 3. Module W2-PM5: Network Scanning with Zenmap

### 3.1 Local Network Configuration (Tasks 1–2)
Following the installation of Nmap/Zenmap, host network parameters were identified via `ipconfig /all`:
* **Host Machine:** `DESKTOP-JDMVDF`
* **Local IPv4 Address:** `192.168.52.211`
* **Subnet Mask:** `255.255.255.0` (`/24`)
* **Target LAN Subnet:** `192.168.52.0/24`

### 3.2 Host Discovery & Topology Findings (Tasks 3–7)
A network discovery scan was performed across all 256 addresses in `192.168.52.0/24` using Zenmap:
* **Total Live Hosts Discovered:** **2 hosts**

| Host IP Address | MAC Address | Role / Device Description |
| :--- | :--- | :--- |
| `192.168.52.140` | `DE-BF-41-A4-23-90` | Default Gateway / Local Router |
| `192.168.52.211` | `D4-D2-52-53-CD-BB` | Local Windows Testing Workstation |

* **Evidence & Artifacts:**
  * Network topology exported in PDF format: `Zenmap_Topology.pdf`
  * Scan & topology screenshots saved in `screenshots/w2_pm5_zenmap_scan.png` and `screenshots/w2_pm5_zenmap_topology.png`

---

## 4. Recommendations & Conclusion
* **Minimize Public OSINT Exposure:** Regularly audit Certificate Transparency logs and DNS records to ensure internal or staging subdomains are not unnecessarily exposed to passive reconnaissance tools like `theHarvester`.
* **Network Segmentation & Monitoring:** Maintain MAC-address inventory and DHCP monitoring on local subnets (`192.168.52.0/24`) to quickly detect unauthorized or rogue devices connecting to the LAN.
