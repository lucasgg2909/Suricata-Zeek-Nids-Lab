# Suricata and Zeek NIDS/NDR Lab

This repository contains the main technical notes and commands from my dissertation project, where I compared Suricata and Zeek in a controlled virtual NIDS/NDR lab.

The practical lab was built using VirtualBox and included:

- Kali Linux as the attacker machine
- Ubuntu Victim as the target machine
- Ubuntu Monitor as the IDS/NSM sensor

The project compared how Suricata and Zeek behaved when exposed to different types of network traffic, including:

- Nmap reconnaissance
- Benign HTTP traffic
- SSH failed login attempts
- SSH successful login
- SMB enumeration
- FTP activity

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

For a more detailed explanation of the submitted artefact, see [DIGITAL_ARTEFACT.md](DIGITAL_ARTEFACT.md).

## Repository Structure

```text
suricata-zeek-nids-lab/
├── README.md
├── DIGITAL_ARTEFACT.md
├── commands/
│   ├── 01_network_validation.md
│   ├── 02_traffic_generation.md
│   ├── 03_suricata_commands.md
│   ├── 04_zeek_commands.md
│   └── 05_dataset_backup.md
├── dataset_structure/
│   └── tfg_results_structure.txt
└── notes/
    └── experiment_overview.md
```

## Commands Folder

The `commands/` folder contains the main technical commands used during the practical work.

| File | Description |
|---|---|
| `01_network_validation.md` | IP checks, connectivity tests, service checks and tcpdump visibility |
| `02_traffic_generation.md` | Nmap, curl, Hydra, SSH, SMB and FTP traffic generation commands |
| `03_suricata_commands.md` | Suricata validation, PCAP analysis and alert summary commands |
| `04_zeek_commands.md` | Zeek PCAP analysis and zeek-cut extraction commands |
| `05_dataset_backup.md` | Dataset organisation, summary files, backup and export commands |

## Dataset Structure

The full practical dataset is submitted separately as a compressed archive. Its structure is documented in:

```text
dataset_structure/tfg_results_structure.txt
```

The dataset contains:

```text
tfg-results/
├── pcaps/
├── suricata/
├── zeek/
└── summaries/
```

## Experiments Included

The practical dataset includes outputs from the following experiments:

| Experiment | Purpose |
|---|---|
| Nmap scan | Simulate reconnaissance and service discovery |
| Benign HTTP traffic | Generate normal HTTP activity using curl |
| SSH failed login | Generate controlled failed authentication attempts |
| SSH successful login | Compare legitimate SSH activity |
| SMB enumeration | Observe traffic targeting Samba/SMB services |
| FTP login | Generate basic FTP protocol activity |

## Important Note

The commands and experiments documented in this repository were used only inside an isolated VirtualBox lab. No public systems, third-party networks or real external targets were tested.

Any usernames or passwords shown in the command files were created only for the lab and do not represent real credentials.
