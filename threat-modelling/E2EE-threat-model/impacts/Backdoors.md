# ↑ Backdoors

With the advance of E2EE, secret services will still want access to our data and the amount of [Ghost protocols](../attack-vectors/Ghost-protocols.md) and [backdoors](../attack-vectors/Backdoor.md) is likely to increase.

Protecting against backdoors can be difficult, but there are some things that can help reduce the risk of a breach of this kind.

### Individuals
* Most backdoors can be removed by reinstalling the system from a backup that is clean and was kept secure.
* Pay special attention to open-source based software. Open-source projects have hundreds of (mirroring) sites (an enormous attack surface). Be picky, very picky.
* Use firewalls that block entry points from all but authorised users, making a port binding backdoor attack nearly impossible.

### Organisations
* Robust network monitoring, meaning including intrusion detection systems (IDS) and intrusion prevention systems (IPS). Monitoring can help detect information being gathered by a command and control server and flag it with network administrators.
* Some backdoors emulate network traffic, but a machine learning program may still catch those.


