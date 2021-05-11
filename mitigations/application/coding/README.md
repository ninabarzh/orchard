# Coding

* Disable verbose error messages for messages that are displayed to users without special privileges.
* Use context-sensitive server side output encoding, a combination of escaping, filtering, and validating string data when handling user input and output from the server (cross-site scripting (XSS))
  * Replace special characters with escape codes for those characters. 
  * Remove dangerous characters from the data received as input. This is not enough. There are some techniques adversaries can use to evade such filters.
  * Validate browser-supplied input for it to only contain expected characters. Use whitelisting of acceptable characters and reject everything else.
* Use client ***and*** server-side validation. Python validation can be used for making sure only expected data makes it into the application, and to inform users immediately of issues with their input. 
* When the server sets a cookie on the browser, the `Http-Only` attribute can inform the browser not to allow access to the cookie from the DOM. This prevents client-side script-based attacks from accessing the sensitive data stored in the cookies.
* Best protection is not to store sensitive information such as tokens in browser storage at all.
* Tokenise client-server communication with an additional token not stored in cookies. Each form can have a separate token when the session is established and be sent with each request during the session. 
* Establish and maintain control over all [inputs](Input.md)
* Establish and maintain control over all [outputs](Output.md)
* Mitigate the most common language specific vulnerabilities
  * [JavaScript](Javascript.md)
  * [Python](Python.md)