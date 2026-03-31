# SOC Detection Lab: Password Spraying

## Objective


The Password Spraying Detection Lab aimed to emulate a real world authentication-based attack and analyze its detection within a SIEM environment. The primary focus was to generate failed login activity using Atomic Red Team tests (MITRE T1110.003) in a Windows VM and investigate how these events are logged, ingested, and correlated in a Wazuh SIEM. This hands-on experience was designed to develop practical skills in log analysis, threat detection, and attack pattern identification associated with credential-based attacks.

### Setup


To build this lab environment, I created an Windows 11 virtual machine using VMware Fusion on my MacBook to serve as the target system for attack simulation and log generation. Next, I set an Ubuntu virtual machine up with the intention of deploying a local Wazuh SIEM. However, due to hardware limitations and insufficient RAM on my host machine, Wazuh was unable to run. As an alternative, I utilized Wazuh Cloud as the centralized SIEM and XDR platform to monitor the Windows 11 VM telemetry and detect security incidents. I began by deploying a Wazuh agent in the Windows VM to collect and forward security logs to the Wazuh Cloud platform.

Once the environment was established, I configured a Windows Security exclusion for the Atomic Red Team directory to prevent endpoint protection from blocking or interrupting attack emulation. I then ran Atomic Red Team tests via Windows PowerShell to emulate a password spraying attack mapped to MITRE ATT&CK technique T1110.003. This technique attempts authentication across multiple user accounts using a single or limited set of passwords, generating repeated failed login attempts while avoiding account lockouts. The execution of this attack on the Windows VM produced multiple failed authentication event logs (Event ID 4625), which were then collected and analyzed within Wazuh Cloud to identify patterns associated with credential-based attacks.

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
- Atomic Red Team T1110.003 Test 1

## Screenshots


<img width="680" height="880" alt="Screenshot 2026-03-25 at 3 45 05 PM" src="https://github.com/user-attachments/assets/ac929d8f-9fbd-4336-adc5-82f31c9fcfe1" />

*Ref 1: Audit Page 1*

<img width="680" height="880" alt="Screenshot 2026-03-25 at 3 45 15 PM" src="https://github.com/user-attachments/assets/1dc5ca4f-439d-4a6c-9821-bf5ee71c1e0b" />

*Ref 2: Audit Page 2*

<img width="680" height="880" alt="Screenshot 2026-03-25 at 3 45 30 PM" src="https://github.com/user-attachments/assets/e63ab1f5-8e1f-4b8b-a58c-14c146129067" />

*Ref 3: Audit Page 3*

<img width="680" height="880" alt="Screenshot 2026-03-25 at 3 45 37 PM" src="https://github.com/user-attachments/assets/f34d47b0-98e0-4e04-a7ea-b335fc88dd17" />

*Ref 4: Audit Page 4*

<img width="680" height="880" alt="Screenshot 2026-03-25 at 3 45 45 PM" src="https://github.com/user-attachments/assets/9514bc8f-42a5-4868-913e-41f37e9af200" />

*Ref 5: Audit Page 5*

<img width="680" height="880" alt="Screenshot 2026-03-25 at 3 45 53 PM" src="https://github.com/user-attachments/assets/1dd41c74-d654-49cd-b658-3a4e065db173" />

*Ref 6: Audit Page 6*

<img width="680" height="880" alt="Screenshot 2026-03-25 at 3 46 00 PM" src="https://github.com/user-attachments/assets/41c50dc2-72bd-48c3-a047-8537851c00cf" />

*Ref 7: Audit Page 7*

<img width="680" height="880" alt="Screenshot 2026-03-25 at 3 46 09 PM" src="https://github.com/user-attachments/assets/2d63efc9-1b8c-497b-9291-7e2f5e1ebecf" />

*Ref 8
