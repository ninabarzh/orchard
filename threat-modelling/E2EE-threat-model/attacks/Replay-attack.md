# Replay attack

A [replay attack](../../../trees/network-attacks/Replay-attack.md) (alias playback attack) is a form of network attack in which a valid data transmission is maliciously or fraudulently repeated or delayed. This is carried out either by the originator of the transmission or by an adversary who intercepts the data and re-transmits it, possibly as part of a masquerade attack by IP packet substitution. This is one of the lower tier versions of a Man-in-the-middle attack.

Suppose Alice wants to prove her identity to Bob. Bob requests her password as proof of identity, which Alice dutifully provides (possibly after some transformation like a hash function); meanwhile, Eve is eavesdropping on the conversation and keeps the password (or the hash). After the interchange is over, Eve (impersonating Alice) connects to Bob; when asked for a proof of identity, Eve sends Alice's password (or hash) read from the last session which Bob accepts, thus granting Eve access. 
