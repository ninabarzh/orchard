# TLS/SSL PKI

  * Do not use SSL 3.0 on a server (this will be a problem if Internet Explorer 6.0 must still be supported). Use TLS 1.1 or TLS 1.2
  * Most current browsers/servers use ''TLS_FALLBACK_SCSV''. If a client requests a TLS protocol version that is lower than the highest supported by the server (and client), the server will treat it as an intentional downgrade and drop the connection.
  * Do not accept an incorrect padding structure after decryption.
  * Disable HTTP compression.
  * Separate secrets from user input.
  * Randomize secrets per request.
  * Mask secrets (randomize by XORing with a random secret per request).
  * Protect pages against injections.
  * Hide length (for example by adding random numbers of bytes to responses).
  * Limit the rate of requests.
  * Use the latest version of OpenSSL or recompile the already installed version with ''-DOPENSSL_NO_HEARTBEATS''.
  * The NULL cipher suites inform the browser not to encrypt data, therefore nullifying any protection given through the use of SSL/TLS. Do not have NULL.
  * Disable RC2 and SHA-1.
  * Consider disabling RC4 (Bar Mitzvah), DES and 3DES (Sweet32).

