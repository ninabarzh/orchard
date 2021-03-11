# Chosen ciphertext attack

In a [chosen-ciphertext attack](../../../trees/crypto-attacks/Chosen-ciphertext-attack.md) (CCA), an adversary can analyse chosen ciphertexts together with their corresponding plaintexts to acquire a secret key or to get as much information about the system as possible. In this attack, the adversary is assumed to have a way to trick someone who knows the secret key into decrypting arbitrary message blocks and send back the result. The attacker can choose some arbitrary nonsense as an “encrypted message” and ask to see the (usually) different nonsense it decrypts to, and can do this a number of times. The goal of the adversary is deducing what the secret key is.

