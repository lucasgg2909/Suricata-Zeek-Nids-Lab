# 02 - Traffic Generation Commands



These commands were used from Kali Linux to generate controlled traffic towards Ubuntu Victim.



## Nmap Reconnaissance Scan



Initial scan:



```bash

nmap 192.168.56.10

```



Scan with service and version detection:



```bash

nmap -sS -sV 192.168.56.10

```



Scan focused on the common service ports used in the lab:



```bash

nmap -sS -sV -p 21,22,80,139,445 192.168.56.10

```



## Nmap SYN Scan



```bash

nmap -sS 192.168.56.10

```



This was used to generate TCP SYN scan traffic from Kali to Ubuntu Victim.



## Benign HTTP Traffic



HEAD request:



```bash

curl -I http://192.168.56.10

```



GET request:



```bash

curl http://192.168.56.10

```



Repeated HTTP requests:



```bash

for i in {1..7}; do curl http://192.168.56.10; done

```



These commands were used to generate normal HTTP traffic towards the Apache service running on Ubuntu Victim.



## SSH Failed Login Test



The SSH failed login experiment used a test user and a small password list.



Create or edit the password list:



```bash

nano ssh_passwords.txt

```



Example password list used for the controlled test:



```text

password

admin

123456

wrongpass

test123

```



Hydra command used to generate failed SSH login attempts:



```bash

hydra -l sshuser -P ssh_passwords.txt -t 2 -V ssh://192.168.56.10

```



This was used only inside the isolated lab environment to generate controlled failed authentication traffic.



## SSH Successful Login



```bash

ssh sshuser@192.168.56.10

```



Example lab password:



```text

CorrectPass123!

```



This password was created only for the isolated lab environment and was not a real credential.



## SMB Enumeration



SMB share enumeration using smbclient:



```bash

smbclient -L //192.168.56.10 -N

```



Nmap SMB script scan:



```bash

nmap -sS -sV -p 139,445 --script smb-protocols,smb-os-discovery 192.168.56.10

```



These commands were used to generate SMB-related traffic towards the Samba services on Ubuntu Victim.



## FTP Login



Start FTP session:



```bash

ftp 192.168.56.10

```



Example FTP commands used during the session:



```text

pwd

ls

quit

```



This generated basic FTP protocol activity between Kali and Ubuntu Victim.

