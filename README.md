# SOC Detection Lab: Password Spraying

## Objective


The Password Spraying Detection Lab aimed to emulate a real world authentication-based attack and analyze its detection within a SIEM environment. The primary focus was to generate failed login activity using Atomic Red Team tests (MITRE T1110.003) in a Windows VM and investigate how these events are logged, ingested, and correlated in a Wazuh SIEM. This hands-on experience was designed to develop practical skills in log analysis, threat detection, and attack pattern identification associated with credential-based attacks.

### Setup


To build this lab environment, I created and configured my own Windows 11 virtual machine using VMware Fusion on my MacBook to serve as the target system for attack simulation and log generation. I also installed and configured Sysmon to enhance system visibility and capture detailed event logs. Next, I set up an Ubuntu virtual machine with the intention of deploying a local Wazuh SIEM. However, due to hardware limitations and insufficient RAM on my host machine, Wazuh was unable to run. As an alternative, I utilized Wazuh Cloud as the centralized SIEM and XDR platform to monitor the Windows 11 VM telemetry and detect security incidents. I then deployed a Wazuh agent on the Windows VM to collect and forward security logs to the Wazuh Cloud platform.

Once the environment was established, I downloaded and configured Atomic Red Team on the Windows VM to enable controlled attack emulation. I then configured a Windows Security exclusion for the Atomic Red Team directory to prevent endpoint protection from blocking or interrupting attack execution. Next, I ran Atomic Red Team tests via Windows PowerShell to emulate a password spraying attack mapped to MITRE ATT&CK technique T1110.003. This technique attempts authentication across multiple user accounts using a single or limited set of passwords, generating repeated failed login attempts while avoiding account lockouts. The execution of this attack on the Windows VM produced multiple failed authentication event logs (Event ID 4625), which were then collected and analyzed within Wazuh Cloud to identify patterns associated with credential-based attacks.

### Skills Learned


- Hands-on experience analyzing Windows Security logs for authentication-related investigations
- Practical use of a SIEM (Wazuh Cloud) to filter, search, and investigate security events
- Understanding of how credential-based attacks are reflected in log data and detected within a SIEM
- Ability to recognize password spraying activity through patterns of repeated failed logins across multiple accounts
- Improved judgment in distinguishing normal system activity from potential security threats

### Tools Used


- Windows 11 Virtual Machine (VMware Fusion)
- Windows Powershell
- Windows Event Viewer
- Wazuh Cloud (SIEM & XDR)
- Sysmon
- Atomic Red Team T1110.003 TestNumbers 1

## Screenshots


<img width="1920" height="958" alt="Screenshot 2026-03-29 at 7 00 56 PM" src="https://github.com/user-attachments/assets/d424586f-20aa-4ec8-a7bd-20b54b758ccc" />

*Ref 1: This is the initial baseline state of the environment prior to attack execution. The Wazuh dashboard overview shows minimal or no alerts, indicating no active security incidents at that time. This establishes a clean starting point for comparison against post-attack activity.*


<img width="1920" height="176" alt="Screenshot 2026-03-30 at 2 52 26 AM" src="https://github.com/user-attachments/assets/a81a54f0-ec9e-454c-b5f9-b040ffab5219" />

*Ref 2: This captures the moment the password spraying attack (MITRE ATT&CK T1110.003) was executed using Atomic Red Team via PowerShell. The command initiates controlled authentication attempts across multiple accounts to simulate adversary behavior. This step marks the transition from a normal baseline state to active attack emulation. It is responsible for generating the failed login events observed in subsequent screenshots.*


<img width="1920" height="1080" alt="Screenshot 2026-03-31 at 1 10 58 AM" src="https://github.com/user-attachments/assets/7ed62ce3-b6af-43e2-a1bc-1ee8cfd511d0" />

*Ref 3: This displays the Windows Security Event Logs after the password spraying attack was executed. Multiple Event ID 4625 entries indicate repeated failed authentication attempts across different user accounts. The presence of these logs confirms that the simulated attack successfully generated endpoint-level telemetry.*


<img width="1920" height="959" alt="Screenshot 2026-03-30 at 3 00 50 AM" src="https://github.com/user-attachments/assets/3a5480dd-1e41-4300-a5c7-19481fc55194" />

*Ref 4: This dashboard is located within the Threat Hunting tab in Wazuh, it reflects the environment after the attack activity has been ingested and processed by Wazuh. The presence of authentication failures indicates detection of abnormal login behavior generated during the simulation. The spike in activity highlights how SIEM dashboards can quickly surface suspicious patterns.*


<img width="1920" height="959" alt="Screenshot 2026-03-30 at 3 11 50 AM" src="https://github.com/user-attachments/assets/d2fc65a3-80c9-4268-85d6-87e85a97a22a" />

*Ref 6: This view shows logs filtered within the Discover tab to isolate Event ID 4625, focusing specifically on failed authentication attempts generated during the attack. In this state, each individual log entry is expanded to display all available fields, including detailed event data from the Windows endpoint. This allows for deeper inspection of each authentication failure, such as usernames, logon types, and failure reasons.*

<img width="1920" height="959" alt="Screenshot 2026-03-31 at 1 07 57 AM" src="https://github.com/user-attachments/assets/a385b5bb-e685-4215-a526-719f85dd3ff8" />

*Ref 5: This is also in the Discover tab in Wazuh. The timeline visualization highlights a clustered spike. In this case, both Event ID 4625, and data.win.systems.systemTime are filtered to isolate failed authentication attempts generated during the attack simulation and the time the event logs originally occurred on the Windows endpoint.*

<img width="1920" height="959" alt="Screenshot 2026-03-30 at 3 26 23 AM" src="https://github.com/user-attachments/assets/b7a775bb-6312-44ec-b632-939c8e5df97e" />

*Ref 7: This view is located in the Events tab within the Threat Hunting module in Wazuh, where processed alerts are displayed in a structured format. The data is filtered to show Event ID 4625-related activity, highlighting failed authentication attempts associated with the attack simulation. Each entry represents a normalized alert generated by Wazuh, including rule descriptions such as “Logon Failure – Unknown user or bad password.*


<img width="1920" height="959" alt="Screenshot 2026-03-30 at 3 31 26 AM" src="https://github.com/user-attachments/assets/6e33b6f3-9c9e-4282-ba65-bd6b2ddc70ee" />

*Ref 8: This view is located in the MITRE ATT&CK tab within Wazuh, where events are mapped to adversary tactics and techniques. The dashboard reflects the state after filtering for Event ID 4625, highlighting authentication-related activity generated during the attack simulation. The visualizations show that the detected events are categorized under relevant attack tactics, indicating that Wazuh successfully mapped the failed login activity to MITRE ATT&CK classifications.*
