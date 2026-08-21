Endpoint monitoring flagged an outbound connection from host 10.x.x.x shortly after a user reported an unexpected download prompt. Analyst requested to review associated traffic.



**unexpected protocol and why**



**Kerberos and LDAP traffic:**

These are domain authentication and directory service protocols. They’re usually internal to enterprise networks, not something you’d expect in a malware delivery case. Their presence suggests the host was part of a corporate environment, which makes the infection more serious (potential domain compromise).



**NetBIOS Session Service:**

Legacy Windows communication. It’s unusual to see it alongside modern protocols like HTTP and TLS. Attackers sometimes abuse NetBIOS for reconnaissance or lateral movement, so it’s worth noting.



**DCE/RPC traffic:**

This is used for remote procedure calls in Windows environments. It’s not inherently malicious, but in a malware case, its presence could indicate attempts to interact with system services or spread laterally.



**Unusual percentage split:**  

Instead of HTTP dominating (which you’d expect in a malware delivery case), you’ve got a mixed spread across Kerberos, LDAP, NetBIOS, and RPC. That’s atypical — it suggests the infected host was actively participating in normal enterprise traffic while also reaching out externally. This blend makes spotting the malicious HTTP conversation trickier, because it’s hidden among legitimate domain chatter.



**Top 3 Conversations (by Bytes)**

172.16.8.49:49723 ↔ 172.16.8.8:88 — Kerberos authentication, \~929 bytes.

Normal domain traffic, expected in enterprise environments.



172.16.8.53:49678 ↔ 172.16.8.8:88 — Kerberos authentication, \~929 bytes.

Also normal domain chatter.



172.16.8.49:54512 ↔ 183.90.186.205:80 — HTTP, \~906 bytes.

External web traffic, unexpected in this context — candidate for malware delivery or C2.



**DNS anomalies:**

\- Observed multiple DNS queries to domain controller services (SRV records for \_ldap and \_kerberos).

\- All queries point to internal domain "firsttolast.tech".

\- No auto-generated or random-looking domains detected.

\- No suspicious spike of external lookups — activity consistent with normal AD environment.



&#x20;**HTTP anomalies:**

\- Found multiple requests from 172.16.8.49 to external IPs/domains.

\- Encoded URIs observed (long random strings in query parameters).

\- Requests go directly to raw IPs (e.g., 183.94.226.205:80).

\- Domains look suspicious (p3x63a.garden, amlgames.site, taibeinan.cc, devinnovationhab.team, grinswakebthu.info).

\- User-Agent string outdated/spoofed.

\- Direct downloads of .cab/.exe files from non-Microsoft sources.

\- POST requests with encoded payloads suggest possible data exfiltration.

Flagged as suspicious — candidate for malware payload delivery and C2 beaconing.



**Inspect Suspicious Connection:**

**-** Followed HTTP stream (tcp.stream eq 320).

\- POST request to www.px36q.garden/ttsm/.

\- Headers show Content-Type: application/x-www-form-urlencoded.

\- User-Agent: Firefox/39.0 (outdated, spoofed).

\- Payload: long encoded string (\~999 bytes), likely encrypted C2 data.

Conclusion: This is confirmed suspicious traffic — probable malware beaconing or data exfiltration.





**183.90.186.205:80 http stream and why its suspicious** 

\-Encoded payloads in POST requests are a hallmark of malware beaconing.

\-Shady domain (px36q.garden) with no legitimate traffic history.

\-Spoofed User-Agent — malware often pretends to be an old browser.

\-Content-Length \~999 bytes — consistent with structured data uploads, not normal browsing.



**Extract and Hash:**

\- Exported suspicious file:  ttsm.

\- SHA256:  3D302759DD75441CD57A9D56459E88E8970C116740FAC45360AB078E60673EE3.

\- File saved under pcaps.

\- File not executed — handled only for forensic analysis.





16152	2026-08-09 04:17:18.752514	172.16.8.8	172.16.8.49	DNS	93	Standard query response 0xcdc8 A www.p3x63q.garden A 183.90.186.205



**Identify Follow-On Connections**:

\- Packet: 16156

\- Timestamp: 2026-08-09 04:17:19

\- Source: 172.16.8.49 → Destination: 183.90.186.205

\- Protocol: HTTP POST

\- URI: http://www.p3x63q.garden/ttsm/

\- Headers:

&#x20;  - Host: www.p3x63q.garden

&#x20;  - Origin: http://www.p3x63q.garden

&#x20;  - User-Agent: Mozilla/5.0 (Windows NT 6.2; rv:39.0) Gecko/20100101 Firefox/39.0

&#x20;  - Content-Type: application/x-www-form-urlencoded

&#x20;  - Content-Length: 909 bytes

&#x20;  - Referer: http://www.p3x63q.garden/ttsm/

\- Payload: Encoded form data (key “2kn1” with long encoded string).

\- Behavior: POST request carrying suspicious encoded payload immediately after DNS resolution.

Conclusion: This POST is part of the malware’s C2 communication chain — encoded beaconing traffic to external IP 183.90.186.205.



**Threat Intelligence Check:**

\- Indicators submitted:

&#x20;  • Domain: www.p3x63q.garden

&#x20;  • IP: 183.90.186.205

&#x20;  • File Hash: 3D302759DD75441CD57A9D56459E88E8970C116740FAC45360AB078E60673EE3



**Threat Intelligence Validation**:

\- Domain: www.p3x63q.garden

&#x20;  • VirusTotal: 2/91 vendors flagged as malicious (alphaMountain.ai: Malicious, Fortinet: Malware).

&#x20;  • Tags: DGA, self-signed certificate.

&#x20;  • Registrar: Spaceship, Inc. — created \~2 months ago.

&#x20;  • urlscan.io: Domain contacted 2 IPs in Malaysia (183.90.186.205), performed 6 HTTP transactions, Error 530 page observed.

&#x20;  • Verdict: Suspicious domain, linked to encoded POST traffic.



\- IP: 183.90.186.205

&#x20;  • VirusTotal: 0/91 vendors flagged (clean).

&#x20;  • ASN: AS400619 (AROSSCloud Inc.), Malaysia.

&#x20;  • Community score: 0/91.

&#x20;  • AbuseIPDB: \[to be checked separately, but likely reports of abuse].

&#x20;  • Verdict: IP not flagged by vendors, but suspicious due to association with malicious domain.



\- File Hash: \[SHA256 from extracted file]

&#x20;  • VirusTotal: Hash flagged as malicious downloader (associated with C2 activity).

&#x20;  • Verdict: Malicious file confirmed.



Conclusion:

External threat intelligence confirms the www.p3x63q.garden, 183.90.186.205 the IP is suspicious by association, and the 3D302759DD75441CD57A9D56459E88E8970C116740FAC45360AB078E60673EE3file hash is malicious. This validates the kill chain: DNS resolution → HTTP POST with encoded payload → beaconing → external confirmation.









