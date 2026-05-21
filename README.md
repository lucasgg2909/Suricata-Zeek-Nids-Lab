\# Suricata and Zeek NIDS/NDR Lab



This repository contains the main technical commands and notes used during my dissertation project comparing Suricata and Zeek in a controlled virtual network lab.



The practical lab was built using VirtualBox and included:



\- Kali Linux as the attacker machine

\- Ubuntu Victim as the target machine

\- Ubuntu Monitor as the IDS/NSM sensor



The project compared how Suricata and Zeek behaved when exposed to different types of network traffic, including:



\- Nmap reconnaissance

\- Benign HTTP traffic

\- SSH failed login attempts

\- SSH successful login

\- SMB enumeration

\- FTP activity



\## Repository Structure



```text

suricata-zeek-nids-lab/

├── README.md

├── commands/

│   ├── 01\_network\_validation.md

│   ├── 02\_traffic\_generation.md

│   ├── 03\_suricata\_commands.md

│   ├── 04\_zeek\_commands.md

│   └── 05\_dataset\_backup.md

├── dataset\_structure/

│   └── tfg\_results\_structure.txt

└── notes/

&#x20;   └── experiment\_overview.md

