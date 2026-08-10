# Wireshark-SOC-analyst-investigation-project

#  Home SOC Lab — Threat Detection & Incident Response

![Status](https://img.shields.io/badge/Status-Complete-success)
![Platform](https://img.shields.io/badge/Platform-Splunk%20%7C%20Suricata%20%7C%20Sysmon-blue)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE%20ATT%26CK-5%20Techniques-orange)
![IR Reports](https://img.shields.io/badge/IR%20Reports-3%20Complete-green)


A fully operational Security Operations Center built from scratch to demonstrate end-to-end threat detection, investigation, and incident response capabilities.
Built by Sabelo Eugene Moyo 

---
 <h1>🎯 Project Overview</h1>
This project showcases practical SOC analyst skills through a complete security operations environment. I built a multi-platform SOC lab using industry-standard tools (Splunk, Suricata IDS, Sysmon) to detect, investigate, and document real-world attack scenarios mapped to the MITRE ATT&CK framework.

## Why This Project Matters:

- Demonstrates hands-on experience with SIEM platforms, not just theoretical knowledge
- Shows ability to write custom detection rules and investigate security incidents
- Proves capability to document findings in professional incident response reports
- Validates understanding of adversary tactics, techniques, and procedures (TTPs)

---
  <h1>🏗️ Architecture</h1>
<h2>Environment Overview</h2>


| Component          | Technology                     | Purpose                                         |
|--------------------|--------------------------------|-------------------------------------------------|
| **SIEM**           | Splunk Enterprise 9.2          | Central log aggregation, correlation, alerting  |
| **Network IDS**    | Suricata                       | Network traffic monitoring, signature detection |
| **Windows Telemetry** | Sysmon (SwiftOnSecurity config) | Process creation, network connections, file events |
| **Linux Telemetry** | auditd                        | System call auditing, security events           |
| **Attack Platform** | Kali Linux                    | Adversary simulation and penetration testing    |
| **Virtualization** | VirtualBox 7.0                 | Isolated lab environment                        |


## Steps
<p align="center">
1.downloading VirtualBox: <br/>
<br />
<img src="https://imgur.com/2UZ6YkM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
2.Running installer with default settings: <br/>
<br />
<img src="https://imgur.com/XPaEZmd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
3.creating the lab virtual network: <br/>
<br />
<img src="https://imgur.com/JvvWWGK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
4.downloading the ubuntu server ISO image: <br/>
<br />
<img src="https://imgur.com/N7W8qMY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
5.downloading kali linux ISO image: <br/>
<br />
<img src="https://imgur.com/Ny6rtAk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
6. Downloading Windows 11 enterprise ISO image: <br/>
<br />
<img src="https://imgur.com/PtYClso.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
7.1 Creating the Splunk VM: <br/>
<br />
<img src="https://imgur.com/FUQJ7uj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
7.2 Creating the Splunk VM: <br/>
<br />
<img src="https://imgur.com/7bSNP1l.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
7.3 Creating the Splunk VM: <br/>
<br />
<img src="https://imgur.com/07AJj2W.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
7.4 Creating the Splunk VM: <br/>
<br />
<img src="https://imgur.com/sFtSsq9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
7.5 Creating the Splunk VM (Network Adapter).png: <br/>
<br />
<img src="https://imgur.com/TvAgDUr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
8.0  Boot the VM and walk through the Ubuntu Server installation using default options..png: <br/>
<br />
<img src="https://imgur.com/VObTAdv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
8.1 choosing ubuntu server installation type.png: <br/>
<br />
<img src="https://imgur.com/XxLZlBR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
8.2 ubuntu server network configuration and DHCP address.png : <br/>
<br />
<img src="https://imgur.com/VIm2ov3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
8.3 ubuntu server storage configuration.png: <br/>
<br />
<img src="https://imgur.com/86msWET.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
8.4 ubuntu server profile configuration.png: <br/>
<br />
<img src="https://imgur.com/erR8CBk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
8.5 ubuntu server installing.png: <br/>
<br />
<img src="https://imgur.com/LJ6heHt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
9.1 intial ubuntu configuration.png : <br/>
<br />
<img src="https://imgur.com/1XHgs6s.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
9.2 updating system .png: <br/>
<br />
<img src="https://imgur.com/9QRmN03.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
9.3 server ip address.png: <br/>
<br />
<img src="https://imgur.com/NTZSmlf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
9.4 issues downloading splunk.png: <br/>
<br />
<img src="https://imgur.com/3Hp07WK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
9.5 installing wget, curl and ping.png: <br/>
<br />
<img src="https://imgur.com/vwJc4wS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
9.6 successfully downloading splunk after troubleshooting.png: <br/>
<br />
<img src="https://imgur.com/wzqGUH4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
9.7 installing the package and setting username and password.png: <br/>
<br />
<img src="https://imgur.com/JXLK8b0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
9.8 enabling splunk to start at boot.png: <br/>
<br />
<img src="https://imgur.com/SDbfe7c.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
10. accessing splunk web UI.png: <br/>
<br />
<img src="https://imgur.com/WfULw3f.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br /
 
<p align="center">
10.1 creating windows log index on splunk web UI.png: <br/>
<br />
<img src="https://imgur.com/Us7hdnP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
10.2 creating linux log index in splunk web UI.png: <br/>
<br />
<img src="https://imgur.com/Lt71lEC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
10.3 creating suricata log index in splunk web UI.png: <br/>
<br />
<img src="https://imgur.com/Tn2SLBk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
10.4 creating firewall log index in splunk web UI.png: <br/>
<br />
<img src="https://imgur.com/nrmitXC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
11.1 windows11 configuration.png: <br/>
<br />
<img src="https://imgur.com/tWCxu29.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
11.creating windows 11 victim machine.png: <br/>
<br />
<img src="https://imgur.com/99kiDu1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
12.0 installing windows 11 victim machine.png: <br/>
<br />
<img src="https://imgur.com/psF5ERv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
12.1 Win11 ip address.png: <br/>
<br />
<img src="https://imgur.com/XAW7eAq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
12.2 fixing DNS resolution in Windows VM.png: <br/>
<br />
<img src="https://imgur.com/XpPOB1n.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
12.3 Manualling configuring Windows VM DNS.png: <br/>
<br />
<img src="https://imgur.com/XpPOB1n.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
12.4 Pinging google to verify if DNS resolution worked.png.png: <br/>
<br />
<img src="https://imgur.com/BltxX8S.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
12.5 pulling the official Sysmon package from Microsoft Sysinternals..png: <br/>
<br />
<img src="https://imgur.com/VHF86Sh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
12.6 installing sysmon.png: <br/>
<br />
<img src="https://imgur.com/iekudHq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
12.7 confirming if Sysmon is running.png : <br/>
<br />
<img src="https://imgur.com/gCroYbM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
12.8 downloading splunk universal forwarder.png: <br/>
<br />
<img src="https://imgur.com/aRAiLa6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
12.9 running installer.png: <br/>
<br />
<img src="https://imgur.com/o8F5jOc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
12.10 post installation configuration.png: <br/>
<br />
<img src="https://imgur.com/1xJEpr1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
12.11  Configuring Log Collection (inputs.conf).png: <br/>
<br />
<img src="https://imgur.com/LESVH1o.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
12.12 confirming windows index in splunk.png: <br/>
<br />
<img src="https://imgur.com/XaZEONd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
13.0 downloading Ubuntu Desktop ISO.png: <br/>
<br />
<img src="https://imgur.com/5IFwnNW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
13.1 creating ubuntu vm.png: <br/>
<br />
<img src="https://imgur.com/vzb2ZPV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
13.2 downloading splunk universal forwarder on ubuntu vm.png: <br/>
<br />
<img src="https://imgur.com/il6Expv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
13.3 installing splunk universal forwarder.png: <br/>
<br />
<img src="https://imgur.com/kRxnjOm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
13.4 pointing the forwarder to my splunk server.png: <br/>
<br />
<img src="https://imgur.com/6vgUJXY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />

<p align="center">
13.5 adding log sources .png: <br/>
<br />
<img src="https://imgur.com/W9krzAV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
13.6  Enabling Auditd for Enhanced Linux Logging .png: <br/>
<br />
<img src="https://imgur.com/4tNzAiN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
14.1 installing Suricata on Splunk server VM.png: <br/>
<br />
<img src="https://imgur.com/5TdJGqH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
14.2 configuring suricata on the splunk server vm.png: <br/>
<br />
<img src="https://imgur.com/MQzsdqq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
14.3 starting and enabling suricata.png: <br/>
<br />
<img src="https://imgur.com/boyJUx1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<p align="center">
14.4 configuring inputs.conf so Splunk reliably ingests Suricata logs every time it starts.png: <br/>
<br />
<img src="https://imgur.com/wAho32l.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
