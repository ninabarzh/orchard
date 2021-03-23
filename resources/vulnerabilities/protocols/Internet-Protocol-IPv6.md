# Internet Protocol IPv6

The IPv6 header is a streamlined version of the IPv4 header. It eliminates fields that are unneeded or rarely used and adds fields that provide better support for real-time traffic. 

Extension headers are an intrinsic part of the IPv6 protocol and they support some basic functions and certain services:

* Hop-by-Hop is used for the support of Jumbo-grams or Multicast Listener Discovery (MLD).
* Destination is used in IPv6 Mobility and support of certain applications.
* Routing is used in IPv6 Mobility and in Source Routing. (disable “IPv6 source routing” on routers to protect against DDoS).
* Fragmentation is critical in support of communication using fragmented packets. In IPv6, the traffic source must do fragmentation while routers do not perform fragmentation of the packets they forward. Note: fragmentation can be used to evade network security controls. As a result, it is now required that the first fragment of an IPv6 packet contains the entire IPv6 header chain.
* Mobility is used in support of Mobile IPv6 service
* Authentication is similar to the IPv4 authentication header (rfc2402).
* Encapsulating Security Payload (ESP) is similar in format and use to the IPv4 ESP header (rfc2406). All information following the Encapsulating Security Header (ESH) is encrypted. It is inaccessible to intermediary network devices and can be followed by an additional Destination Options extension header and the upper layer datagram.

## Known vulnerabilities

### IPv6-over-IPv4 tunneling

This vulnerability has been known for years, but can in certain contexts (for example in MPLS networks) still be exploited. It can be used to avoid network congestion controls used to manage traffic, and also to gain access to networks.

### IP Spoofing

Falsifying the content in the Source IP header, usually with random numbers, to mask the sender's identity or to launch a DDoS attack. 

#### Mitigations
The threat of IP spoofing can be reduced (not completely eliminated) by:

* Packet filters are capable of filtering out and blocking packets with conflicting source address information (packets from outside the network that show source addresses from inside the network and vice-versa)
    * Ingress filtering for preventing IP addresses from coming into a network segment that should already be on that segment (RFC 2827).
    * Address allocation for preventing “private” addresses from entering or exiting a network segment (RFC 1918).
* Monitoring networks for atypical activity.
* Migrate sites to IPv6, making IP spoofing harder by including encryption and authentication.
* Developing protocols that do not rely on trust relationships (or as little as possible). Trust relationships only use IP addresses for authentication.
* ... 

## VPN Bypass through split tunneling
A VPN solution does not allow “split tunneling”, meaning all traffic is forced through the VPN. You think. All IPv4 traffic is forced over the VPN, IPv6 traffic completely bypasses it and if the system receives an IPv6 Router Advertisement it will immediately configure IPv6. This may include a global address, a default route, and a new DNS server. The new IPv6 address, default route, and DNS server will be preferred over the IPv4 options (rfc6724/3484). An adversary can inject a Router Advertisement to configure IPv6 on a user’s computer. And with control of DNS and IPv6, the attacker can:
* Sniff all client traffic
* Attempt a MitM attack
* Impersonate servers/systems and capture presented user credentials 
* Gain access to the network

### Mitigations
Make sure the VPN supports IPv6 allowing:
* Full support for either IPv4, IPv6 or both
* IPv6 over IPv4 and IPv4 over IPv6
* Blocking/disabling either IPv4 or IPv6
* VPN bypass of either IPv4 or IPv6 (only on purpose!)
* Application of ACLs for either IPv4 or IPv6
* Pushing firewall policies for either IPv4 or IPv6

## Rogue Router Advertisements

Extension headers/Upper Layer Protocols are not required to be in the first packet and if ULP information is not in the first packet, stateless ACLs can be bypassed.

Rogue router advertisements: [rfc6104 - Rogue IPv6 Router Advertisement Problem Statement](https://tools.ietf.org/html/rfc6104) for IPv6 can be used for denial-of-service or man-in-the-middle attacks. An adversary injects network nodes for example with a VPN Bypass and can flood the network with a (DoS) attack.

Another threat in RA comes from the ability to send DNS configuration over RA, so that an adversary can spoof that too: [rfc6106 - IPv6 Router Advertisement Options for DNS Configuration](http://tools.ietf.org/html/rfc6106)

### Mitigations
* [Methods to Mitigate against Rogue RAs](https://tools.ietf.org/html/rfc6104#section-3)

## Routing Header Type 0 attacks
The protocol specification for Internet Protocol version 6 (IPv6) was originally defined in RFC 1883 and then obsoleted by RFC 2460. These RFCs also define IPv6 extension headers that contain optional Internet-layer information encoded in separate headers. These headers may be inserted between the IPv6 header and the upper-layer header in an IPv6 packet. (applies to old Cisco routers)

### Mitigations
* [Countermeasures for IPv6 Type 0 Routing Headers](https://tools.cisco.com/security/center/resources/countermeasures_ipv6_type_0.html#7)

## Quad A query

Quad A queries can indicate which nodes on a network are IPv6-enabled (IPv6-enabled machines but not IPv6 enabled)










