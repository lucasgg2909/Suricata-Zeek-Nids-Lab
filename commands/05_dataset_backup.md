# 05 - Dataset and Backup Commands



These commands were used to organise, verify and export the final dataset generated during the practical work.



## Create the Main Dataset Folder



```bash

mkdir -p ~/tfg-results

```



## Create the Main Dataset Structure



```bash

mkdir -p ~/tfg-results/pcaps

mkdir -p ~/tfg-results/suricata

mkdir -p ~/tfg-results/zeek

mkdir -p ~/tfg-results/summaries

```



The dataset was organised into four main folders: PCAP captures, Suricata outputs, Zeek outputs and summary files.



## Example Experiment Folder Structure



Example for the HTTP benign experiment:



```bash

mkdir -p ~/tfg-results/pcaps/http_benign

mkdir -p ~/tfg-results/suricata/http_benign

mkdir -p ~/tfg-results/zeek/http_benign

```



The same structure was used for the other experiments, including Nmap, SSH, SMB and FTP.



## Check Dataset Files



```bash

find ~/tfg-results -type f | sort

```



This command was used to list all files generated inside the dataset folder.



## Check Dataset Folder Sizes



```bash

du -sh ~/tfg-results/*

```



More detailed folder size check:



```bash

du -sh ~/tfg-results/pcaps/* ~/tfg-results/suricata/* ~/tfg-results/zeek/* ~/tfg-results/summaries/*

```



These commands were used to confirm that the experiment folders contained data and were not empty.



## Create Global Experiment Overview



```bash

mkdir -p ~/tfg-results/summaries

nano ~/tfg-results/summaries/experiment_overview.tsv

```



Example content:



```text

experiment	traffic_type	suricata_result	zeek_result	key_observation

nmap_scan	reconnaissance	ET_SCAN_Nmap_User_Agent_Observed	Zeek_recorded_connections_HTTP_UserAgent_and_services	Suricata_alerted_on_Nmap_HTTP_UserAgent_while_Zeek_provided_context

http_benign	benign_http	0_security_alerts_checksum_warnings	Zeek_recorded_7_HTTP_requests_with_curl_UserAgent	Suricata_did_not_alert_on_benign_HTTP_while_Zeek_logged_activity

ssh_failed_login	authentication	0_alerts	Zeek_recorded_SSH_auth_failure	Zeek_provided_authentication_context_while_Suricata_did_not_alert

ssh_successful_login	authentication	0_security_alerts_checksum_warnings	Zeek_recorded_SSH_session_auth_unknown	Zeek_logged_SSH_session_but_auth_success_was_not_confirmed

smb_enum	smb_enumeration	Suricata_result_saved	Zeek_recorded_connections_to_139_and_445	Zeek_showed_SMB_connection_visibility

ftp_login	ftp_traffic	0_alerts	Zeek_recorded_FTP_command_EPSV	Zeek_logged_FTP_protocol\_activity_while_Suricata_did_not_alert

```



## Create Final Dataset Backup



```bash

cd ~

tar -czf tfg-results-final-backup.tar.gz tfg-results

ls -lh ~/tfg-results-final-backup.tar.gz

```



This created a compressed backup of the complete dataset.



## Transfer Backup to Windows Using SCP



From Windows PowerShell:



```powershell

scp -P 2222 lgg@127.0.0.1:/home/lgg/tfg-results-final-backup.tar.gz "$env:USERPROFILE\Desktop\TFG-NIDS\\"

```



This command copied the final dataset backup from Ubuntu Monitor to Windows.



## Extract Backup on Windows



From Windows PowerShell:



```powershell

cd "$env:USERPROFILE\Desktop\TFG-NIDS"

tar -xzf .\tfg-results-final-backup.tar.gz

```



After extraction, the dataset folder was available on Windows for review and report writing.



## Final Dataset Structure



```text

tfg-results/

├── pcaps/

├── suricata/

├── zeek/

└── summaries/

```

