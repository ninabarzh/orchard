# TLS/SSL PKI vulnerabilities

SSL and TLS are commonly used by web browsers to protect connections between web applications and web servers. Many other TCP-based protocols use TLS/SSL as well, including email (SMTP/POP3), instant messaging (XMPP), FTP, VoIP, VPN, etc. …

## Vulnerabilties

SSL version flaws, use of weak ciphers (less than 128 bit), certificate keys (less than 1024 bits), client vulnerabilities, server vulnerabilities, and application vulnerabilities. 

### Known vulnerabilties

* The Decrypting RSA with Obsolete and Weakened eNcryption (DROWN) vulnerability allows an attacker who has a man-in-the-middle to break the encryption of a TLS connection. It affects servers still supporting SSLv2 or servers that share a private key with any other server that allows SSLv2 (even for other protocols).
* The Factoring RSA Keys (FREAK) vulnerability allows an attacker with a man-in-the-middle attack to reduce the security offered by SSL/TLS by forcing a connection to use “Export-grade” grade encryption – which reduces the RSA strength to 512 bits, which is easily breakable.
* The Bar Mitzvah attack recovers small amounts of plaintext data (the least significant bit of 100 bytes from the encrypted stream) from an SSL/TLS session protected using the RC4 cipher.
* The Sweet32 attack is a birthday attack against 64-bit block ciphers such as DES and 3DES and requires a man-in-the-middle attack capable of capturing a long-lived HTTPS connection (bypassing the protections offered by the secure flag on cookies by using a SOP bypass or cross-site scripting).
* The Padding Oracle On Downgraded Legacy Encryption (POODLE) attack was published in October 2014 and takes advantage of some servers/clients still supporting SSL 3.0 for interoperability and compatibility with legacy systems and a vulnerability in SSL 3.0 related to block padding.
* The Browser Exploit Against SSL/TLS (BEAST) attack involves determining the Initialisation Vector utilised as part of the encryption process but is limited in that it is only possible to retrieve small pieces of data, such as session tokens. The attacker must have a man-in-the-middle a connection and there must be a way of generating additional traffic (SOP bypass or cross-site scripting, requires an older browser). If session tokens are protected against XSS through HttpOnly cookies then an adversary can use BEAST to gain access to the tokens.
* The Compression Ratio Info-leak Made Easy (CRIME) requires a man-in-the-middle connection and the ability to repeatedly inject predictable data whilst monitoring the resulting encrypted traffic, for example by cross-site scripting attacks. For CRIME to be possible the client and server must support compression of the request before encryption. Both DEFLATE and SPDY (compression algorithms) are vulnerable.
* The Browser Reconnaissance and Exfiltration via Adaptive Compression of Hypertext (BREACH) vulnerability targets HTTP compression, not TLS compression. An adversary can force the victim’s browser to connect to a TLS-enabled third-party website after which she can monitor the traffic between the victim and the server using a man-in-the-middle attack. A vulnerable web application must satisfy the following conditions for the attack to work:
    * Be served from a server that uses HTTP-level compression
    * Reflect user input in HTTP response bodies
    * Reflect a secret (such as a CSRF token) in HTTP response bodies (therefore values in HTTP headers, such as cookies, are safe from this attack).
* Heartbleed was a critical vulnerability that was found in the heartbeat extension of the popular OpenSSL library.

## Resources

