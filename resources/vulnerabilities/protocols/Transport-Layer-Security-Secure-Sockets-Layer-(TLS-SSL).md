# Transport Layer Security-Secure Sockets Layer (TLS-SSL)

Regardless of server based protections and [TLS/SSL PKI based encryption](../../../E2EE-threat-model/threats/TLSSSL-PKI-vulnerabilities.md), the majority of HTTPS servers are vulnerable to connection hijacking attacks and the most common attack is simply luring a person to run a shell on his own machine/host by using social engineering techniques, leading to further [phishing](../../../trees/social-engineering/Phishing.md), [pharming](../../../trees/social-engineering/Pharming.md) and [man-in-the-middle](../../../trees/social-engineering/Phishing.md) attacks.

## The usual suspects

* In a [Decrypting RSA with Obsolete and Weakened eNcryption (DROWN)](https://drownattack.com/drown-attack-paper.pdf) attack an adversary breaks the encryption (in a way similar to the Bleichenbacher RSA padding-oracle attack) and reads or steals sensitive communications. Requirements:
    * Any protocol suite including TLSv1.2 as long as the requirement for SSLv2 is also met (OR)
    * A server that shares a private key (RSA key exchange) with any other server that allows SSLv2 (even for other protocols such as email).
* In a [Browser Exploit Against SSL/TLS (BEAST)](https://www.acunetix.com/blog/web-security-zone/what-is-beast-attack/) attack an adversary determines the Initialisation Vector of the encryption process by which she retrieves small pieces of data, for example session tokens. It is a highly unlikely attack. Requirements:
    * A vulnerable version of SSL/TLS must be in use, with a block cipher
    * A man-in-the-middle attack 
    * A way of generating additional traffic such as an SOP bypass or a XSS vulnerability (injection of JavaScript or an Applet into the same origin of the target web application), for example a web application with server-side CORS headers that override the default same-origin policy.
    * A user using an older web browser
    * Session tokens which are protected against XSS through mechanisms such as HttpOnly cookies

### Crimes against compression
* In a [Compression Ratio Info-leak Made Easy (CRIME)](https://www.acunetix.com/vulnerabilities/web/crime-ssl-tls-attack/) an adversary makes a MitM connection and repeatedly injects (for example through XSS) predictable data whilst monitoring the resulting encrypted traffic. Compression algorithms which compress HTTP requests by eliminating duplicate strings are vulnerable to CRIME, which takes advantage of the method in which duplicate strings are eliminated to guess session tokens by systematically brute-forcing them. Requirements for CRIME: 
    * Client and server support compression at the SSL/TLS level (both the header and body are subjected to compression) of the request before encryption, for example by using SPDY. 
    * JavaScript is not required, a HTML Injection could work (but is not very efficient).
* A [Browser Reconnaissance and Exfiltration via Adaptive Compression of Hypertext (BREACH)](http://www.breachattack.com/) is an instance of CRIME against HTTP Compression (CRIME attacks TLS SPDY, while BREACH attacks HTTP gzip/DEFLATE). Turning off TLS compression has no affect on BREACH as it exploits the underlying HTTP compression. The attack follows the basic steps of the CRIME attack and there are several methods to remediate the issue, such as disabling HTTP compression, protecting the application from CSRF attacks, randomising CSRF tokens per request to prevent them being captured, obfuscating the length of page responses by adding random amounts of arbitrary bytes to the response. To be vulnerable, a web application must:
    * Be served from a server that uses HTTP-level compression
    * Reflect user-input in HTTP response bodies
    * Reflect a secret (such as a CSRF token) in HTTP response bodies

