# Ping sweep

## Attack tree

    1 Send out ICMP echo requests to every system on a particular 
    network or subset of a network to determine which hosts are up.


## Notes

* If a service is listening on a port and someone makes a connection to it (by sending a SYN packet), the service will send a SYN/ACK packet in return. That means that there is a machine at that IP address.
* If no service is listening on that port but the machine is up and running and on the network, a reset (RST) packet will be sent back. That means there is nothing listening on that port, but having sent something in return means that a machine is at that IP address.
* If nothing is received after sending a SYN packet, it means there is no host at that IP address OR a firewall is blocking traffic OR the host is down. Port 80 is therefore extremely useful for ping sweeps, because most firewalls and port filters do not block web traffic.

|Send |Receive  |Send |Assumption  |
| --- | --- | --- | --- | 
|`SYN`|`SYN/ACK`|`ACK` followed by `RST`|Port is open, host is up|
|`SYN`|`RST`|-|Port is closed, host is up|
|`SYN`|Nothing|-|Port is blocked by firewall, host is down, or there is no host at that IP address|

## Tools

* [Netenum](https://github.com/redcode-labs/Netenum)  
* [NMap](https://nmap.org/) can also be used for a simple ping sweep, but is a little bit more talkative.

## Examples

<img align="left" src="../assets/images/warning.png">_These are examples for demystification. Do not scan any devices that you do not have explicit permission to scan. If you do not own the devices I strongly recommend you get that permission in writing._   
<br/>
<br/>
`netenum` performs a basic ICMP ping and then replies with only the reachable targets. It requires a timeout to be specified. If that is not set, it delivers a CR-delimited dump of input-addresses. Below a time-out value of 5 is used for a CIDR of 192.168.1.1/24 

```
# netenum 192.168.1.1/24 5
192.168.1.1
192.168.1.10
192.168.1.13
192.168.1.250
```

`nmap` can also be used for a simple ping sweep, but is a little bit more talkative. The `-sP` means Perform a Ping Only Scan

```
# nmap -sP 192.168.1.1/24

Starting Nmap 7.60 ( https://nmap.org ) at 2018-03-24 11:32 EDT
Nmap scan report for 192.168.1.0
Host is up (0.00018s latency).
Nmap scan report for 192.168.1.1
Host is up (0.0039s latency).
Nmap scan report for 192.168.1.2
Host is up (0.00027s latency).

[snip]

Nmap scan report for pc2.home (192.168.1.10)
Host is up (0.027s latency).
Nmap scan report for 192.168.1.11
Host is up (0.00044s latency).
Nmap scan report for pc1.home (192.168.1.12)
Host is up (0.00021s latency).
Nmap scan report for pc19.home (192.168.1.13)

[snip]
```

