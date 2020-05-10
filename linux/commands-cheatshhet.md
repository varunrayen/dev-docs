---
description: list of all commands that are used to get some useful information
---

# Commands Cheatsheet

### Show list of banned IP's by Fail2ban from iptables

```text
sudo iptables -L -n | awk '$1=="REJECT" && $4!="0.0.0.0/0"'
```

