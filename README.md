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

📌 Refer to the below screenshot:

<img width="400" height="800" alt="image" src="https://github.com/user-attachments/assets/d91a61ea-967c-4485-a535-7835310760e7" />

### 2. Mythic C2 Server Deployment:
- Deployed a Kali Linux virtual machine and installed the required dependencies, including Docker Compose and Make.
- Cloned and deployed the Mythic C2 framework using Docker.
- Accessed and authenticated to the Mythic GUI.
- Prepared the C2 infrastructure for the planned adversary simulation.

📌 Refer to the below screenshots: (left to right)

<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/3f828831-022a-48e7-8cb6-183d3672c50b" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/5bd557e5-e4bb-493f-b94d-501d53f054ae" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/d1aa65f6-8504-4180-b824-1a75a89ae26e" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/5026cce7-a758-4ff3-943c-31d1a0112323" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/69ec0e77-d792-4fe2-8b55-ab37e4e0c290" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/b8628b09-9ef2-4fa0-a098-3453d47bb992" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/f8b15403-3564-45b2-9443-c96a96c1ee01" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/75ba8c6a-8cb6-4c8f-86ed-838ae3187fcc" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/d99f38f3-b499-4945-bdfc-67aaf0d4551c" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/065854ef-e5dd-4b39-84ef-c520dd6389a0" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/1d466e74-c8d8-46c2-86aa-6bd84a0adfeb" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/305980b0-6bc7-4e7f-8ed0-70b8d1691a18" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/a221dab8-6297-40c5-b286-2e9015853888" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/aa19c596-4be1-4292-9cc6-387b136b2ef6" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/bfe04ca0-350d-4a03-92c5-372c96a7bafb" />

### 3. Adversary Simulation – Attack Chain Execution:

#### Phase 1 – Credential Access (Brute Force):
- Seeded a target password into a custom wordlist built from the first 50 entries of `rockyou.txt`.
- Defined the target endpoint IP address and username.
- Used Hydra against the RDP service to perform a controlled brute-force attack against the Windows 11 administrator account.
- Achieved successful authentication, confirming valid credential compromise within the lab environment.

📌 Refer to the below screenshots: (left to right)

<img width="393" height="230" alt="image" src="https://github.com/user-attachments/assets/54ccb43c-216b-4569-a984-34d31e135109" />
<img width="393" height="230" alt="image" src="https://github.com/user-attachments/assets/daeca78c-db4b-48fa-80f8-d6608e2f6330" />
<img width="393" height="230" alt="image" src="https://github.com/user-attachments/assets/7f5f911a-48ba-4084-9c5b-b41251fb9cc8" />
<img width="393" height="230" alt="image" src="https://github.com/user-attachments/assets/a5be8112-4437-4e9d-ad94-8af6b07fa500" />
<img width="393" height="230" alt="image" src="https://github.com/user-attachments/assets/c3fe0bf0-4ad7-4be4-a373-9666e73a1380" />
<img width="393" height="230" alt="image" src="https://github.com/user-attachments/assets/48738ea6-891c-4128-9478-a7f6d729be84" />
<img width="790" height="230" alt="image" src="https://github.com/user-attachments/assets/c58e359a-32df-424a-b706-56e15bf1790c" />

#### Phase 2 – Discovery:
- Used the compromised RDP session to enumerate the Windows 11 environment.
- Performed host and account reconnaissance using commands including `whoami`, `ipconfig`, `net user`, and `net group`.
- Collected basic information about the host, user accounts, network configuration, and group membership.

📌 Refer to the below screenshots: (left to right)

<img width="393" height="230" alt="image" src="https://github.com/user-attachments/assets/401b0c4c-4add-4385-9d13-4aeb28bfda70" />
<img width="393" height="230" alt="image" src="https://github.com/user-attachments/assets/07404c77-82d9-4a95-b4cd-c3486942c7dd" />

#### Phase 3 – Defense Evasion:
- From the active RDP session, disabled the Windows Defender Firewall on the Windows 11 endpoint to simulate a defense evasion technique and reduce host-level network protection.

📌 Refer to the below screenshots: (left to right)

<img width="550" height="450" alt="image" src="https://github.com/user-attachments/assets/798a9694-bbc6-4ade-b568-2dbe1ea71824" />

#### Phase 4 – Execution:
- Used a PowerShell `IEX` (Invoke-Expression) command to retrieve and stage the Mythic Apollo agent on the Windows 11 endpoint.
- Executed the Mythic agent, establishing the initial connection back to the Mythic C2 server.

📌 Refer to the below screenshots: (left to right)

