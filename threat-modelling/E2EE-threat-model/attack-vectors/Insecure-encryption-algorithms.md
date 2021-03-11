# Insecure encryption algorithms

A product is not automagically secure if it uses publicly known and reviewed “AES-256”, “RSA-4096” or “military-grade encryption” algorithms. The implementation of algorithms is also very important.

Some known (and common) vulnerabilities in messaging applications:

* Key and Initialisation Vector for the symmetric-key encryption are derived from a group-shared key and public information from the sender.
* No key confirmation in the client-to-client key exchange phase.
* In the message encryption phase, the integrity of the elements of associated data in a packet (sender key ID and recipient key ID) is not guaranteed.
* Some intermediate value is computable without any secret information.
* Using the same key in distinctively different contexts (modes).


