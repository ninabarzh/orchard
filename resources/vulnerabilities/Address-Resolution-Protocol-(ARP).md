# Address Resolution Protocol

The Address Resolution Protocol is a network layer protocol used to convert an IP address into a physical address, such as an Ethernet address. A host wishing to obtain a physical address broadcasts an ARP request to the TCP/IP network. The host on the network that has the IP address in the request then replies with its physical hardware address. See [rfc826](https://tools.ietf.org/html/rfc826) and [Network sourcery ARP](http://networksorcery.com/enp/protocol/arp.htm).

It is used when IPv4 is used over Ethernet. In IPv6, ARP and RARP are replaced by a neighbour discovery protocol called Neighbour Discovery (ND), which is a subset of the control protocol Internet Control Message Protocol (ICMP).

## Known vulnerabilities

ARP Spoofing and ARP Poisoning are the most ignored, long-standing vulnerabilities.

### ARP poisoning

ARP poisoning is a method used for manipulating the flow of traffic between arbitrary hosts on a local area network: ARP messages contain the IP address of a network resource, such as the default gateway, or a DNS server, and replaces the MAC address for the corresponding network resource with its own MAC address. Network devices, by design, overwrite any existing ARP information in conjunction with the IP address, with the new, fake ARP information. The attacker then takes the role of man in the middle; any traffic destined for the legitimate resource is sent through the attacking system. This attack occurs on the lower levels of the stack and the end-user is oblivious to the attack happening.

ARP poisoning is also capable of executing Denial of Service (DoS) attacks. The attacking system, instead of posing as a gateway and performing a man in the middle attack, can simply drop the packets, causing the clients to be denied service to the attacked network resource.

### Man in the Middle (MitM)

In an ARP MITM attack a MAC address is spoofed within a LAN in response to a victim's ARP request. If the MAC is successfully spoofed with the attacker's machine, then the victim will send traffic to the spoofed MAC address instead of the destination MAC address. The attack must be executed from within the victim's LAN and respond faster than the actual destination ARP response.

If an endpoint accepts requests from a different domain when sent in conjunction with ARP spoofing + man in the middle (MiTM) attack, the door is open for a CSRF attack.

### MAC flooding

By flooding a network device with data packets, the translation table can go haywire and the connection between the ports and specific MAC addresses can be destroyed. Any data that is intended for a single MAC address is now sent out on all ports associated with the network. This means that any type of data that was intended for a single address is received by multiple addresses.

Via MAC flooding an attacker can gain access to all sorts of data, including system passwords, protected files, and even email and instant messaging conversations. Because of the security risk that MAC flooding represents, many switches today can be configured to either provide extra security to specific MAC addresses, or to even shut down the network device in the event too much data floods into a given port.


