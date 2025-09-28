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
- **What:** Compiled inventory (manufacturer, model, firmware, MAC, connectivity).  
- **Why:** Helps identify possible attack vectors.  
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
1. <img width="521" height="296" alt="image" src="https://github.com/user-attachments/assets/3b1e3a22-dded-4692-918e-59c25fe9dc9a" />
  Fig 4.1.1 Scan for open ports
2. <img width="515" height="286" alt="image" src="https://github.com/user-attachments/assets/46bf052d-5d57-4be2-b947-289fadaf3ab8" />
  Fig 4.1.2 Nmap basic scan
3. <img width="518" height="296" alt="image" src="https://github.com/user-attachments/assets/0fcc7c8e-d2da-42b2-9517-ab7d3388474d" />
  Fig 4.1.3 Version detection scan
4. <img width="380" height="439" alt="image" src="https://github.com/user-attachments/assets/dbbc1034-260c-412c-81f1-3a3d32e33fb8" />
  Fig 4.1.4 Scan for known vulnerabilities
5. <img width="576" height="283" alt="image" src="https://github.com/user-attachments/assets/431ccfab-1a65-4fc5-a6b3-19f30964d986" />
  Fig 4.1.5 Aggressive scan
  
6. <img width="975" height="221" alt="image" src="https://github.com/user-attachments/assets/2b5ab257-8784-46ff-b5e8-b0eee71958d9" />

7. <img width="528" height="457" alt="image" src="https://github.com/user-attachments/assets/a726a3ad-d3f9-415e-8de7-5f87146921a2" />

8. <img width="975" height="327" alt="image" src="https://github.com/user-attachments/assets/33715e51-4b1c-4a5c-bb3d-7c7119b7f979" />

9. <img width="595" height="399" alt="image" src="https://github.com/user-attachments/assets/d96e14a9-2b76-4f10-b384-5068e31069cc" />

10. <img width="975" height="175" alt="image" src="https://github.com/user-attachments/assets/ec74ae00-5cd0-40ec-92b3-cc486bab6c78" />

11. <img width="986" height="439" alt="image" src="https://github.com/user-attachments/assets/d73522d1-d4ce-4cd3-8504-4dfb2e460370" />

12. <img width="975" height="442" alt="image" src="https://github.com/user-attachments/assets/18555e8d-963b-4acf-9f68-4ad44f156b2b" />

13. <img width="487" height="487" alt="image" src="https://github.com/user-attachments/assets/57dd7ec7-27dc-49fe-bbd2-16f050e7cb9c" />

14. <img width="909" height="701" alt="image" src="https://github.com/user-attachments/assets/10591876-c4b4-4a6a-b554-3b01556fd3ce" />

15. <img width="975" height="217" alt="image" src="https://github.com/user-attachments/assets/df5cad0d-e549-4499-8858-3043b0a53061" />

16. <img width="975" height="319" alt="image" src="https://github.com/user-attachments/assets/bd0f982c-15b6-487f-8afb-0a9ce0556d30" />

17.<img width="975" height="240" alt="image" src="https://github.com/user-attachments/assets/47ae7746-ef34-4f74-ab66-c146eb903a29" />

18. <img width="920" height="438" alt="image" src="https://github.com/user-attachments/assets/2b54499f-1307-49ee-87cb-a968585e1e04" />

19. <img width="975" height="252" alt="image" src="https://github.com/user-attachments/assets/40732023-d09e-428b-8419-ed31f07c05ef" />

20. <img width="975" height="242" alt="image" src="https://github.com/user-attachments/assets/3130cb52-8734-49a9-84dc-e1ed716aa33f" />

21. <img width="975" height="240" alt="image" src="https://github.com/user-attachments/assets/be9c2f05-e42f-4a68-accb-9739276effbc" />

22. <img width="975" height="325" alt="image" src="https://github.com/user-attachments/assets/9a720db6-5086-4679-881e-0693bb7a45df" />

23. <img width="941" height="491" alt="image" src="https://github.com/user-attachments/assets/f1f4a3c8-83d8-4a17-a379-0ad09a40ea69" />






