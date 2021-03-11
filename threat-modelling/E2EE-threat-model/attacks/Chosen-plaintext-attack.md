# Chosen plaintext attack

In a [chosen-plaintext](../../../trees/crypto-attacks/Chosen-plaintext-attack.md) attack an adversary can (possibly adaptively) ask for the ciphertexts of arbitrary plaintext messages. This is formalized by allowing the adversary to interact with an encryption oracle, viewed as a black box. The goal is to reveal all or part of the secret encryption key.

It may seem infeasible in practice that an attacker could obtain ciphertexts for given plaintexts, but modern cryptography is implemented in software or hardware and is used in a diverse range of applications and very feasible. Chosen-plaintext attacks become extremely important in the context of public key cryptography, where the encryption key is public and so attackers can encrypt any plaintext they choose.

Chosen-plaintext attacks (CPAs) are often used to break symmetric encryption. To be considered CPA-secure, the symmetric cipher must not be vulnerable to chosen-plaintext attacks. Thus, it is important for symmetric cipher implementers to understand how an attacker would attempt to break their cipher (and make improvements based on that).

For some chosen-plaintext attacks, only a small part of the plaintext may need to be chosen by the attacker; such attacks are known as plaintext injection attacks.
