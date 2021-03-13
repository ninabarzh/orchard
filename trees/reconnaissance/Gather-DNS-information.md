# Gather DNS information

## Attack tree

    1 Use InterNIC (AND)
    2 Gather more details
        2.1 from RIR
        2.2 from other web sources
        2.3 from cli command

## Resources

* [DNS information](../../resources/cheatsheets/DNS-information.md)

## Examples

    # nmap -sn -T4 -oG Discovery.gnmap 192.168.9.1/24  
    Starting Nmap 7.91 ( https://nmap.org ) at 2021-03-13 18:47 UTC
    Nmap scan report for LEDE.lan (192.168.9.1)
    Host is up (0.00022s latency).
    MAC Address: C1:4F:B2:BD:1A:3E (Tp-link Technologies)
    Nmap scan report for machine.lan (192.168.9.173)
    Host is up (0.00025s latency).
    MAC Address: B3:BC:70:43:33:05 (Pegatron)
    Nmap scan report for kali.lan (192.168.1.89)
    Host is up.
    Nmap done: 256 IP addresses (3 hosts up) scanned in 2.04 seconds

Enumerating live hosts in a file 

    # grep "Status: Up" Discovery.gnmap | cut -f 2 -d ' ' > LiveHosts.txt  
         



