# Man-in-the-Middle attack

Search terms used to query web search engines contain significant amounts of sensitive information and the aggregation and use of these terms constitutes a severe privacy breach ([information exposure](../threats/Information-exposure.md)).

* The most impactful attack is based on the common flaw of simply not encrypting sensitive data, or when encrypting is employed, using weak key generation and management, weak algorithms, protocol and ciphers, especially for password hashing storage techniques. For data in transit, server side weaknesses are easy to detect, but hard for data at rest. Failure to encrypt (properly) can compromise all data which require protection as defined by laws or regulations such as the EU GDPR or local privacy laws.
* A usual suspect can monitor network traffic, for example at an insecure wireless network, downgrade connection from HTTPS to HTTP, intercept requests, and steal the user's session cookie. The attacker can then replay this cookie and can hijack a user's (authenticated) session, accessing or modifying the user's private data or alter all transported data. This means he or she can learn all of the queries without any threat of retribution.

See attack trees in [Network attacks](../../../trees/network-attacks) and [Application hacking](../../../trees/application-hacking)

## Known mitigations

A possible solution has been proposed by Yehuda Lindell and Erez Waisbard, in the form of a highly efficient cryptographic protocol for parties to mix their inputs that guarantees privacy in the presence of malicious adversaries. Unlike the usual setting of mixnets, in this solution the parties themselves carry out the mix. The novelty of the approach is based on the observation that, unlike the setting of voting where mixnets are usually applied, the guarantee of correctness is not necessary for private web search. That is, a malicious participant is allowed to carry out a “denial of service” type attack, causing the search to fail. In return, the expensive zero-knowledge proofs of correctness in every stage of the mix can be omitted, making it faster than the known mixnet solutions.
Data controller

* Classify data processed, stored or transmitted. Identify which data is sensitive according to privacy laws or regulatory requirements and apply controls as per the classification.
* Do not store sensitive data unnecessarily in the indexes or dictionaries. Discard it as soon as possible or use PCI DSS compliant tokenisation or even truncation. Data that is not retained cannot be stolen.
* Encrypt all sensitive data at rest.
* Use up-to-date and strong standard algorithms, protocols, and keys, and use proper key management.
* Encrypt all data in transit with secure protocols.
* Disable caching for responses that contain sensitive data.
* Store passwords using strong adaptive and salted hashing functions with a work factor (delay factor), such as Argon2, scrypt, bcrypt or PBKDF2.
* Audit the effectiveness of configuration and settings.


