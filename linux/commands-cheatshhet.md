---
description: list of all commands that are used to get some useful information
---

# Commands Cheatsheet

> For Ubuntu 16.04 & 18.04

### Enable SSH Root access

```text
vim /etc/ssh/sshd_config
PermitRootLogin yes
sudo service sshd restart
```

### Show list of banned IP's by Fail2ban from iptables

```text
sudo iptables -L -n | awk '$1=="REJECT" && $4!="0.0.0.0/0"'
```



