# Browsers

Many of the [browser vulnerabilities](../../resources/vulnerabilities/endpoints/Browser.md) exploited by the attacks and abuses mentioned need to be fixed by the developers of browsers and web applications, which aren’t much under the direct control of users, but users are not entirely powerless.

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



