Wireshark SOC Investigations — Malware, Reconnaissance & DNS Exfiltration Analysis


![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)
![Platform](https://img.shields.io/badge/Platform-Wireshark-1679A7)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE%20ATT%26CK-5%20Techniques-orange)
![IR Reports](https://img.shields.io/badge/IR%20Reports-3%20Complete-green)


A packet-level investigation portfolio built to demonstrate SOC Tier 1 analyst skills across three distinct attack categories, using the same Alert → Filter → Inspect → Correlate → Document process a real analyst follows on a live alert.

Built by Sabelo Moyo

---
 <h1>🎯 Project Overview</h1>
This project analyzes real (safely sourced) packet captures to investigate three genuinely different categories of SOC incident: a malware infection with command-and-control beaconing, a network reconnaissance and brute-force intrusion attempt, and a DNS tunneling exfiltration channel. Each investigation starts from a written alert scenario, not a blank pcap and ends in a formal incident report mapped to MITRE ATT&CK.

## Why This Project Matters:

- Demonstrates hands-on packet analysis skills, not just filter syntax memorized from a cheat sheet
- Shows the ability to tell a real threat apart from background noise across three different traffic shapes
- Proves the ability to document findings in a professional, audience-ready incident response format
- Validates understanding of adversary TTPs across delivery, reconnaissance, and exfiltration stages, not just one attack type

---
  <h1>🏗️ Investigation Types</h1>

<table>
  <thead>
    <tr>
      <th>#</th>
      <th>Investigation Type</th>
      <th>What It Simulates</th>
      <th>Source</th>
      <th>MITRE ATT&CK</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td><strong>Malware Delivery & C2 Beaconing</strong></td>
      <td>An infected endpoint downloading a payload and checking in with external infrastructure on a schedule</td>
      <td>malware-traffic-analysis.net</td>
      <td>T1105, T1071</td>
    </tr>
    <tr>
      <td>2</td>
      <td><strong>Network Reconnaissance & Brute-Force</strong></td>
      <td>Port scanning and repeated login attempts against exposed services</td>
      <td>NETRESEC honeypot captures / SANS ISC</td>
      <td>T1595, T1110</td>
    </tr>
    <tr>
      <td>3</td>
      <td><strong>DNS Tunneling & Data Exfiltration</strong></td>
      <td>Abuse of DNS as a covert channel to move data out undetected</td>
      <td>Active Countermeasures (dnscat2) / Elastic examples (iodine)</td>
      <td>T1048.001, T1071.004</td>
    </tr>
  </tbody>
</table>

<h2>Tools & Methodology</h2>
<table>
  <thead>
    <tr>
      <th>Component</th>
      <th>Tool</th>
      <th>Purpose</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Packet Analysis</strong></td>
      <td>Wireshark 4.x</td>
      <td>Core investigation tool for all three cases</td>
    </tr>
    <tr>
      <td><strong>Traffic Orientation</strong></td>
      <td>Statistics → Protocol Hierarchy, Conversations</td>
      <td>First pass on any new capture, before filtering</td>
    </tr>
    <tr>
      <td><strong>Stream Reassembly</strong></td>
      <td>Follow TCP / HTTP / TLS Stream</td>
      <td>Reads a conversation as a transcript, not packet-by-packet</td>
    </tr>
    <tr>
      <td><strong>Artifact Extraction</strong></td>
      <td>Export Objects + SHA256 hashing</td>
      <td>Safely pulls transferred files without ever executing them</td>
    </tr>
    <tr>
      <td><strong>Threat Intel Lookup</strong></td>
      <td>VirusTotal, AbuseIPDB, urlscan.io</td>
      <td>Verifies extracted IOCs against known-bad infrastructure</td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th>Step</th>
      <th>Action</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>1</strong></td>
      <td><strong>Alert</strong></td>
      <td>Write a one-line simulated SIEM/IDS trigger before opening the capture</td>
    </tr>
    <tr>
      <td><strong>2</strong></td>
      <td><strong>Filter</strong></td>
      <td>Narrow the haystack with targeted display filters and Statistics views</td>
    </tr>
    <tr>
      <td><strong>3</strong></td>
      <td><strong>Inspect</strong></td>
      <td>Drill into headers, follow reassembled streams, extract artifacts</td>
    </tr>
    <tr>
      <td><strong>4</strong></td>
      <td><strong>Correlate</strong></td>
      <td>Connect the anomaly to surrounding traffic, timing, and infrastructure</td>
    </tr>
    <tr>
      <td><strong>5</strong></td>
      <td><strong>Document</strong></td>
      <td>Write the finding as a formal report with a confidence level and a recommended action</td>
    </tr>
  </tbody>
</table>


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
