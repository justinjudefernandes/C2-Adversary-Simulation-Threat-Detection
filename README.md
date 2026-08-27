# C2 Adversary Simulation & Threat Detection

## 🎯 Objective:
Simulate a realistic Command and Control (C2) attack chain spanning credential access, discovery, defense evasion, execution, command and control, and exfiltration, then develop detection rules and dashboards to identify the resulting attacker activity.

## 📊 Project Overview:
Conducted an end-to-end adversary simulation using the Mythic C2 framework against a Windows 11 endpoint, following a structured six-phase attack chain aligned to MITRE ATT&CK tactics. The simulation progressed from a brute-force credential attack through host discovery, defense evasion, payload execution, live C2 command and control, and simulated data exfiltration. The resulting telemetry was then analyzed to build detection rules and a security dashboard surfacing suspicious process creation, outbound network activity, and Windows Defender tampering. This provided an end-to-end view of how attacker activity can be simulated, detected, and investigated.

## 🧰 Tools Used:
- Kali Linux
- Mythic C2 Framework (Apollo Agent)
- Hydra
- xfreerdp
- Docker / Docker Compose
- Windows 11 – Target Endpoint
- Elastic Stack (Elasticsearch, Kibana)
- Sysmon
- Windows Defender
- VirusTotal (OSINT/Threat Intelligence)
- PowerShell / Windows Command Prompt

## 🛠️ Capabilities Demonstrated:
- C2 framework architecture and operational understanding (Mythic, Cobalt Strike, Sliver, Metasploit)
- Adversary attack-chain planning, diagramming, and MITRE ATT&CK tactic mapping
- C2 infrastructure deployment using Docker
- Credential-based brute-force attack execution
- Host discovery and post-exploitation reconnaissance
- Defense evasion technique execution
- Custom payload generation and C2 callback configuration
- Payload delivery and remote command execution
- Command and control session management
- Data exfiltration technique execution
- Adversary telemetry analysis using Sysmon and Elastic
- Threat intelligence lookups and hash-based analysis
- Detection rule development for C2 agent activity
- Dashboard development for suspicious process, network, and security-control-tampering activity

## 📁 Key Deliverables:
- Documented C2 concepts, frameworks, and a six-phase attack-chain diagram mapped to MITRE ATT&CK tactics
- Deployed a Mythic C2 server via Docker on Kali Linux
- Executed a full adversary simulation: brute force → discovery → defense evasion → execution → command & control → exfiltration
- Generated and deployed a custom Apollo C2 payload (`svchost-justin-apollo.exe`)
- Investigated the resulting telemetry and performed hash-based threat intelligence analysis using VirusTotal
- Created a detection rule (`MYDFIR-Mythic-C2-Apollo-Agent-Detected`) to identify Apollo agent activity
- Built a 3-panel security dashboard (`MYDFIR-Suspicious-Activity`) covering process creation, network connections, and Windows Defender tampering

## 🔍 Steps Performed:

### 1. C2 Threat Research & Attack Planning:
- Researched Command and Control (C2) concepts, purpose, and common frameworks such as Metasploit, Cobalt Strike, Sliver, and Mythic.
- Mapped a six-phase attack chain aligned to MITRE ATT&CK tactics:
  - Credential Access
  - Discovery
  - Defense Evasion
  - Execution
  - Command & Control
  - Exfiltration
- Designed an attack-chain diagram to document the planned adversary simulation from initial access through data exfiltration.

📌 Refer to the below screenshots: (left to right)

### 2. Mythic C2 Server Deployment:
- Deployed a Kali Linux virtual machine and installed the required dependencies, including Docker Compose and Make.
- Cloned and deployed the Mythic C2 framework using Docker.
- Accessed and authenticated to the Mythic GUI.
- Prepared the C2 infrastructure for the planned adversary simulation.

📌 Refer to the below screenshots: (left to right)

### 3. Adversary Simulation – Attack Chain Execution:

#### Phase 1 – Credential Access (Brute Force):
- Seeded a target password into a custom wordlist built from the first 50 entries of `rockyou.txt`.
- Defined the target endpoint IP address and username.
- Used Hydra against the RDP service to perform a controlled brute-force attack against the Windows 11 administrator account.
- Achieved successful authentication, confirming valid credential compromise within the lab environment.

#### Phase 2 – Discovery:
- Used the compromised RDP session to enumerate the Windows 11 environment.
- Performed host and account reconnaissance using commands including `whoami`, `ipconfig`, `net user`, and `net group`.
- Collected basic information about the host, user accounts, network configuration, and group membership.

#### Phase 3 – Defense Evasion:
- From the active RDP session, disabled the Windows Defender Firewall on the Windows 11 endpoint to simulate a defense evasion technique and reduce host-level network protection.

#### Phase 4 – Execution:
- Used a PowerShell `IEX` (Invoke-Expression) command to retrieve and stage the Mythic Apollo agent on the Windows 11 endpoint.
- Executed the Mythic agent, establishing the initial connection back to the Mythic C2 server.

#### Phase 5 – Command & Control:
- Confirmed a live, interactive C2 session between the Windows 11 endpoint and the Mythic C2 server.
- Validated C2 connectivity by issuing commands through the session and reviewing the resulting output in the Mythic GUI.
- Retrieved files from the endpoint through the established C2 session.

#### Phase 6 – Exfiltration:
- Created a decoy credentials file (`passwords.txt`) containing non-sensitive test data on the Windows 11 endpoint to simulate sensitive information at rest.
- Used the active C2 session to exfiltrate `passwords.txt` from the Windows 11 endpoint to the Mythic C2 server.
- Demonstrated the complete simulated data theft workflow from endpoint to C2 infrastructure.

📌 Refer to the below screenshots: (left to right)

### 4. Detection Engineering from C2 Telemetry:
- Investigated Sysmon telemetry generated by the Apollo payload, including process creation events and file hash information.
- Reviewed process and execution activity associated with the simulated C2 payload.
- Performed a hash-based threat intelligence lookup using VirusTotal.
- Built and saved a detection search to identify Apollo agent activity.
- Created a corresponding detection rule (`MYDFIR-Mythic-C2-Apollo-Agent-Detected`) to provide visibility into the simulated C2 activity.

📌 Refer to the below screenshots: (left to right)

### 5. Suspicious Activity Dashboard:
- Built targeted queries to identify suspicious process creation involving PowerShell, CMD, and Rundll32.
- Created visibility into outbound network connections initiated by processes.
- Monitored Windows Defender real-time protection tampering.
- Assembled the queries into a 3-panel dashboard (`MYDFIR-Suspicious-Activity`) covering:
  - Suspicious Process Creation
  - Outbound Network Connections
  - Windows Defender Tampering
- Used the dashboard to provide centralized visibility into suspicious activity generated during the adversary simulation.

📌 Refer to the below screenshots: (left to right)