<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/bf230a22-9804-4d65-8444-d2fe2ebc0206" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/4fdcac34-9039-4e50-8908-fc0f3f3af8e2" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/97187076-4989-4d2d-9ade-f6a7ae498530" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/d742428c-a69a-40e4-b108-7a4788935bb4" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/bad937fd-0a21-4297-b31a-36173a8a513c" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/77cb65d9-0d2b-48e9-a0ce-5806f8a02ff9" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/d18e6290-7e89-45ff-a4a2-6a67c83cb482" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/02403d93-b765-4d6c-9321-c17e5536ecf5" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/f31493e9-cb87-43a9-a863-f181b0663366" />


#### Phase 5 – Command & Control:
- Confirmed a live, interactive C2 session between the Windows 11 endpoint and the Mythic C2 server.
- Validated C2 connectivity by issuing commands through the session and reviewed the resulting output in the Mythic GUI.
- Retrieved files from the endpoint through the established C2 session.

📌 Refer to the below screenshots: (left to right)

<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/8f27b645-1889-4add-8904-02c6c4b20e14" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/82d1a7dc-ed76-4ef7-97e3-575e9430a3bb" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/dba72ceb-fa0e-45c4-9846-1a488be3526e" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/00efeb9f-6a41-4f01-b178-121cdc0c58ca" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/d88c8508-04e4-4d83-80aa-59153cdae108" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/36777462-37a6-486e-968d-a95b73969267" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/6a88d790-84ac-45c2-a05d-76bbe0d4065d" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/3660eb3d-437e-412b-a80d-16dc10d4319b" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/ed701adc-2747-41d9-9541-2e265ed1cd39" />

#### Phase 6 – Exfiltration:
- Created a decoy credentials file (`passwords.txt`) containing non-sensitive test data on the Windows 11 endpoint to simulate sensitive information at rest.
- Used the active C2 session to exfiltrate `passwords.txt` from the Windows 11 endpoint to the Mythic C2 server.
- Demonstrated the complete simulated data theft workflow from endpoint to C2 infrastructure.

📌 Refer to the below screenshots: (left to right)

<img width="393" height="230" alt="image" src="https://github.com/user-attachments/assets/4ef00cc5-13e7-4a6f-8466-203d51412f6a" />
<img width="393" height="230" alt="image" src="https://github.com/user-attachments/assets/7a211506-a691-4d36-9416-17837dfedfe0" />

### 4. Detection Engineering from C2 Telemetry:
- Investigated Sysmon telemetry generated by the Apollo payload, including process creation events and file hash information.
- Reviewed process and execution activity associated with the simulated C2 payload.
- Built and saved a detection search to identify Apollo agent activity.
- Created a corresponding detection rule (`MYDFIR-Mythic-C2-Apollo-Agent-Detected`) to provide visibility into the simulated C2 activity.

📌 Refer to the below screenshots: (left to right)

<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/0ef92255-eda6-476d-b24f-b8eebbe7c51e" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/3c60ec11-ef0f-41b1-976d-7e956ea1def8" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/162e4e66-ee50-412a-997b-2c2499fd7acb" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/a12ef55f-e283-453e-9588-43307b4ea37c" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/4b59a498-092f-4629-ae2b-83c9d21fb64c" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/e5ed9c5c-3344-46ec-8f30-8921b12114a5" />
<img width="975" height="563" alt="image" src="https://github.com/user-attachments/assets/fcbe3bad-1c69-48e9-b766-086047fd20d5" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/39609e79-8b40-490e-82a0-b49731ffbef7" />
<img width="975" height="563" alt="image" src="https://github.com/user-attachments/assets/a737295b-6b3f-42fe-a14a-14b848ae219f" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/829ecafe-9bb7-481d-8029-1070a98b1093" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/fa77a678-9890-4d82-98aa-5a78d9410c55" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/88ff83ac-02b4-4b96-bf4d-79ebee8fb0dc" />
<img width="975" height="563" alt="image" src="https://github.com/user-attachments/assets/f7456984-4231-4425-b430-5e958d2a6cd4" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/ed7315d8-330b-4adc-b046-0c0b617c9ebe" />


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

<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/35744bac-6227-4681-9241-2b81126a42b2" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/48a601ce-b881-4500-8e0d-03a512841cb2" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/15691a69-18c1-4b68-b66f-fcf10460c561" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/841ac393-1902-498c-b743-f6d0c7133756" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/22528c55-883a-4f0e-8ae4-f3908fcf3f80" />
<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/edaace7d-f20e-4dd8-8faa-3119d2393150" />
<img width="975" height="556" alt="image" src="https://github.com/user-attachments/assets/8b220e81-c590-4d53-96cd-3a90d66cd283" />
<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/d9f8e230-cd3d-470b-a719-f9668c203d15" />
<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/6509d8e5-168a-405c-b00f-698562c82543" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/8473755e-585d-43e8-a0b8-8a80c8bb1371" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/2150b9c8-b4ee-4afc-82a9-ed534c194b3b" />





