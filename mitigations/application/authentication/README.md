# Authentication

* Use [SSL](protocols/TLS-SSL-PKI).md)
* Encrypt credentials when stored on the server, using hashing, MD5, etc.
* Enforce strict cookie control, to thwart impersonating tokens.
* Implement session tokens and postfix the token in all requests raised by the user (Cross-site request forgery (CSRF))
* Terminate idle sessions (Cross-site request forgery (CSRF))
