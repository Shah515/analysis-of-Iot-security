# analysis-of-Iot-security
Security analysis of IoT devices (Smart TVs &amp; CCTV cameras) using tools like Nmap, Wireshark, Aircrack-ng &amp; JADX GUI. Conducted vulnerability scanning, traffic monitoring, wireless attacks, and app reverse engineering to identify risks &amp; propose mitigation measures.
# Analysis of IoT Security 🔐

This repository contains the project **"Analysis of Security of IoT Devices"** 
submitted as part of the **Master of Science in Forensic Science (IV Semester)** at **Kristu Jayanti College, Bangalore**.  
Author: *Shahrukh Khan (23MFOR31)*  
Guide: *Mr. Don Caeiro, Assistant Professor*  

---
## Abstract
Internet of Things (IoT) has been considered of great importance in technical and social fields due to the desire of smart living and intelligent solutions for industrial operations, home automation and healthcare. The telecommunication networks give all-time internet connectivity for the devices in physical systems and hand-held devices. The IoT has gotten too much research attention in recent years and is seen as the internet's future. IoT will play a critical role in the future, transforming our lifestyles, standards, and business methods.  

In the coming years, the use of IoT in different types of applications is likely to rise. In this context, artificial intelligence (AI) is becoming an important technique for increasing the security of IoT devices. This provides a better understanding of how AI may support cybersecurity in the IoT ecosystem. In the world of information technology, cybersecurity is critical. IoT activities are autonomous and support dynamic Machine-to-Machine (M2M) communication, which also creates risks. Therefore, this project analyses vulnerabilities in IoT devices (Smart TVs, CCTV cameras, etc.) using tools like **Nmap, Wireshark, Aircrack-ng, and JADX GUI**, focusing on vulnerability scanning, traffic monitoring, wireless attacks, and app reverse engineering to propose mitigation strategies.

## 🌐 Introduction
The **Internet of Things (IoT)** is a rapidly growing ecosystem of interconnected devices that communicate and exchange data via the internet. From smart homes and wearable devices to industrial automation and healthcare, IoT has penetrated nearly every sector.  

However, this innovation comes at a cost: IoT devices are often deployed with **weak authentication, unpatched firmware, and insecure communication channels**. Real-world incidents such as the **Mirai Botnet (2016)** and the **Oldsmar Water Treatment Hack (2021)** highlight the potential dangers.  

This project investigates the **security posture of common IoT devices** through penetration testing techniques, focusing on vulnerabilities, risks, and mitigation strategies.

---

## 📚 Review of Literature
Previous studies have highlighted critical IoT security concerns:

1. **Mirai Botnet – Krebs (2016)**  
   - Millions of IoT devices hijacked using default credentials.  
   - Caused massive DDoS on DynDNS, disrupting services like Twitter and Netflix.  
   - **Lesson:** Weak authentication can weaponize IoT at scale.  

2. **Firmware vulnerabilities – Roman et al. (2013)**  
   - IoT firmware often outdated and exploitable.  
   - Risks include code injection and data theft.  
   - **Lesson:** Firmware patching and secure design are essential.  

3. **IoT threats & frameworks – Alaba et al. (2017)**  
   - Classified IoT attacks (device, network, application-level).  
   - Suggested layered security frameworks.  
   - **Lesson:** Threat modeling helps guide testing methodologies.  

4. **Critical infrastructure attack – CISA (2021)**  
   - Hackers tried to poison public water via IoT systems.  
   - **Lesson:** IoT insecurities can directly endanger human life.  

5. **Cost of IoT breaches – IBM (2023)**  
   - IoT-related breaches cost higher than standard breaches.  
   - **Lesson:** Economic and reputational stakes are high.  

---

## ⚙️ Methodology
A **practical penetration-testing approach** was applied to 12 real-world IoT devices (smart plugs, bulbs, TVs, CCTV, smart speaker, smartwatch). Testing remained ethical and non-destructive.

### 1. Device selection & information gathering
- **Kya kiya:** Compiled inventory (manufacturer, model, firmware, MAC, connectivity).  
- **Kyon zaroori:** Helps identify possible attack vectors.  
- **Deliverable:** Device info table.  

### 2. Network scanning (Nmap)
- **Objective:** Discover open ports, services, versions, CVEs, IoT protocols.  
- **Commands:**  
  - `nmap -Pn -sS -p 1-1000 <ip>` (basic scan)  
  - `nmap -Pn -sV -p- <ip>` (service detection)  
  - `nmap --script vuln -p- <ip>` (vuln scan)  
  - `nmap -A <ip>` (aggressive scan)  
