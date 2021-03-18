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

* Routing Header Type 0 attacks (old Cisco routers)
* Quad A queries can indicate which nodes on a network are IPv6-enabled (IPv6-enabled machines but not IPv6 enabled)
* Rogue router advertisements for IPv6 (can be used for denial-of-service or man-in-the-middle attacks)




