# Digital Artefact

This file explains the digital artefact produced for the dissertation project.

## Artefact Description

The digital artefact is a controlled NIDS/NDR experiment dataset generated from a virtual lab comparing Suricata and Zeek.

The lab contained three main virtual machines:

- Kali Linux as the attacker machine
- Ubuntu Victim as the target machine
- Ubuntu Monitor as the IDS/NSM monitoring sensor

The artefact demonstrates the practical methods and findings described in the dissertation by providing captured traffic, tool outputs and result summaries from the experiments.

## Purpose of the Artefact

The purpose of the artefact is to show how Suricata and Zeek behave when exposed to the same controlled network traffic. Suricata was evaluated mainly through its alert output, while Zeek was evaluated through its connection and protocol logs.

The artefact supports the dissertation by providing evidence for:

- the practical lab setup
- the traffic generation process
- the PCAP-based data collection method
- the Suricata outputs
- the Zeek outputs
- the comparison between alert-based detection and contextual network visibility

## Dataset Contents

The full dataset is submitted separately as a compressed archive and follows this structure:

```text
tfg-results/
├── pcaps/
├── suricata/
├── zeek/
└── summaries/
```

## Main Dataset Folders

| Folder | Description |
|---|---|
| `pcaps/` | Raw packet captures generated during the experiments |
| `suricata/` | Suricata outputs, including alerts, event logs and summaries |
| `zeek/` | Zeek protocol and connection logs generated from the PCAPs |
| `summaries/` | TSV files used to summarise and compare the results |

## Experiments Included

The dataset includes outputs from the following experiments:

- Nmap reconnaissance scan
- Benign HTTP traffic
- SSH failed login attempts
- SSH successful login
- SMB enumeration
- FTP login activity

## Example Data Types

The artefact includes different types of technical evidence, including:

| Data Type | Examples |
|---|---|
| PCAP files | Raw traffic captures created with tcpdump |
| Suricata logs | `fast.log`, `eve.json`, `stats.log` |
| Zeek logs | `conn.log`, `http.log`, `ssh.log`, `ftp.log`, `weird.log` |
| Summary files | `.tsv` files created to compare experiment results |
| Global overview | Summary of the main outcome from each experiment |

## Repository Purpose

This repository does not replace the full dataset archive. Instead, it provides supporting documentation, command files and notes that explain how the artefact was created, organised and analysed.

The command files are organised into:

```text
commands/
├── 01_network_validation.md
├── 02_traffic_generation.md
├── 03_suricata_commands.md
├── 04_zeek_commands.md
└── 05_dataset_backup.md
```

These files document the main workflow used during the practical stage of the project, including network validation, traffic generation, Suricata analysis, Zeek analysis and dataset backup.

## Submission Note

The full artefact dataset is submitted separately as a compressed archive. This GitHub repository is provided as supplementary documentation to make the workflow easier to understand and reproduce.
