# What can possibly go wrong?

* Note: many attacks on organisational applications come from inside the network. 
* Intrusion detection techniques will not work when the problem is poor input validation in the application.
* Network and host security fails. Development and production environment are not locked down.
* Authentication mechanism to control which users are allowed to access which data, such as [TLS/SSL PKI](TLS-SSL-PKI.md) are not in place or not carefully implemented: SSL version flaws, use of weak ciphers (< `128 bit`), certificate keys (< `1024 bit`), client vulnerabilities, server vulnerabilities, and application vulnerabilities.
* Properly [locked-down clients](../../../mitigations/pc) can not interact with the application, meaning security aware users have to run risks to use it.  
* [The most common programming language vulnerabilities](Programming-language-vulnerabilities.md) are not [mitigated](../../../mitigations/application/coding). 