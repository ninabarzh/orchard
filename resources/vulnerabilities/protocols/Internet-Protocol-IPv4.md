# Internet Protocol IPv4

Internet Protocol (IP) provides support at the network layer of the OSI model. IP provides for:

* Addressing
* Type of service specification
* Fragmentation and re-assembly
* Security

All transport protocol data packets such as UDP or TCP packets are encapsulated in IP data packets to be carried from one host to another. IP is a connection-less unreliable service, meaning there is no guarantee that the data will reach the intended host. The datagrams may be damaged upon arrival, out of order, or not arrive at all. IP is defined by [rfc791](https://tools.ietf.org/html/rfc791). Therefore the layers above IP such as TCP are responsible for being sure correct data is delivered.

IPv4 still routes most Internet traffic today, despite the ongoing deployment of a successor protocol, IPv6.

## Known vulnerabilities

IP is responsible for the transmission of packets between network end points. IP includes some features which provide basic measures of fault-tolerance (Time to Live, checksum), traffic prioritization (Type of Service) and support for the fragmentation of larger packets into multiple smaller packets (ID field, Fragment Offset). The support for fragmentation of larger packets provides a protocol allowing routers to fragment a packet into smaller packets when the original packet is too large for the supporting datalink frames.

### IP fragmentation exploits

IP fragmentation exploits (attacks) use the fragmentation protocol within IP as an attack vector.

### Denial of Service (DoS)

The IPv4 Fragmentation and Reassembly can be used to trigger a Denial of Service Attack (DOS). The receiving device will attempt reassembly following receipt of a frame containing a Flag field set to xx1, indicating more fragments are to follow. Receipt of such a frame causes the receiving device to allocate buffer resources for reassembly. If a device is flooded with separate frames, each with the Flag field set to xx1, but each has the Identification Field set to a different value, the device would attempt to allocate resources to each separate fragment in preparation for reassembly and would quickly exhaust its available resources while waiting for buffer time-outs to occur. To defend against such DOS attempts, many network security features include specific rules implemented at the Firewall that change the time-out value for how long they will hold incoming fragments before discarding them.

## Resources
* [Resolve IPv4 Fragmentation, MTU, MSS, and PMTUD Issues with GRE and IPsec](https://www.cisco.com/c/en/us/support/docs/ip/generic-routing-encapsulation-gre/25885-pmtud-ipfrag.html)


