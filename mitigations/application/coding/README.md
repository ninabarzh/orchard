# Coding

* Disable verbose error messages for messages that are displayed to users without special privileges.
* Use context-sensitive server side output encoding, a combination of escaping, filtering, and validating string data when handling user input and output from the server (cross-site scripting (XSS))
  * Replace special characters with escape codes for those characters. 
  * Remove dangerous characters from the data received as input. This is not enough. There are some techniques adversaries can use to evade such filters.
  * Validate browser-supplied input for it to only contain expected characters. Use whitelisting of acceptable characters and reject everything else.
* Use client ***and*** server-side validation. Python validation can be used for making sure only expected data makes it into the application, and to inform users immediately of issues with their input.  
* Establish and maintain control over all [inputs](Input.md)
* Establish and maintain control over all [outputs](Output.md)
* Mitigate the language specific most common vulnerabilities
  * [JavaScript](Javascript.md)
  * [Python](Python.md)