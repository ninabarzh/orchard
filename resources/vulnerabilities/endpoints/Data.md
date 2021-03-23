# Data

Data can be categorised as public data or private/protected data. All of us, individuals, organisations, governments, have confidential data that must be safeguarded from appearing in the public domain.

## Web applications

Unauthorised access to our data can occur due to a web application not properly protecting data. A lack of quality encryption and improper key generation is often cause. Luckily, this type of vulnerability is difficult to exploit.

### Mitigations
* Strict data encryption with a proven encryption technique
* Protect websites with the [HTTPS (SSL/TLS) protocol](../protocols/Transport-Layer-Security-Secure-Sockets-Layer-(TLS-SSL).md)
* Weaknesses in password hashing algorithms can be used to steal sensitive information stored on a web or application server. Use cryptographic hash functions to implement password hashing.
* Use third-party pentesting. Even the best senior programmers are susceptible to making mistakes. Review the application for potential vulnerabilities. For best results, do it regularly.