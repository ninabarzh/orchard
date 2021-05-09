# Choosing a VPN

Virtual Private Networks can be used for connecting to private networks over public networks (internet). A VPN client communicates over the internet and sends the computer’s network traffic through the encrypted connection to a VPN server. The encryption provides a (more or less) secure connection, which means it is made harder for adversaries to snoop on the connection and see sensitive information. 

  * VPN solutions based on Point-to-Point Tunnelling Protocol (PPTP),  Layer Two Tunnelling Protocol (L2TP), Secure Socket Tunnelling Protocol (SSTP), or Internet Key Exchange (IKEv2) depend heavily on the features originally specified for Point-to-Point Protocol (PPP). PPP was designed to send data across dial-up or dedicated point-to-point connections. For IP, PPP encapsulates IP packets within PPP frames and then transmits the encapsulated PPP-packets across a point-to-point link. PPP was originally defined as the protocol to use between a dial-up client and a network access server. These is known as Layer 2 tunnelling, using //datalink layer frames// to encapsulate data payloads. 
  * Layer 3 tunnelling uses //network layer tunnelling protocols//, such as IPSec in the tunnel mode and IP over IP, for the exchange of data packets. These protocols use packets as a medium of exchange. Layer 3 tunnelling involves the addition of a new IP header to an IP packet before sending them across a tunnel created over an IP-based network. 
  * VPNs using OpenVPN access the service on the application layer level.

Routed vs bridged VPN: 
|Feature |Layer 2 Tunnelling (Bridging)|Layer 3 Tunnelling (Routing)|
| :--- | :--- | :--- |
|Protocol support|Provides support for various network protocols.|Provides support for only IP-based networks.|
|Authentication|Supports user-based authentication using authentication protocols. Hardware-based authentication mechanisms, such as tokens and smart cards, are supported using EAP.|Supports device-based authentication methods, such as digital certificates.|
|Assignment of IP addresses|Supports dynamic assignment of IP addresses to VPN clients by the VPN server at the time of connection establishment.|IP addresses are assigned prior to the creation of a tunnel.|
|Encryption|Supports encryption mechanisms and cryptographic algorithms|Supports similar encryption mechanisms as Layer 2 tunnelling protocols. IPSec provides strong encryption.|

When a client connects via bridging to a remote network, it is assigned an IP address that is part of the remote physical Ethernet subnet and is then able to interact with other machines on the remote subnet as if it were connected locally. When the connection is done via routing, the client uses its own separate subnet, and routes are set up on both the client machine and remote gateway so that data packets will seamlessly traverse the VPN. The "client" is not necessarily a single machine. It could be a subnet of several machines.

Bridging and routing are functionally very similar, with the major difference being that a routed VPN will not pass IP broadcasts while a bridged VPN will. Choose bridging only when:

  * the VPN needs to be able to handle non-IP protocols
  * you are running applications over the VPN which rely on network broadcasts (such as LAN games)
  * avoiding setting up a Samba or WINS server for MS file sharing across a VPN.

[Bitmask](https://github.com/leapcode/bitmask-vpn) is an open source application to provide easy and secure encrypted communication. You can choose among several different service providers (like [Riseup](https://riseup.net/en/vpn) or [Calyx](https://calyxinstitute.org/projects/digital-services/vpn)), or start your own. 











