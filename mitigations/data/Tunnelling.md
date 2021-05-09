# Tunnelling 

A tunnel is a mechanism used to ship a foreign protocol across a network that normally wouldn't support it. Tunnelling enables the encapsulation of a packet from one type of protocol within the datagram of a different protocol. The complete IP packet to be sent from source to destination is encapsulated into another IP packet. This new packet has a legal internet IP address. For example, a VPN can use PPTP to encapsulate IP packets over a public network, such as the Internet. Most tunnelling protocols operate at layer 4, which means they are implemented as a protocol that replaces something like TCP or UDP. This concept can be used for anonymising.

Various types of tunnelling are useful for [circumventing censorship] as well, like [SSH](SSH.md), [VPN](VPN.md), [mixnets](Digital-mixing.md) like [Tor](Tor.md) and [I2P](I2P.md), and [chaining anonymising gateways](Chaining.md).

