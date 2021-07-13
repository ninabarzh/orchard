# PKI

Public key infrastructure (PKI) is the umbrella term for everything needed in order to issue, distribute, store, use, verify, revoke, and otherwise manage and interact with certificates and keys. It’s an intentionally vague term, like “database infrastructure”. Certificates are the building blocks of most PKIs, and certificate authorities are the foundation. 

## Failing

[PKI is vulnerable](https://nvd.nist.gov/vuln/search/results?form_type=Basic&results_type=overview&query=PKI+&search_type=all) by trying to be all things to all people and things. PKIs have experienced a hype and many companies and organizations announced to provide certification services to the general public. Only a few of these have succeeded and actually provide certification services that can be taken seriously.

### X.509 standard

X.509 is a complex standard and X.509 certificates are complex data structures with a lot of fields, many of which are critical and/or non-critical extension fields. Complex technology is not easy to deploy on a large-scale. Since Peter Gutmann from Auckland University published the X.509 Style Guide in 2000, little has improved.

* X.509 certificates are specified with ASN.1 and the resulting data structures are not very meaningful for humans (and hard to parse).
* The X.509 specification is scattered across many standards, drafts and amendments from multiple standard bodies, leading to confusion and numerous profiles that lack interoperability.
* Parts of the standard, even some that are related to key elements, are underspecified. That leads to ambiguity, unknown semantics and interoperability issues, like the country code, date/time formats in validity or path validation.

### Technical

* Because the PKI system is asymmetric, users need access to a public key and recipients of a message need a private key to decrypt the information. 
* Public key pairs must be generated in an efficient and secure (centralized or decentralized) way, and require a cryptographically strong pseudo-random bit generator, something which is not always available to end-users.
* Private keys must be securely stored in a personal security environment (and not a vulnerable endpoint), and for Web PKI public CA's certificates must be made publicly available in a certificate repository or directory service. Hierarchical trust models are dangerous, because they provide a single point of attack. Alternative models (for example the mesh model) are poorly scalable in time and in space.
* Certificate authorities (CA's) have to periodically send out a list of certificates that have been revoked (CRL's), meaning that a user will not only have to get the corresponding certificates from the certification chain, but will also have to check that those certificates are not in the CRL.
* The definition and maintenance of a global name space is not as simple in practice.
* Cross-certification does not work in practice because competition is rule.
* Many simple PKIs don’t even use certificates. When editing ~/.ssh/authorized_keys you’re configuring a simple certificate-less form of PKI that SSH uses to bind public keys to names in flat files.

### Economical

* The establishment and operation of a top CA requires large investments. One needs protection from adversaries trying to break into the facility, intercepting electromagnetic signals, and exploitation of other weaknesses of the used hardware and software, and one needs qualified personnel able to withstand all of the regulation and bureaucratic stuff.
* The ROI of a top CA is difficult to determine and quantify. Like many other infrastructure components, public key certificates do not provide a specific function in and of themselves, but provides only the means to secure functions and applications of other infrastructures. IOW, business cases for PKI's are extremely hard to make. That part got solved, with some scary stuff happening, web PKI next in the chain, and hosting companies (re)selling certificates.

### Juridical

* If a digital signature is generated according to some digital signature law, then somebody must be made liable if something goes wrong. If that is the Credential service provider (CSP), the insurance protection must be taken into account in a business case.
* As Bruce Schneier pointed out in Secrets and Lies, CA's usually limit their liability to the protection of their private key. As the CA plays the role of a trusted third party users of certificates are put at a disadvantage. CA's are like a notary who would only be liable to keep his stamp secure. Nothing changed much there either.
* The owner of a public key certificate cannot repudiate a signature that is generated with the appropriate signing key, which may lead to the situation in which a certificate owner may be held liable and accountable for statements that are digitally signed with the proper key, even if he or she does not know (and does not agree) with the statements.

### Social

* Web PKI is mostly defined by RFC 5280 and refined by the CA/Browser Forum. It's hierarchical, based on trusting authorities, and for some such authorities a big cash cow.
* In the real world, trust is based on two-way relationships and experiences that have been made over time. This can only insufficiently be modelled with hierarchical certificate models.
* Poor usability is a common feature of many products that employ (public key) cryptography. Secure cryptographic solutions and usability seem mutually exclusive. But then, there is not much focus on end users and UX design in general. 
* Lost keys are also an issue for individuals that rely on encrypted data. Lost keys restrict access to messages, and these messages are unavailable forever unless the cryptographic algorithm is weak and can be cracked.
* The users of public key cryptography are often not aware of the vulnerabilities and pitfalls.
* Web PKI being a money-spinner, we also have an alternative. Let’s Encrypt is a free, automated, and open Certificate Authority. And it has vulnerabilities.

### Privacy and security

* X.509 uses features from other standards, like DNs from X.500 which are in itself complex and have little value and provides unanticipated attack vectors.
* SSL in the context of web browsers used to be target of several successful attacks, either directly on SSL (e.g. SSL renegotiation bug), the combination of https and http ([SSL Strip](../../../trees/application-hacking/SSL-stripping.md), URL-forgery, and X.509-based attacks on ASN.1 and DN-parsing.
* Integration of PKI with the surrounding environment ([end points](../endpoints), [web applications](../endpoints/Applications.md)) may allow compromise.
* Should a private key be compromised, an attacker would have access to data intended for the recipient. Attackers that gain access to private keys can also eavesdrop on content intended for a recipient and decrypt data as it’s collected. This is the biggest threat to the PKI system, because compromised keys require new keys to be issued, and old ones revoked.
* There is no easy, fast and effective method to revoke a root certificate. Anything less that a full compromise of the root key will tempt a CA to downplay the incident and revoke only certain certificates. This occurred with the DigiNotar-Hack, because the revocation of the root-CA would have interrupted the operation of many services.
* Revocation services are suspect to DoS-attacks.
* CAs are included in browsers by OS- and browser vendors without a common consistent policy. To be included in the trust store the vendor has to pay a fee. Only Microsoft requires a formal audit. As a result there is a sufficient number of weak and very weak CAs that are included in default certificate stores. In addition there is suspicion in the security community that governments use compelled certificates to tap Internet communication.
* Clients certificates and their attributes have zero security value, because there are CAs that do not validate the attributes including attributes with arbitrary OIDs (P. Gutmann).
* Some certificate stores contain funny root certificates that should be excluded on any serious security review.
* SSL and PKI infrastructures are components in client device security and are used to bootstrap into higher-level security services such as software updates and digital signature services. Their vulnerabilities put other security services at risk.
* Pluggable Authentication Modules (PAM) is a suite of shared libraries, providing an abstraction layer between the various methods available that provide authentication and the applications that require authentication and would otherwise have to support those methods directly. With PAM, all that is necessary for these components to cooperate is that a specific PAM module be available for each of them. The pam_listfile.so module authenticates users based on the contents of a specified file. For example, if username exists in a file /etc/ssh/ssh.allow, ssh will grant login access. 
* An Internal PKI consists of a master-your-own master Certificate Authority (CA) certificate and key which is used to sign each of the server and client certificates and a separate certificate (public key) and private key for the server and each client. The most secure way of doing this is have the Certificate Authority keys generated on a stand-alone (not Internet-connected) machine in a secure location.

### IoT

Enter the Internet of Things (IoT), the Internet of Everything (IoE) and the Industrial Internet: all the devices that want confidentiality, integrity and authentication related to their identity and that of others too: implanted medical devices, robots on the plant floor, smart light bulbs, …
We have a veritable explosion of checks and balances, not to mention issuances, revocations and expirations … problems, old ones not solved and new ones.



