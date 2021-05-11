# Javascript

* Avoid `eval()`. Instead, opt for alternative options that are more secure.
* Use HTTPS/SSL to encrypt data exchanged between the client and the server.
* Set cookies as “secure,” limiting the use of the application’s cookies to only secure web pages.
* Assign individual tokens for each end user. If the tokens do not match up, deny or revoke access (API access keys).
* Use safe methods of DOM manipulation. `innerHTML` does not limit or escape/encode values passed on to them. Use `innerText` instead. It provides escaping (preventing DOM-based XSS attacks).
