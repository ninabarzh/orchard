# Identity providers

Increasingly, Identity providers are used instead of explicitly authenticating a user. An Identity Provider is responsible for authenticating users and issuing identification information by using security tokens like SAML 2.0, OpenID Connect, OAuth 2.0 and WS-Trust.

* When a user attempts to log in to a website, service or cloud app, they are redirected to a trusted identity provider that has been preconfigured to accept authentication requests from that service or cloud application.
* The IdP collects the user’s credentials, for example, their username and one-time passcode (OTP) and returns an accept or reject, according to which a user is granted or denied access to the application.

## First session setup

Users authenticate with an Identity Provider :

* The user needs to ensure it sent the authentication credentials to the right Identity Provider. Malware, weak authentication credentials, phishing, weak transport-layer security, etc. are known problems.
* The Identity Provider must authenticate the user. Security vulnerabilities can potentially compromise this step.

The Identity Provider provides a signed identity token to users:

* The token contains an assertion about the user identity. If the signature scheme is weak, or the keys are compromised, it could allow an attacker to forge the token and bypass the authentication step.
* The scope of a token is the service that requested it. If the Identity Provider mistakenly provides a token for the Key Server to a third party, then such a third party can impersonate the user to the Key Server.
* The token must be securely transmitted back to the user, failure to do so could allow a third party to impersonate the user.

