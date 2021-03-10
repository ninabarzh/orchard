# Port scanning

The most common type of scan in the discovery phase is a `SYN` scan (or SYN stealth scan), named for the `TCP SYN` flag used in the `TCP` connection sequence. To perform the default SYN (`-sS`)scans, privileges are required. If privileges are insufficient a TCP connect (`-sT`) scan is used. 

## Attack tree

    1 Port scanning (AND)
        1.1 Do a TCP scan (OR)
                1.1.2 Use the default SYN (`-sS`)scans (privileges are required) (OR)
                1.1.3 Use the connect (`-sT`) scan (privileges are not required)
        1.2 Do a UDP scan
    2 Check for potential known problems with found ports

## Tools

There are many different ports scanners that all operate in pretty much the same way. 

* [NMap](https://nmap.org/) 
* [OpenVAS](https://www.openvas.org/)
* [Metasploit](https://www.metasploit.com/)
* [Netenum](https://github.com/redcode-labs/Netenum)
* [Unicornscan](https://www.aldeid.com/wiki/Unicornscan)
* [IKE-scan](https://github.com/royhills/ike-scan)

## Resources

* [Ports Database](https://www.speedguide.net/ports.php), a comprehensive, searchable database of official and unofficial tcp/udp port[1] assignments, known vulnerabilities, trojans, applications use and more. 

## Notes

* SYN scans are relatively fast and stealthy because the handshake is not completed: a `SYN` packet is sent, the return is analysed, a determination is made about the state of the system or port (`SYN/ACK` or `RST`), but the final packet to make the connection is not sent and as a result, the target machine does not see a full connection and usually does not log the transactions.
* To bypass some access controls, the `TCP` flags `FIN`, `PSH` and `URG` can be used. Different systems respond differently to these packets and they can also be used to get indicators for detecting which OS is running on the target. 

|Flags 	|Type of packet sent 	|Response if open 	|Response if closed 	|Purpose  |
| --- | --- | --- | --- | --- |
|`-sF`|TCP packet with FIN flag set|Connection timeout|`RST`|Bypass nonstateful firewalls  |
|`-sX`|TCP packet with FIN, PSH and URG flag set|Connection timeout|`RST`|Bypass nonstateful firewalls  |
|`-sM`|TCP packet with FIN/ACK flag set|Connection timeout|`RST `|Works for some BSD systems  |

* TCP scans are faster and more productive, but many admins focus on securing TCP based services and do not pay much attention to UDP-based services, and it might just give another entry point into the target system, especially if those include infrastructure devices and SunOS/Solaris systems. 
* IPsec VPN servers generally will not be detected by a port scan. This is because they don't listen on any TCP ports, so a TCP port scan won't find them. What is more, they don't normally send ICMP unreachable messages, so a UDP port scan won't pick up IKE on port 500 (a standard port for such connections) and a raw IP scan won't pick up ESP or AH with IP protocols 50 and 51. In addition, the IPsec RFCs specify that incorrectly formatted packets should be ignored, so sending random garbage to UDP port 500 or IP protocols 50 and 51 will not normally elicit any response either. An effective way to detect IPsec VPN systems is to send a correctly formatted IKE packet to each of the systems that you want to check, and display any IKE responses that are received. This method is able to detect IPsec VPNs that use IKE for key exchange and do not restrict the source IP addresses that they will respond to. In practice, almost all modern IPsec implementations use IKE; the alternative is manual key exchange, which is very rare nowadays. The ike-scan program allows us to send an IKE packet to the specified target systems and display the responses. 



## Examples

<img align="left" src="../assets/images/warning.png">_These are examples for demystification. Do not scan any devices that you do not have explicit permission to scan. If you do not own the devices I strongly recommend you get that permission in writing._   
<br/>
<br/>

The SYN scan makes the first part of the TCP connection (SYN flag set). If it receives a packet with the `RST` flag set in return, nmap assumes the port is closed. If it receives a response (`SYN/ACK` flag set), instead fo acknowledging that packet like a normal connection would, nmap sends an `RST` packet. The three-way handshake is never completed, it may not be logged by the server. Because of the required manipulation of flags, this type of scan can not be done without root access to the system one is scanning from. 

TCP SYN scan:
```
# nmap -sS 192.168.1.1

Starting Nmap 7.60 ( https://nmap.org ) at 2018-03-24 12:32 EDT
Nmap scan report for 192.168.1.1
Host is up (0.096s latency).
Not shown: 989 filtered ports
PORT      STATE  SERVICE
23/tcp    closed telnet
53/tcp    open   domain
80/tcp    open   http
113/tcp   closed ident
135/tcp   closed msrpc
139/tcp   open   netbios-ssn
443/tcp   open   https
445/tcp   open   microsoft-ds
631/tcp   open   ipp

Nmap done: 1 IP address (1 host up) scanned in 24.59 seconds
```
A `TCP` connect requires a full `TCP` connection to be established (the use of all of the steps involved in the standard TCP three-way handshake) and therefore is a slower scan. Many firewalls or hosts will not respond to ping, and these could be missed unless you select the `-Pn` parameter. Of course this can make scan times much longer as you could end up sending scan probes to hosts that aren't there.
TCP connect scan:
```
# nmap -sT 192.168.1.1

Starting Nmap 7.60 ( https://nmap.org ) at 2018-03-24 12:19 EDT
Nmap scan report for 192.168.1.1
Host is up (0.025s latency).
Not shown: 991 filtered ports
PORT      STATE  SERVICE
23/tcp    closed telnet
53/tcp    open   domain
80/tcp    open   http
113/tcp   closed ident
135/tcp   closed msrpc
139/tcp   open   netbios-ssn
443/tcp   open   https
445/tcp   open   microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 14.30 seconds
```
Scan selected ports - ignore discovery:
```
nmap -Pn -F 192.168.1.1

Starting Nmap 7.60 ( https://nmap.org ) at 2018-03-24 12:38 EDT
Nmap scan report for 192.168.1.1
Host is up (0.015s latency).
Not shown: 89 filtered ports
PORT      STATE  SERVICE
23/tcp    closed telnet
53/tcp    open   domain
80/tcp    open   http
113/tcp   closed ident
135/tcp   closed msrpc
139/tcp   open   netbios-ssn
443/tcp   open   https
445/tcp   open   microsoft-ds
631/tcp   open   ipp

Nmap done: 1 IP address (1 host up) scanned in 2.00 seconds
```

UDP scanning is more difficult than TCP scanning because it is a connectionless protocol and does not use a handshake. Instead, the source sends an UDP packet to destination. Destination then checks to see if the port/protocol is active and then takes appropriate action.

And therein lies the challenge. If receiving a response it will either be:

* An ICMP type 3 message if the port is closed (and the firewall allows the traffic)
* A disallowed message from the firewall
* A response from the service itself

If not receiving a response it could mean that the port is open, but it can also mean that the packet was blocked and did not reach the destination. 

UDP scan:

```
# nmap -sU -p 123,161,162 192.168.1.1

Starting Nmap 7.60 ( https://nmap.org ) at 2018-03-24 12:51 EDT
Nmap scan report for 192.168.1.1
Host is up (0.00099s latency).

PORT    STATE         SERVICE
123/udp open|filtered ntp
161/udp open|filtered snmp
162/udp open|filtered snmptrap

Nmap done: 1 IP address (1 host up) scanned in 1.52 seconds
```