- **Expected findings:** Open/filtered ports, Avahi/mDNS exposure.  
- **Deliverable:** Per-device Nmap reports.
  <img width="521" height="296" alt="image" src="https://github.com/user-attachments/assets/3b1e3a22-dded-4692-918e-59c25fe9dc9a" />

### 3. Traffic analysis (Wireshark)
- **Objective:** Capture traffic to detect plaintext transmissions, DNS leaks, cloud endpoints.  
- **Approach:** Monitor mode / port mirroring, apply protocol filters, capture during boot/pairing/operation.  
- **Findings:** Some mDNS traffic visible; no HTTP plaintext for most devices.  
- **Deliverable:** .pcap files and screenshots.  

### 4. Wireless & protocol attacks (Aircrack-ng suite)
- **Objective:** Test WPA security via handshake capture and dictionary attack.  
- **Steps:**  
  - `airmon-ng start wlan0`  
  - `airodump-ng wlan0mon`  
  - `aireplay-ng --deauth 10 -a <BSSID> -c <CLIENT> wlan0mon`  
  - `aircrack-ng -w rockyou.txt capture.cap`  
- **Result:** Strong passwords resisted cracking.  
- **Deliverable:** Handshake captures + logs.  

### 5. Reverse engineering (JADX GUI)
- **Objective:** Analyze Android companion apps for hardcoded secrets.  
- **Process:** Load APK → inspect strings, network calls, API keys.  
- **Findings:** Apps obfuscated; some insecure endpoints possible.  
- **Deliverable:** Decompiled snippets + recommendations.  

### 6. Firmware acquisition & analysis
- **Objective:** Extract firmware from vendor/OTA for analysis.  
- **Methods:** Vendor site download, OTA capture, serial/JTAG.  
- **Challenges:** Most firmware encrypted or proprietary.  
- **Deliverable:** Firmware images (if available), CVE matches.  

### 7. Documentation & recommendations
- **Documentation:** Findings, risk levels (Low/Medium/High).  
- **Recommendations:**  
  - Unique credentials  
  - TLS for communication  
  - OTA patching  
  - Disable unused services  
- **Deliverable:** Consolidated risk report.  

---

## 📊 Results and Analysis
1. **Port Security**  
   - Most devices blocked common ports → smaller attack surface.  
   - Nmap results showed limited exposure.  

2. **Service Exposure**  
   - Some devices broadcast mDNS/Avahi.  
   - Could allow reconnaissance/DoS.  

3. **Wireless Security**  
   - WPA handshake captured but not cracked.  
   - Strong passwords provided resilience.  

4. **App Security**  
   - Companion apps obfuscated.  
   - Risk of hardcoded API keys remains.  

5. **Firmware Analysis**  
   - Most firmwares encrypted / inaccessible.  
   - Limited internal analysis possible.  

---

## 💡 Discussion
- **Default credentials** remain a recurring issue in IoT.  
- **Unencrypted traffic** like mDNS still risks information leakage.  
- **Limited patching** leaves devices open to known exploits.  
- **Scale factor:** Even small vulnerabilities can snowball into massive botnets.

These findings confirm that **manufacturers prioritize usability and cost over security**. Literature and case studies show a persistent global challenge.

---

## 🏁 Conclusion
IoT is transforming industries but remains a **weak link in cybersecurity**.  

### Key conclusions:
1. IoT devices must enforce **strong, unique authentication**.  
2. **TLS/SSL encryption** must be mandatory.  
3. **Regular OTA firmware updates** should be enforced.  
4. Governments must create **global IoT security standards**.  
5. Users should be educated to change defaults and follow security hygiene.  

If these measures are implemented, IoT can evolve into a **secure, reliable, and trusted ecosystem**.

---

## 📌 References
- Ashton, K. (1999). *Origin of IoT concept*.  
- Krebs, B. (2016). *Mirai Botnet attack*.  
- Roman, R., Zhou, J., & Lopez, J. (2013). *IoT firmware vulnerabilities*.  
- Sicari, S. et al. (2015). *IoT security frameworks*.  
- Alaba, F. A. et al. (2017). *IoT threats and frameworks*.  
- CISA (2021). *Florida water treatment hack*.  
- IBM (2023). *Cost of Data Breach Report*.  
- Yu, W. et al. (2020). *IoT Vulnerability Analysis*.  
- Han, J. et al. (2024). *Security challenges in IoT ecosystems*.  

*(Full reference list available in research document)*  

---

## 🎓 Academic Info
Submitted to:  
**Department of Forensic Science, Kristu Jayanti College (Autonomous)**  
K. Narayanapura, Bangalore – 560077  
**May 2025**
