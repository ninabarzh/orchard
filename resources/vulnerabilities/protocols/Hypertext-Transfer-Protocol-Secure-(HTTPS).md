# Hypertext Transfer Protocol Secure (HTTPS)

Many sites now use HTTPS by default, and millions of TLS certificates are currently in use. With companies like Let's Encrypt offering free certificates and automated management tools, it is also easier than ever to deploy HTTPS. The purpose of a certificate is to allow a browser to verify that it is communicating with the correct site. Supposedly a man-in-the-middle attacker would not be able to hijack a browser's connection to the site unless he or she is able to obtain a valid certificate for that domain. And only a few HTTPS servers correctly implements HTTP Strict Transport Security, a widely-supported security feature that prevents visitors making unencrypted HTTP connections to a server.

* Some websites implement HTTPS but do not implement an HSTS policy (and HSTS Preloading) and can be attacked simply by hijacking an HTTP connection that is destined for it. This is an extremely feasible attack vector, as there are many ways in which a user can end up connecting via HTTP instead of HTTPS.
    * When not explicitly typing in the protocol string, some older browsers still default to HTTP.
    * Most secure websites also run an HTTP service to redirect users to the corresponding HTTPS site. A [SSLStrip attack](../../../trees/application-hacking/SSL-stripping.md) transparently hijacks HTTP traffic on a network and converts HTTPS links and redirects to HTTP.

## Mitigations

### Development

* SSLStrip doesn't depend on the server's behaviour, it depends on the client, even if the server only supports HTTPS. For SSLStrip to work, the attacker only needs to be a man in the middle. On an incoming HTTP request, the attacker would open an HTTPS connection to the real server, and “strip” the SSL off the HTTPS. HSTS prevents the browser from performing the plain HTTP request in the first place (on subsequent requests).

