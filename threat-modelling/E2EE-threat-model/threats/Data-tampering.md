# Data tampering

Data tampering is deliberately modifying (destroying, manipulating or editing) data through unauthorized channels.

* An adversary can intercept data packets, decrypt and modify its contents and change its destination address using a variety of attack vectors.
* A E2EE adversary can impersonate a sender.
* A malicious group member can collude with an E2EE adversary or a malicious group member is the E2EE adversary, and can mount a forgery or impersonation attack.
* The OpenPGP message format allows for limited tampering with the encrypted messages if Symmetrically Encrypted Data Packets (Tag 9) lacking integrity protection are used.

## Mitigation

### PGP

* In accordance to RFC 4880, PGP uses Symmetrically Encrypted Integrity Protected Data Packets (Tag 18 packets) when composing messages and verifies the MDC code when processing messages with Tag 18 packets. PGP still also accepts the Tag 9 packet for compatibility.
* Sign created PGP messages with the user's private key by default (provide the user with an option to choose the signing key or to disable the signature for an individual message)

### Group messaging

* In the group message of the Signal protocol, each group member sends Sender key to all group members via pair-wise secure E2EE. Sender key contains an encryption key of symmetric-key encryption schemes and a verification key of the digital signature of the sender. When a member sends a message to a group, the message is encrypted using an ephemeral key that is derived from the encryption key, and the ciphertext signed by sender’s signature key. The receiver is able to check whether the message is from the sender by verifying the signature by the sender’s verification key in Sender key. Because a malicious group member does not know the target sender’s signature key, he/she is not able to make a signature for the ciphertext.
* Apple's iMessage implements group messaging using pairwise channels: a message is sent to all group members via one-to-one encryption channels. This blocks group message forgery but might be less efficient.

### One-on-one messaging

* The unknown key share attack for impersonation and forgery does not work in Signal because the computation of a shared secret in the key exchange phase involves One-Time Pre Key. This changes the shared secret at every execution of the key exchange even if the public keys are the same.

