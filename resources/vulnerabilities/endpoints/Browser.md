# Browser

[Continuously new attack techniques exploit browser flaws](../../../trees/web-hacking/Browser-based-attacks.md) and lead to the compromise of data.

* 0-day vulnerabilities may result in various levels of browser compromise.
* Some browser extensions have permissions to alter any web application and tamper with HTTP traffic (capability to act as a man-in-the-middle and web application threat source).
* Native applications installed alongside the browser can access assets directly (for example via the file system or a memory monitor). For example, an improperly configured backup solution may leak secret keys stored in a user's browser profile to a network adversary or cloud storage provider.
* Phishing for account credentials, or by breaking into an account (for example by exploiting account recovery flows or weak passwords) can give an adversary the ability to compromise the account by exploiting a vulnerability in one of the devices associated with that account but without the key material (for example malware installed on a smartphone), allowing the adversary to install arbitrary extensions into the browser profile.
* Browsers is where tracking starts. Many websites track IP addresses and related system information, including system names and Internet network addresses that often uniquely identify computers.
* Browsers can be used as gateways in [XSS](../../../trees/web-hacking/XSS.md), [CSRF](../../../trees/web-hacking/CSRF.md), [clickjacking](../../../trees/web-hacking/Clickjacking.md), and [Man-in-the-Browser](../../../trees/application-hacking/Man-in-the-Browser-(MitB)) attacks. Ongoing business. Content Security Policy (CSP) is a computer security standard introduced to prevent cross-site scripting (XSS), clickjacking and other code injection attacks resulting from execution of malicious content in a trusted web page context. Widely supported by modern web browsers. The December 2015 “XSS Jigsaw” and December 2016 “Collection of CSP bypasses” publications list a few methods of bypassing 'nonce' whitelisting origins. In January 2016, “An Abusive Relationship with AngularJS” was published, which leverages server-wide CSP whitelisting to exploit old and vulnerable versions of JavaScript libraries hosted at the same server. In May 2017, “Don't Trust The DOM: Bypassing XSS Mitigations Via Script Gadgets” appeared describing a method to bypass CSP using web application frameworks code.

Many of the browser vulnerabilities exploited by the attacks and abuses mentioned need to be fixed by the developers of browsers and by web application developers, neither of which is much under the direct control of users, but users are not entirely powerless. Some [mitigations](../../../mitigations/pc/malware/Browsers.md) and [ways to make browsing safer](../../../mitigations/data/browsing/README.md) are available. 



