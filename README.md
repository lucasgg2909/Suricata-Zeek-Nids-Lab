# Suricata and Zeek NIDS/NDR Lab



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

## Digital Artefact

This repository supports the digital artefact submitted as part of my dissertation project.

The practical artefact for this project is a controlled Suricata and Zeek NIDS/NDR lab dataset. The dataset was generated from a VirtualBox lab where Kali Linux acted as the attacker machine, Ubuntu Victim acted as the target machine, and Ubuntu Monitor acted as the network monitoring sensor.

The full artefact dataset is submitted separately as a compressed archive. It contains:

- raw PCAP files captured with tcpdump
- Suricata outputs, including fast.log, eve.json and stats.log
- Zeek logs, including conn.log, http.log, ssh.log and ftp.log
- TSV summary files used to compare the experiment results
- a global experiment overview file

This GitHub repository provides the supporting documentation and command structure used to understand and reproduce the workflow.
