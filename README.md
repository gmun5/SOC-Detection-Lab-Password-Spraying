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
- Atomic Red Team T1110.003 TestNumbers 1

## Screenshots


<img width="1920" height="958" alt="Screenshot 2026-03-29 at 7 00 56 PM" src="https://github.com/user-attachments/assets/d424586f-20aa-4ec8-a7bd-20b54b758ccc" />

*Ref 1: Audit Page 1*

<img width="1920" height="176" alt="Screenshot 2026-03-30 at 2 52 26 AM" src="https://github.com/user-attachments/assets/a81a54f0-ec9e-454c-b5f9-b040ffab5219" />

*Ref 1: Audit Page 1*

<img width="1920" height="1080" alt="Screenshot 2026-03-31 at 1 10 58 AM" src="https://github.com/user-attachments/assets/7ed62ce3-b6af-43e2-a1bc-1ee8cfd511d0" />

*Ref 2: Audit Page 2*

<img width="1920" height="959" alt="Screenshot 2026-03-30 at 3 00 50 AM" src="https://github.com/user-attachments/assets/3a5480dd-1e41-4300-a5c7-19481fc55194" />

*Ref 3: Audit Page 3*

<img width="1920" height="959" alt="Screenshot 2026-03-31 at 1 07 57 AM" src="https://github.com/user-attachments/assets/a385b5bb-e685-4215-a526-719f85dd3ff8" />

*Ref 4: Audit Page 4*

<img width="1920" height="959" alt="Screenshot 2026-03-30 at 3 11 50 AM" src="https://github.com/user-attachments/assets/d2fc65a3-80c9-4268-85d6-87e85a97a22a" />

*Ref 5: Audit Page 5*

<img width="1920" height="959" alt="Screenshot 2026-03-30 at 3 35 48 AM" src="https://github.com/user-attachments/assets/ab4e757a-3890-4d91-aa9e-95899373d17a" />

*Ref 6: Audit Page 6*

<img width="1920" height="959" alt="Screenshot 2026-03-30 at 3 31 26 AM" src="https://github.com/user-attachments/assets/6e33b6f3-9c9e-4282-ba65-bd6b2ddc70ee" />

*Ref 7: Audit Page 7*
