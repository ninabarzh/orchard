# Browser

[Continuously new attack techniques exploit browser flaws](../../../trees/web-hacking/Browser-based-attacks.md) and lead to the compromise of data.

* 0-day vulnerabilities may result in various levels of browser compromise.
* Some browser extensions have permissions to alter any web application and tamper with HTTP traffic (capability to act as a man-in-the-middle and web application threat source).
* Native applications installed alongside the browser can access assets directly (for example via the file system or a memory monitor). For example, an improperly configured backup solution may leak secret keys stored in a user's browser profile to a network adversary or cloud storage provider.
* Phishing for account credentials, or by breaking into an account (for example by exploiting account recovery flows or weak passwords) can give an adversary the ability to compromise the account by exploiting a vulnerability in one of the devices associated with that account but without the key material (for example malware installed on a smartphone), allowing the adversary to install arbitrary extensions into the browser profile.
* Browsers is where tracking starts. Many websites track IP addresses and related system information, including system names and Internet network addresses that often uniquely identify computers.
* Browsers can be used as gateways in XSS, CSRF, clickjacking, and Man-in-the-Browser attacks. Ongoing business. Content Security Policy (CSP) is a computer security standard introduced to prevent cross-site scripting (XSS), clickjacking and other code injection attacks resulting from execution of malicious content in a trusted web page context. Widely supported by modern web browsers. The December 2015 “XSS Jigsaw” and December 2016 “Collection of CSP bypasses” publications list a few methods of bypassing 'nonce' whitelisting origins. In January 2016, “An Abusive Relationship with AngularJS” was published, which leverages server-wide CSP whitelisting to exploit old and vulnerable versions of JavaScript libraries hosted at the same server. In May 2017, “Don't Trust The DOM: Bypassing XSS Mitigations Via Script Gadgets” appeared describing a method to bypass CSP using web application frameworks code.

## Mitigations

Many of the vulnerabilities exploited by the attacks and abuses mentioned need to be fixed by the developers of browsers and web applications, which aren’t much under the direct control of users, but users are not entirely powerless.

### Individuals

* View the metadata browsers are sending
* Check extensions/add-ons/plugins for known vulnerabilities
* Change default browser settings to exclude cookies, since they can be used to build up detailed profiles of surfing patterns over time.
* Use private browsing.
* Use safer browsing.
* Use networked or single-point anonymisers to obscure identifying information.
* Security awareness training
* Lock down the browser and the software it can invoke.
* Tighten associated application settings to disable unwanted features and to configure trust zones.

### Organisations

* Organisations best tighten application settings to disable unwanted features and configure trust zones centrally (using the Group Policy feature of Active Directory?)

### Developers

* Frame busting is a severely limited protection from clickjacking. For example, frame-busting JavaScript can be defeated by disabling JavaScript. Some clickjacking looks for CSRF vulnerabilities by looking for evidence of exclusively cookie based session ids, using a variety of heuristics to identify and verify whether various parameters are serving as session tokens. Combinations of lack of frame busting and/or CSRF issues can lead to opening up for clickjacking for pages requiring an authenticated session.
* Use persistent and transient authentication methods (or a hidden field provided on every form) to aid protection against CSRF
* Sandbox applications so that adversaries will need to use two exploits: one for the vulnerable browser or add-on/extension and another to break out of the sandbox.


