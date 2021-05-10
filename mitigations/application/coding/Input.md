## Input

Use a standard input validation mechanism to validate input for length, type of input, syntax, missing or extra inputs, and consistency across related fields. Understand all the potential areas where untrusted inputs can enter the application: parameters or arguments, cookies, anything read from the network, environment variables, reverse DNS lookups, query results, request headers, URL components, e-mail, files, databases, and any external systems that provide data to the application. Inputs may be obtained indirectly through API calls.

  * Validate on the server side to protect against attacks. Server side validation is also important for compatibility.
  * Validate on the client side to give better feedback to users providing input.
  * Some validations can't be properly done in server-side application code, and are impossible in client-side code, because they depend on the current state of a database. Only the database can reliably validate data which depends on related data.

For mitigating the low hanging fruit, the OWASP has created a list of [Top 25 vulnerabilities](https://cwe.mitre.org/top25/archive/2020/2020_cwe_top25.html) that can be helpful. [MITRE](https://cwe.mitre.org) has more detailed descriptions and (coding) examples.
