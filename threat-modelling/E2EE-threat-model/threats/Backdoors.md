# Backdoors

Backdoors do not come only as applications that allow for remote access to computers, hardware components including authentication tokens, network appliances, surveillance systems and certain communication infrastructure devices can also have backdoors.

Adversaries typically install backdoors to access the system again at some later date and are often used in targeted attacks for breaking into the infrastructure without being discovered (port binding, connect-back, connect availability use and legitimate platform abuse). Used in the second (point of entry) or third (command-and-control [C&C]) stage of a targeted attack process, backdoors are often designed to bypass intrusion detection systems (IDS) and enable adversaries to gain command and control of a network.

## Mitigations

Protecting against backdoors can be difficult, but there are some things that can help reduce the risk of a breach of this kind.

### Individuals
* Most backdoors can be removed by reinstalling the system from a backup that is clean and was kept secure.
* Pay special attention to open-source based software. Open-source projects have hundreds of (mirroring) sites (an enormous attack surface). Be picky, very picky.
* Use firewalls that block entry points from all but authorised users, making a port binding backdoor attack nearly impossible.

### Organisations
* Robust network monitoring, meaning including intrusion detection systems (IDS) and intrusion prevention systems (IPS). Monitoring can help detect information being gathered by a command and control server and flag it with network administrators.
* Some backdoors emulate network traffic, but a machine learning program may still catch those.


