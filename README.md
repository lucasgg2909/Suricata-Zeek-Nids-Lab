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

│   ├── 01_network_validation.md

│   ├── 02_traffic_generation.md

│   ├── 03_suricata_commands.md

│   ├── 04_zeek_commands.md

│   └── 05_dataset_backup.md

├── dataset_structure/

│   └── tfg_results_structure.txt

└── notes/

   └── experiment\_overview.md

