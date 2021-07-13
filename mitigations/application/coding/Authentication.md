# Authentication

Authentication provides a way to collect credentials and determine the identity of a user. During authentication with a web application for example, //Web Agents// communicate with a //Policy Server// to determine the proper credentials that must be retrieved from the user who is requesting resources, potentially introducing a larger attack surface. IOW, the strength of the access control model to guard against unauthorised access depends on the robustness of the authentication scheme being used. 

Carefully implement an authentication mechanism to control which users are allowed to access which data. The keyword here is the "carefully", so as to introduce as little new holes in the Emmental cheese as possible.

* Use [SSL](protocols/TLS-SSL-PKI.md)
* Always do the authentication process in a https session. 
* Encrypt credentials in rest (when stored on the server) using hashing, MD5, etc.
* When the server sets a cookie on a browser, the `Http-Only` attribute can inform the browser not to allow access to the cookie from the DOM. This prevents client-side script-based attacks from accessing the sensitive data stored in the cookies.
* Use persistent and transient authentication methods (or a hidden field provided on every form) to aid protection against CSRF
  * Tokenise client-server communication with an additional token not stored in cookies. Each form can have a separate token when the session is established and be sent with each request during the session.
  * Implement session tokens and postfix the token in all requests raised by the user (Cross-site request forgery (CSRF))
  * Do not store sensitive information such as tokens in browser storage.
  * Make the token pseudo-random enough to make it computationally expensive for an attacker to guess. 
  * For highly sensitive operations, add a user interaction based protection (re-authentication or a one-time token) along with token based mitigation.
  * Terminate idle sessions (Cross-site request forgery (CSRF))
* Sandbox applications so that adversaries will need to use two exploits: one for the vulnerable browser or add-on/extension and another to break out of the sandbox.
