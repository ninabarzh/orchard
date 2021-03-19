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

* Falsifying the content in the Source IP header, usually with random numbers, to mask the sender's identity or to launch a DDoS attack (IP Spoofing)
* Routing Header Type 0 attacks (old Cisco routers)
* Quad A queries can indicate which nodes on a network are IPv6-enabled (IPv6-enabled machines but not IPv6 enabled)
* Rogue router advertisements for IPv6 (can be used for denial-of-service or man-in-the-middle attacks)

## Mitigations

### IP Spoofing

The threat of IP spoofing can be reduced (not completely eliminated) by:

* Packet filters are capable of filtering out and blocking packets with conflicting source address information (packets from outside the network that show source addresses from inside the network and vice-versa)
    * Ingress filtering for preventing IP addresses from coming into a network segment that should already be on that segment (RFC 2827).
    * Address allocation for preventing “private” addresses from entering or exiting a network segment (RFC 1918).
* Monitoring networks for atypical activity.
* Migrate sites to IPv6, making IP spoofing harder by including encryption and authentication.
* Developing protocols that do not rely on trust relationships (or as little as possible). Trust relationships only use IP addresses for authentication.
* ...






