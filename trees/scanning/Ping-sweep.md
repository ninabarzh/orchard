# Ping sweep

## Attack tree

    1 Send out ICMP echo requests to every system on a particular 
    network or subset of a network to determine which hosts are up.

## Resources

* * [Nmap cheatsheet](../../resources/cheatsheets/Nmap-cheatsheet.md)

## Examples

    # nmap -sn -T4 -oG Discovery.gnmap 192.168.1.1/24
    # grep “Status: Up” Discovery.gnmap | cut -f 2 -d ' ' > LiveHosts.txt

## Notes

* If a service is listening on a port and someone makes a connection to it (by sending a SYN packet), the service will send a SYN/ACK packet in return. That means that there is a machine at that IP address.
* If no service is listening on that port but the machine is up and running and on the network, a reset (RST) packet will be sent back. That means there is nothing listening on that port, but having sent something in return means that a machine is at that IP address.
* If nothing is received after sending a SYN packet, it means there is no host at that IP address OR a firewall is blocking traffic OR the host is down. Port 80 is therefore extremely useful for ping sweeps, because most firewalls and port filters do not block web traffic.

|Send |Receive  |Send |Assumption  |
| --- | --- | --- | --- | 
|`SYN`|`SYN/ACK`|`ACK` followed by `RST`|Port is open, host is up|
|`SYN`|`RST`|-|Port is closed, host is up|
|`SYN`|Nothing|-|Port is blocked by firewall, host is down, or there is no host at that IP address|



