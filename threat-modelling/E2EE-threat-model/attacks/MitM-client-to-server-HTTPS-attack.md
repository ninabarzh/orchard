# MitM client-to-server HTTPS attack

* A passive MitM attack (only sniffing), decrypting the traffic by using the servers private key, is possible when RSA key exchange is used. Diffie-Hellman key exchange causes forward secrecy, which means that previously sniffed connections can not be decrypted once an adversary has the private key of the certificate.
* An active MitM attack consists of an encrypted session from client to MitM and from MitM to server. Two fully separate sessions which have different keys and can also use a different cipher, protocol version etc. If an adversary has the servers original private key he/she can impersonate the server by using the original certificate. Alternatively a fake certificate can be created and used, which succeeds only if the client already trusts the CA issuing the fake certificate or the client does not do proper certificate validation.
* Client certificates are similar to server certificates: either the adversary has to have the private key of the original certificate or the server needs to somehow trust the attackers fake certificate or fails to properly validate the certificate.

## Mitigations

A tremendous amount of work.

* Secure all vulnerable endpoints on the network
* Ensure users are using secure connections.
* Use static ARP tables.

