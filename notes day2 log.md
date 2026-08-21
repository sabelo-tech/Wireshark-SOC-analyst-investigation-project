Firewall logs show a spike in connection attempts from an external host across multiple ports, analyst requested to characterize the activity.



**Filter for Scan Patterns:**

\- Filter: tcp.flags.syn==1 \&\& tcp.flags.ack==0

\- Observation: Source IP 45.89.173.196 sent 29,597 SYN packets to port 80 in <time window>.

\- Interpretation: Consistent with automated scanning or brute-force attempts against HTTP service.

\- MITRE ATT\&CK: T1595 (Active Scanning), T1110 (Brute Force).



&#x20;**Filter for Scan Patterns:**

\- Tool: Statistics > Conversations (TCP tab), sorted by Packets

\- Observation: Source IP 45.89.173.196 shows 29,597 short-lived SYN attempts to port 80

\- Interpretation: Consistent with scanning/brute-force intrusion attempts

\- Contrast: Day 1 beaconing showed sustained long-lived connections instead



**Check for Brute-Force Behavior:**

\- Filter: tcp.port == 80

\- Observation: Source IP 45.89.173.196 attempted 301,789 connections to 192.168.138.2:80

\- Interpretation: Consistent with brute-force login attempts or SYN flood against HTTP service

\- MITRE ATT\&CK: T1110 (Brute Force)



**Inspect a Representative Attempt:**

\- Observation: Source IP 45.89.173.196 sent repeated HTTP GET requests to 192.168.138.2:80

\- Stream Analysis: Request for /static/code\_editor/addon/mode/install/ returned HTTP 404

\- Pattern: Single port focus (80), probing for web resources

\- Interpretation: Consistent with automated web reconnaissance and brute-force style probing

\- MITRE ATT\&CK: T1595 (Active Scanning), T1110 (Brute Force)





**Determine Scope and Outcome**:

\- Distinct Sources: 1 (45.89.173.196)

\- Attempts: 301,789 SYNs to 192.168.138.2:80

\- Handshake Completion: None observed (all reset or failed)

\- Outcome: Background noise, no sustained intrusion

\- Threat Intel: IP flagged on AbuseIPDB for web bot, web attack and ddos attack



**Case-02**: Recon \& Brute-Force

Source: 45.89.173.196

Target: 192.168.138.2:80

Attempts: 301,789 SYN/HTTP requests

Outcome: Background scanning, no sustained intrusion

MITRE ATT\&CK: T1595 (Active Scanning), T1110 (Brute Force)

Recommended Action: Monitor unless handshake completes; escalate if sustained traffic observed



