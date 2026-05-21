# 01 - Network Validation Commands

These commands were used to verify the network configuration, connectivity and traffic visibility between the lab machines.

## Check IP Configuration

```bash
ip a
```

This command was used on Kali Linux, Ubuntu Victim and Ubuntu Monitor to confirm the assigned IP addresses.

Expected IP addresses:

```text
Kali Linux:      192.168.56.30
Ubuntu Victim:   192.168.56.10
Ubuntu Monitor:  192.168.56.20
```

## Ping Connectivity Tests

From Kali to Ubuntu Victim:

```bash
ping 192.168.56.10
```

From Kali to Ubuntu Monitor:

```bash
ping 192.168.56.20
```

These tests confirmed that the lab machines could communicate inside the IDS-LAB network.

## Check Open Services on Ubuntu Victim

```bash
ss -tulnp | grep -E ':21|:22|:80|:139|:445'
```

This command was used to confirm that FTP, SSH, HTTP and SMB-related services were listening on Ubuntu Victim.

Expected ports:

```text
21/tcp   FTP
22/tcp   SSH
80/tcp   HTTP
139/tcp  NetBIOS/Samba
445/tcp  SMB/Samba
```

## Check Traffic Visibility on Ubuntu Monitor

```bash
sudo tcpdump -i enp0s3
```

This command was used to confirm that Ubuntu Monitor could observe traffic on the IDS-LAB interface.