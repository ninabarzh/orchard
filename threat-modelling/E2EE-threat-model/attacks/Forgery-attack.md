# Forgery attack

A [forgery attack](../../../trees/crypto-attacks/Forgery-attack.md) can be mounted by an [E2EE adversary](../adversaries/E2EE-adversary.md), able to bypass the client-to-server transport encryption.

A forgery attack can (but not necessarily) lead to an [impersonation attack](Impersonation-attack.md). An impersonation attack is when an adversary can successfully claim an identity that she doesn't possess, and pass authentication (i.e. she can pretend to be another person in the system). 

Many authentication protocols rely on verifying some cryptographic data, if the cryptographic data can be forged, then authentication will admit the wrong person. Often, the authentication protocols rely on PKI, and require the party to be authenticated to provide a valid certificate, and the validation of the certificate relies on the CA's signature on the certificate. If one can forge the CA's signature, she can forge a certificate, thus be authenticated as another person.

If a malicious group member colludes with an E2EE adversary or the malicious group member is the E2EE adversary, this forgery attack works and because the E2EE adversary sends an unmodified packet D to the targeted group member, he or she does not notice the attack. If a scenario like this is possible, the group message encryption does not provide for integrity of the messages - data tampering is possible.