* 2016-2183: The DES and Triple DES ciphers, as used in the TLS, SSH, and IPSec protocols and other protocols and products, have a birthday bound of approximately four billion blocks, which makes it easier for remote attackers to obtain cleartext data via a birthday attack against a long-duration encrypted session, as demonstrated by an HTTPS session using Triple DES in CBC mode, aka a “Sweet32” attack.
* CVE-2016-0800: The SSLv2 protocol, as used in OpenSSL before 1.0.1s and 1.0.2 before 1.0.2g and other products, requires a server to send a ServerVerify message before establishing that a client possesses certain plaintext RSA data, which makes it easier for remote attackers to decrypt TLS ciphertext data by leveraging a Bleichenbacher RSA padding oracle, aka a “DROWN” attack.
* CVE-2015-0204: The ssl3_get_key_exchange function in s3_clnt.c in OpenSSL before 0.9.8zd, 1.0.0 before 1.0.0p, and 1.0.1 before 1.0.1k allows remote SSL servers to conduct RSA-to-EXPORT_RSA downgrade attacks and facilitate brute-force decryption by offering a weak ephemeral RSA key in a noncompliant role, related to the “FREAK” issue. Also see CVE-2015-1637 and CVE-2015-1067.
* CVE-2015-2808: The RC4 algorithm, as used in the TLS protocol and SSL protocol, does not properly combine state data with key data during the initialization phase, which makes it easier for remote attackers to conduct plaintext-recovery attacks against the initial bytes of a stream by sniffing network traffic that occasionally relies on keys affected by the Invariance Weakness, and then using a brute-force approach involving LSB values, aka the “Bar Mitzvah” issue.
* CVE-2014-3566: The SSL protocol 3.0, as used in OpenSSL through 1.0.1i and other products, uses nondeterministic CBC padding, which makes it easier for man-in-the-middle attackers to obtain cleartext data via a padding-oracle attack, aka the “POODLE” issue.
* CVE-2011-3389: The SSL protocol, as used in certain configurations in Microsoft Windows and Microsoft Internet Explorer, Mozilla Firefox, Google Chrome, Opera, and other products, encrypts data by using CBC mode with chained initialization vectors, which allows man-in-the-middle attackers to obtain plaintext HTTP headers via a blockwise chosen-boundary attack (BCBA) on an HTTPS session, in conjunction with JavaScript code that uses (1) the HTML5 WebSocket API, (2) the Java URLConnection API, or (3) the Silverlight WebClient API, aka a “BEAST” attack.
* CVE-2012-4929: The TLS protocol 1.2 and earlier, as used in Mozilla Firefox, Google Chrome, Qt, and other products, can encrypt compressed data without properly obfuscating the length of the unencrypted data, which allows man-in-the-middle attackers to obtain plaintext HTTP headers by observing length differences during a series of guesses in which a string in an HTTP request potentially matches an unknown string in an HTTP header, aka a “CRIME” attack.
* CVE-2013-3587: A CVE Entry is marked as “RESERVED” when it has been reserved for use by a CVE Numbering Authority (CNA) or security researcher, but the details of it are not yet populated.
* CVE-2014-0160: The (1) TLS and (2) DTLS implementations in OpenSSL 1.0.1 before 1.0.1g do not properly handle Heartbeat Extension packets, which allows remote attackers to obtain sensitive information from process memory via crafted packets that trigger a buffer over-read, as demonstrated by reading private keys, related to d1_both.c and t1_lib.c, aka the Heartbleed bug.

### Mitigations

* Do not use SSL 3.0 on a server (this will be a problem if Internet Explorer 6.0 must still be supported). Use TLS 1.1 or TLS 1.2
* Most current browsers/servers use TLS_FALLBACK_SCSV. If a client requests a TLS protocol version that is lower than the highest supported by the server (and client), the server will treat it as an intentional downgrade and drop the connection.
* Do not accept an incorrect padding structure after decryption.
* Disable HTTP compression.
* Separate secrets from user input.
* Randomize secrets per request.
* Mask secrets (randomize by XORing with a random secret per request).
* Protect pages against injections.
* Hide length (for example by adding random numbers of bytes to responses).
* Limit the rate of requests.
* Use the latest version of OpenSSL or recompile the already installed version with -DOPENSSL_NO_HEARTBEATS.
* The NULL cipher suites inform the browser not to encrypt data, therefore nullifying any protection given through the use of SSL/TLS. Do not have NULL.
* Disable RC2 and SHA-1.
* Consider disabling RC4 (Bar Mitvah), DES and 3DES (Sweet32).

