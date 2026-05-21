# 04 - Zeek Commands



These commands were used to run Zeek and extract useful fields from Zeek logs during the experiments.



## Check Zeek Version



```bash

/opt/zeek/bin/zeek --version

```



This command was used to confirm that Zeek was installed and available on Ubuntu Monitor.



## Run Zeek on a Live Interface



```bash

sudo /opt/zeek/bin/zeek -i enp0s3

```



The `enp0s3` interface was connected to the internal IDS-LAB network and was used to observe lab traffic.



## Analyse a PCAP File with Zeek



General format:



```bash

/opt/zeek/bin/zeek -r input.pcap

```



Example for Nmap traffic:



```bash

/opt/zeek/bin/zeek -r ~/tfg-results/pcaps/nmap_scan_test/nmap_scan_kali_to_victim.pcap

```



Example for HTTP benign traffic:



```bash

/opt/zeek/bin/zeek -r ~/tfg-results/pcaps/http_benign/http_benign_kali_to_victim.pcap

```



## List Zeek Output Files



```bash

ls -lh

```



This command was used after running Zeek to check which logs had been generated.



Common Zeek logs reviewed in this project included:



```text

conn.log

http.log

ssh.log

ftp.log

weird.log

packet_filter.log

```



## Extract Connection Information from conn.log



```bash

/opt/zeek/bin/zeek-cut id.orig_h id.resp_h id.resp_p proto service conn_state < conn.log

```



This was used to review source IPs, destination IPs, ports, protocols, identified services and connection states.



## Extract HTTP Information from http.log



```bash

/opt/zeek/bin/zeek-cut id.orig_h id.resp_h method host uri user_agent < http.log

```



This was used to review HTTP methods, requested resources and User-Agent values.



## Extract SSH Information from ssh.log



```bash

/opt/zeek/bin/zeek-cut id.orig_h id.resp_h version auth_success < ssh.log

```



This was used to check SSH sessions and whether Zeek inferred authentication success or failure.



## Extract FTP Information from ftp.log



```bash

/opt/zeek/bin/zeek-cut id.orig_h id.resp_h user command arg reply_code reply_msg < ftp.log

```



This was used to review FTP users, commands and server responses.



## Create HTTP Benign Summary TSV



```bash

echo "orig_h resp_h method host uri user_agent" > zeek_http_benign_summary.tsv

/opt/zeek/bin/zeek-cut id.orig_h id.resp_h method host uri user_agent < http.log >> zeek_http_benign_summary.tsv

cat zeek_http_benign_summary.tsv

```



## Count HTTP Requests



```bash

echo "experiment http_request_count" > zeek_http_benign_request_count.tsv

echo "http_benign $(grep -v '^#' http.log | wc -l)" >> zeek_http_benign_request_count.tsv

cat zeek_http_benign_request_count.tsv

```



## Create SSH Failed Login Summary



```bash

echo "orig_h resp_h version auth_success" > zeek_ssh_failed_login_summary.tsv

/opt/zeek/bin/zeek-cut id.orig_h id.resp_h version auth_success < ssh.log >> zeek_ssh_failed_login_summary.tsv

cat zeek_ssh_failed_login_summary.tsv

```



## Create SMB Connection Summary



```bash

echo "orig_h resp_h resp_p proto service conn_state" > zeek_smb_enum_conn_summary.tsv

/opt/zeek/bin/zeek-cut id.orig_h id.resp_h id.resp_p proto service conn_state < conn.log >> zeek_smb_enum_conn_summary.tsv

cat zeek_smb_enum_conn_summary.tsv

```



## Create SMB Port Count Summary



```bash

echo "port connection_count" > zeek_smb_enum_port_count.tsv

awk 'NR>1 {c\[$3]++} END {for (p in c) print p, c\[p]}' zeek_smb_enum_conn_summary.tsv | sort -n >> zeek_smb_enum_port_count.tsv

cat zeek_smb_enum_port_count.tsv

```



## Create FTP Login Summary



```bash

echo "orig_h resp_h user command arg reply_code reply_msg" > zeek_ftp_login_summary.tsv

/opt/zeek/bin/zeek-cut id.orig_h id.resp_h user command arg reply_code reply_msg < ftp.log >> zeek_ftp_login_summary.tsv

cat zeek_ftp_login_summary.tsv

```

