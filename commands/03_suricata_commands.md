# 03 - Suricata Commands



These commands were used to install, validate and run Suricata on the Ubuntu Monitor machine.



## Check Suricata Version



```bash

suricata -V

```



Alternative command:



```bash

suricata --build-info

```



These commands were used to confirm that Suricata was installed correctly.



## Update Suricata Rules



```bash

sudo suricata-update

```



This command was used to download and prepare the Suricata ruleset used during the experiments.



## Test Suricata Configuration



```bash

sudo suricata -T -c /etc/suricata/suricata.yaml -v

```



This was used to confirm that Suricata could load its configuration and rules successfully before running the experiments.



## Run Suricata on the Monitoring Interface



```bash

sudo suricata -c /etc/suricata/suricata.yaml -i enp0s3

```



The `enp0s3` interface was connected to the internal IDS-LAB network and was used to monitor lab traffic.



## Run Suricata with Local Validation Rules



```bash

sudo suricata -c /etc/suricata/suricata.yaml -i enp0s3 -S /etc/suricata/rules/local.rules

```



Local ICMP and TCP SYN rules were used only to validate that Suricata could observe traffic and write alerts. These local rules were not used as part of the final comparison results.



## View Suricata fast.log in Real Time



```bash

sudo tail -f /var/log/suricata/fast.log

```



This command was used during live testing to observe whether Suricata generated alerts.



## Analyse a PCAP File with Suricata



General format:



```bash

sudo suricata -c /etc/suricata/suricata.yaml -r input.pcap -l output_folder

```



Example for HTTP benign traffic:



```bash

sudo suricata -c /etc/suricata/suricata.yaml -r ~/tfg-results/pcaps/http_benign/http_benign_kali_to_victim.pcap -l ~/tfg-results/suricata/http_benign

```



Example for FTP traffic:



```bash

sudo suricata -c /etc/suricata/suricata.yaml -r ~/tfg-results/pcaps/ftp_login/ftp_login_kali_to_victim.pcap -l ~/tfg-results/suricata/ftp_login

```



## View Suricata Output Files



```bash

ls -lh ~/tfg-results/suricata/http_benign

```



```bash

cat ~/tfg-results/suricata/http_benign/fast.log

```



The main Suricata files reviewed during the project were:



```text

fast.log

eve.json

stats.log

```



## Count Real Alerts Excluding Checksum Warnings



```bash

grep -v "invalid checksum" fast.log | wc -l

```



This command was used to separate real security alerts from technical checksum warnings.



## Count Checksum Warnings



```bash

grep -c "invalid checksum" fast.log

```



Checksum warnings were treated as technical noise related to the virtualised environment, not as real security alerts.



## Create a Suricata Alert Summary TSV



Example:



```bash

echo "experiment security_alert_count checksum_warning_count" > suricata_alert_summary.tsv

echo "http_benign 0 7" >> suricata_alert_summary.tsv

cat suricata_alert_summary.tsv

```



Summary files were created to make the results easier to compare across experiments.

