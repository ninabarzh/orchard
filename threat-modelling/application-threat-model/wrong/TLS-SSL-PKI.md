# TLS/SSL PKI

SSL and TLS are commonly used by web browsers to protect connections between web applications and web servers. Many other TCP-based protocols use TLS/SSL as well, including email (SMTP/POP3), instant messaging (XMPP), FTP, VoIP, VPN, etc. ... 

## What can possibly go wrong?

* The Decrypting RSA with Obsolete and Weakened eNcryption (DROWN) vulnerability allows an attacker who has a man-in-the-middle to break the encryption of a TLS connection. It affects servers still supporting SSLv2 or servers that share a private key with any other server that allows SSLv2 (even for other protocols). 
* The Factoring RSA Keys (FREAK) vulnerability allows an attacker with a man-in-the-middle attack to reduce the security offered by SSL/TLS by forcing a connection to use “Export-grade” grade encryption – which reduces the RSA strength to 512 bits, which is easily breakable.
* The Bar Mitzvah attack recovers small amounts of plaintext data (the least significant bit of 100 bytes from the encrypted stream) from an SSL/TLS session protected using the RC4 cipher.
* The Sweet32 attack is a birthday attack against 64-bit block ciphers such as DES and 3DES and requires a man-in-the-middle attack capable of capturing a long-lived HTTPS connection (bypassing the protections offered by the secure flag on cookies by using a SOP bypass or cross-site scripting).
* The Padding Oracle On Downgraded Legacy Encryption (POODLE) attack was published in October 2014 and takes advantage of some servers/clients still supporting SSL 3.0 for interoperability and compatibility with legacy systems and a vulnerability in SSL 3.0 related to block padding.
* The Browser Exploit Against SSL/TLS (BEAST) attack involves determining the Initialisation Vector utilised as part of the encryption process but is limited in that it is only possible to retrieve small pieces of data, such as session tokens. The attacker must have a man-in-the-middle a connection and there must be a way of generating additional traffic (SOP bypass or cross-site scripting, requires an older browser). If session tokens are protected against XSS through ''HttpOnly'' cookies then an adversary can use BEAST to gain access to the tokens.
* The Compression Ratio Info-leak Made Easy (CRIME) requires a man-in-the-middle connection and the ability to repeatedly inject predictable data whilst monitoring the resulting encrypted traffic, for example by cross-site scripting attacks. For CRIME to be possible the client and server must support compression of the request before encryption. Both DEFLATE and SPDY (compression algorithms) are vulnerable.
* The Browser Reconnaissance and Exfiltration via Adaptive Compression of Hypertext (BREACH) vulnerability targets HTTP compression, not TLS compression. An adversary can force the victim’s browser to connect to a TLS-enabled third-party website after which she can monitor the traffic between the victim and the server using a man-in-the-middle attack. A vulnerable web application must satisfy the following conditions for the attack to work:
  * Be served from a server that uses HTTP-level compression
  * Reflect user input in HTTP response bodies
  * Reflect a secret (such as a CSRF token) in HTTP response bodies (therefore values in HTTP headers, such as cookies, are safe from this attack).
* Heartbleed was a critical vulnerability that was found in the heartbeat extension of the popular OpenSSL library. 

