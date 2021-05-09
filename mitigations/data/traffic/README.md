# Anonymising traffic

Network traffic visibility is the beginning of security.

Public networks like the internet are extremely vulnerable to traffic monitoring and surveillance. The most obvious way you can be tracked is by IP address. Packet headers identify the IP addresses of the recipient(s) and the packet routes can rather easily be tracked. There are many ways to change your IP address. And protecting ones IP address is not enough. Some applications and devices append extra headers to packets or other revealing data that can be correlated.

* Depending on your situation and on why you wish to remain anonymous, consider plausible deniability and installing local traffic monitoring so you can check for leaks in your traffic yourself. There is no better way for staying (relatively) calm under near-paranoia circumstances than to not to have to depend on others.
* It is clear that browsing and email have the most low cost attack vectors for data theft and other hacks, tracking by corporations and for governmental spying. Learning about [safer browsing](Safer-browsing.md) and securing email is overall a good investment of time and energy.
* MAC addresses are used in the media access control protocol sub layer of the ISO/OSI model. It can be and often is used by networking equipment to track users. This means that proxy hopping on a network that has already authenticated your hardware is utterly useless. [Changing MAC address](Change-MAC-address.md) is not that hard to do. And if you do, also renew your IP lease.
* If and when you connect in a public space over a wireless access point, anyone in the area with a packet sniffer can see your "nickname". [It can be changed](Change-nickname.md).
* Use [tunnelling](Tunnelling.md) software.
* Admins of servers and websites need to be aware of [applications](Web-applications.md) they use that can give away information about identity and protect file transfer and login identities.

