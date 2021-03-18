# Internet Control Message Protocol (ICMP)

Compared to other IP protocols the Internet Control Message Protocol (ICMP) is fairly small and is defined by [rfc792](https://tools.ietf.org/html/rfc792) and [rfc1122](https://tools.ietf.org/html/rfc1122). It belongs to the IP layer of TCP/IP but relies on IP for support at the network layer. ICMP messages are encapsulated inside IP datagrams. ICMP only reports errors involving fragment 0 of any fragmented datagrams. The IP, UDP or TCP layer will usually take action based on ICMP messages.

ICMP serves a large number of disparate functions. At its core ICMP was designed as the debugging, troubleshooting, and error reporting mechanism for IP. The errors reported by ICMP are generally related to datagram processing. ICMP will report the following network information:

* Timeouts
* Network congestion
* Network errors such as an unreachable host or network.
* The ping command is also supported by ICMP.

## Vulnerabilities

Most routers come with the option to set the router to ignore or drop ICMP Redirects because they can be used to attack networks by confusing hosts as to where the correct default gateway is.

### Man In The Middle (MITM)

ICMP Redirects can be used to set up Man-in-the-Middle without LAN access. An ICMP Redirect message is typically used to notify routers of a better route, and can be spoofed to reroute a victim's traffic through an attacker controlled router. Many routers have static routes or do not accept/process ICMP Redirect packets, but some still do.

### Ping O’ Death

The variable size of the ICMP packet data section has been exploited a lot. In the well-known Ping O' Death, large or fragmented ping packets are used for denial-of-service attacks. ICMP can also be used to create covert channels for communication (see the LOKI exploit).

## Mitigation

When people talk about blocking ICMP they're really talking about ping and traceroute. The first can be used to determine if a host is alive, and Time Exceeded as part of traceroute, can be used to to map out network architectures, or void forbid, a Redirect(type 5 code 0) to change the default route of a host.

Reasons why it may not be a good idea to restrict ICMP as a whole:

* Path MTU Discovery - A combination of the Don't Fragment flag and type 3 code 4 (Destination Unreachable - Fragmentation required, and DF flag set) can be used to determine the smallest MTU on the path between the hosts. This way fragmentation during the transmission can be avoided.
* Active Directory requires clients ping the domain controllers in order to pull down GPOs. ping is used to determine the “closest” controller and if none respond, then it is assumed that none are close enough. So the policy update doesn't happen.
* ...



