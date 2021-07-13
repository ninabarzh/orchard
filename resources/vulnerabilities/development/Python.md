# Python

The most common Python vulnerabilities ([CVE's with keyword Python](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=JavaScript):

* Some of the most common attacks are [SQL injection attacks](../../../trees/application-hacking/SQL-injection.md), [XSS attacks](../../../trees/web-hacking/XSS.md) and [Cross-site request forgery (CSRF)](../../../trees/web-hacking/CSRF.md) injection attacks. These types of attacks can impact not just the language but the environment as a whole.
* [DoS](../../../trees/network-attacks/DoS.md) and [DDoS](../../../trees/network-attacks/DDoS.md) styled attacks based on XML parsing attack vectors (using an XML standard library module, especially external XML files).
* `mltemp()` when used for creating temp files as a different process may also create a file with this name to attempt to load the wrong data or expose other temporary data.
