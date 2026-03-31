# SOC Detection Lab: Password Spraying

## Objective


The Password Spraying Detection Lab aimed to simulate a real world authentication-based attack and analyze its detection within a SIEM environment. The primary focus was to generate failed login activity using Atomic Red Team (MITRE T1110.003) in a Windows VM and investigate how these events are logged, ingested, and correlated in a Wazuh SIEM. This hands-on experience was designed to develop practical skills in log analysis, threat detection, and attack pattern identification associated with credential-based attacks.

### Setup


To build this lab environment, I created an Windows 11 virtual machine using VMware Fusion on my MacBook to serve as the target system for attack simulation and log generation. Next, I set an Ubuntu virtual machine up with the intention of deploying a local Wazuh SIEM. However, due to hardware limitations and insufficient RAM on my host machine, Wazuh was unable to run. As an alternative, I utilized Wazuh Cloud as the centralized SIEM and XDR platform to monitor the Windows 11 VM telemetry and detect security incidents. I began by deploying Wazuh agents in the Windows VM to collect and forward security logs to the Wazuh Cloud platform.

Once the environment was established, I configured a Windows Security exclusion for the Atomic Red Team directory to prevent endpoint protection from blocking or interrupting attack simulations. I then used Atomic Red Team via Windows PowerShell to simulate a password spraying attack aligned with MITRE ATT&CK technique T1110.003. This technique attempts authentication across multiple user accounts using a single or limited set of passwords, generating repeated failed login attempts while avoiding account lockouts. The execution of this attack on the Windows VM produced multiple failed authentication event logs (Event ID 4625), which were then collected and analyzed within Wazuh Cloud to identify patterns associated with credential-based attacks.

### Skills Learned


- Gained experience performing cybersecurity risk assessments and identifying organizational vulnerabilities
- Developed an understanding of risk analysis methods to prioritize security issues effectively
- Learned how to evaluate security controls using frameworks like the NIST Cybersecurity Framework (CSF)
- Built the ability to translate technical findings into clear, business-friendly recommendations
- Strengthened communication skills through stakeholder interviews and presentations
- Enhanced critical thinking in identifying security gaps and proposing mitigation strategies

### Tools Used


- NIST Cybersecurity Framework (CSF) for control evaluation
- Risk assessment and auditing methodologies
- Security reporting & documentation

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
