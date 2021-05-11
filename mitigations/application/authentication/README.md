# Authentication

* Use [SSL](protocols/TLS-SSL-PKI).md)
* Always do the authentication process in a https session. 
* Encrypt credentials in rest (when stored on the server) using hashing, MD5, etc.
* When the server sets a cookie on a browser, the `Http-Only` attribute can inform the browser not to allow access to the cookie from the DOM. This prevents client-side script-based attacks from accessing the sensitive data stored in the cookies.
* Best protection is not to store sensitive information such as tokens in browser storage at all.
* Tokenise client-server communication with an additional token not stored in cookies. Each form can have a separate token when the session is established and be sent with each request during the session.
* Implement session tokens and postfix the token in all requests raised by the user (Cross-site request forgery (CSRF))
* Make the token pseudo-random enough to make it computationally expensive for an attacker to guess. 
* For highly sensitive operations, add a user interaction based protection (re-authentication or a one-time token) along with token based mitigation.
* Terminate idle sessions (Cross-site request forgery (CSRF))
