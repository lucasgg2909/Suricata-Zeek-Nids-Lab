\# Experiment Overview



This file summarises the main experiments carried out in the Suricata and Zeek NIDS/NDR lab.



| Experiment | Traffic Type | Suricata Result | Zeek Result | Main Observation |

|---|---|---|---|---|

| Nmap scan | Reconnaissance | Detected Nmap User-Agent | Logged connections, services and HTTP User-Agent | Suricata alerted while Zeek provided wider context |

| HTTP benign | Normal HTTP traffic | No real security alerts | Logged HTTP requests and curl User-Agent | Suricata ignored benign traffic while Zeek logged it |

| SSH failed login | Authentication failure | No alerts | Logged SSH activity with auth\_success = F | Zeek provided authentication context |

| SSH successful login | Legitimate SSH session | No real security alerts | Logged SSH session with auth status unknown | Zeek saw the session but did not confirm success |

| SMB enumeration | Service enumeration | Limited alert/context output | Logged connections to ports 139 and 445 | Zeek provided connection-level visibility |

| FTP login | FTP protocol activity | No alerts | Logged FTP command activity | Zeek provided protocol-level detail |

