# Redirection

URL redirection (URL forwarding) makes an object available under more than one address. When a web browser opens a URL that has been redirected, another object with a different address is opened. Domain redirection or domain forwarding is when all pages in a URL domain are redirected to a another domain.

* Going through a series of redirects, for example via the 302 Found response code, before landing on the final page is one of many techniques used to provide a platform for a MaaS (Malware-as-a-Service) infrastructure, as it shields the final landing page from automated security crawlers.
* When a user clicks on the poisoned search results, the request can be redirected to another site by way of:
    * The PHP header() function, to send a redirect status code back to the user's web browser.
    * JavaScript or other active content.
    * CSS (Cascading Style Sheet): In CSS, the URL property can be used to set the background. Without parameter to the URL property, like url() instead of url(some url), it will load the parent page again. During the second loading the referer HTTP header is set to the parent URL itself and the other content will be served.

## False positives

There are also many legitimate ways in which redirection is used.

* 301 Redirect, or permanent redirect, is not considered malicious behaviour.
* Post/Redirect/Get to prevent duplicate form submissions.
* URL shortening
* Logging outgoing links (privacy issue!)

## Known mitigations

These mitigations are neither under the control nor the responsibility of search engines.

* Informing searchers that they are redirected only if they click on a search link to an object. If the URL for the site is typed in, there is no redirection to the other site.
* URL filtering will not be effective because of the use of legitimate web sites to redirect visitors.
* Configuring servers and applications to prevent cross-scripting.

These are.

* Monitoring and securing servers to prevent these from becoming conduits for these attacks.
* Content inspection and filtering and payload detection to prevent malicious content from reaching the user.