### 3. Traffic analysis (Wireshark)
- **Objective:** Capture traffic to detect plaintext transmissions, DNS leaks, cloud endpoints.  
- **Approach:** Monitor mode / port mirroring, apply protocol filters, capture during boot/pairing/operation.  
- **Findings:** Some mDNS traffic visible; no HTTP plaintext for most devices.  
- **Deliverable:** .pcap files and screenshots.
- 
<img width="568" height="319" alt="image" src="https://github.com/user-attachments/assets/29f500fc-04f3-4b2d-b150-803dce6b3cc4" />
Fig 4.1.6 Wireshark Packet capturing
<img width="553" height="311" alt="image" src="https://github.com/user-attachments/assets/3fa5fba9-ef96-4ef0-970c-6971756cc6c6" />
Fig 4.1.7 Wireshark Analysis
<img width="831" height="414" alt="image" src="https://github.com/user-attachments/assets/22108184-6953-48af-a00a-aca0ad05317f" />
<img width="644" height="363" alt="image" src="https://github.com/user-attachments/assets/e619b1b0-5248-4f75-9f57-6fd44ab1d6e8" />
<img width="667" height="429" alt="image" src="https://github.com/user-attachments/assets/516ded08-95f8-4ca6-949c-32edc02107f6" />
Fig 4.2.8 Capturing SSID and Channel Number Using Wireshark
<img width="644" height="313" alt="image" src="https://github.com/user-attachments/assets/4ef377c4-759d-45cb-aa05-85282c6f0127" />
Fig 4.2.9 Deauthentication Attack Traffic Captured in Wireshark
<img width="975" height="394" alt="image" src="https://github.com/user-attachments/assets/11ec42ed-38a5-473d-8672-10246d5220a4" />
<img width="975" height="450" alt="image" src="https://github.com/user-attachments/assets/89b55208-9552-4795-b798-1ecd97665ea3" />
<img width="975" height="477" alt="image" src="https://github.com/user-attachments/assets/8d94dd10-c9a5-4b61-8ff3-15aa51b6e496" />
<img width="975" height="565" alt="image" src="https://github.com/user-attachments/assets/d5964cd2-99f1-4247-a8dd-ce1282893bc8" />


### 4. Wireless & protocol attacks (Aircrack-ng suite)
- **Objective:** Test WPA security via handshake capture and dictionary attack.  
- **Steps:**  
  - `airmon-ng start wlan0`  
  - `airodump-ng wlan0mon`  
  - `aireplay-ng --deauth 10 -a <BSSID> -c <CLIENT> wlan0mon`  
  - `aircrack-ng -w rockyou.txt capture.cap`  
- **Result:** Strong passwords resisted cracking.  
- **Deliverable:** Handshake captures + logs.

<img width="484" height="339" alt="image" src="https://github.com/user-attachments/assets/f56f7412-7357-4e70-95d7-eb13bd615c77" />
Fig 4.1.10 Wireshark Capture Showing Unsuccessful WPA/WPA2 Handshake Crack Attempt
<img width="484" height="339" alt="image" src="https://github.com/user-attachments/assets/1b145f60-6eef-4b43-85f0-27619e05266a" />
<img width="458" height="128" alt="image" src="https://github.com/user-attachments/assets/0ad7562a-da08-45ad-b79e-65af217d68e5" />
<img width="625" height="100" alt="image" src="https://github.com/user-attachments/assets/0ed11c8e-4875-4ff6-84f5-0b7173378d63" />


### 5. Reverse engineering (JADX GUI)
- **Objective:** Analyze Android companion apps for hardcoded secrets.  
- **Process:** Load APK → inspect strings, network calls, API keys.  
- **Findings:** Apps obfuscated; some insecure endpoints possible.  
- **Deliverable:** Decompiled snippets + recommendations.

<img width="476" height="395" alt="image" src="https://github.com/user-attachments/assets/462eeabf-fb7b-45f5-b371-9079c1343779" />
Fig 4.1.11 JADX GUI Analysis
<img width="480" height="422" alt="image" src="https://github.com/user-attachments/assets/cceb6f92-e3b0-47d7-bbd4-7fa7364c37d2" />
Fig 4.1.12 Obfuscated or Unreadable Code in JADX-GUI

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
