# Programming language vulnerabilities

## JavaScript

The most common JavaScript vulnerabilities ([CVE's with keyword JavaScript](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=JavaScript)):

* [XSS attacks](../../../trees/web-hacking/Cross-Site-Scripting-(XSS).md) use data containing special characters in the HTML, JavaScript, or CSS of a web page. When the browser renders the page, it interpret those as part of the code instead of as a value to be displayed. This can be used to add additional browser-side code that gets executed.
* Adversaries can also use special tools to send data directly to the server, entirely avoiding client-side validations and allowing entry of potentially malicious or unverified data.
* Client-side browser scripts have access to all of the content returned by a web application to the browser, and this includes cookies and tokens that could contain sensitive data (user session IDs). The usual exploit of XSS is to hijack the session.
* [Cross-site request forgery (CSRF)](../../../trees/web-hacking/Cross-Site-Request-Forgery-(CSRF).md) attacks trick a browser into executing malicious requests on the websites the user is already logged in to (an may not necessarily be visited at that time). If sessions on the target site are cookie-based, requests to that site can be automatically enriched with authorisation cookies. Adversaries can implement their own web pages and execute malicious requests to other sites in the background when the user opens the site. 
* `eval()` executes passed arguments if a JavaScript expression. If an adversary can manipulate input values, he or she can run any script.

## Python

The most common Python vulnerabilities ([CVE's with keyword Python](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=JavaScript):

* Some of the most common attacks are [SQL injection attacks](../../../trees/application-hacking/SQL-injection.md), [XSS attacks](../../../trees/web-hacking/Cross-Site-Scripting-(XSS).md) and [Cross-site request forgery (CSRF)](../../../trees/web-hacking/Cross-Site-Request-Forgery-(CSRF).md) injection attacks. These types of attacks can impact not just the language but the environment as a whole.
* [DoS](../../../trees/network-attacks/Denial-of-Service-(DoS).md) and [DDoS](../../../trees/network-attacks/Distributed-Denial-of-Service-(DDoS).md) styled attacks based on XML parsing attack vectors (using an XML standard library module, especially external XML files).
* `mltemp()` when used for creating temp files as a different process may also create a file with this name to attempt to load the wrong data or expose other temporary data.
