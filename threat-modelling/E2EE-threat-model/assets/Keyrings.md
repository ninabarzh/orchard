# Keyrings

* Secret keyring - Secret key(s), certifying user identities. Secret keys are used to decrypt incoming messages, and sign outgoing messages. Secret keys also include one or more user identities (often e-mail addresses), each signed by the key. Owning a secret key also implies a claim by its owner to the associated identities (but the validity of such a claim is decided by other users).
* Public keyring - List of public keys imported by the user. Keys in the public keyring are used to encrypt outgoing messages, and verify incoming message signatures. Often, the presence of a key in the user's public keyring implies a user trusts it, along with its associated identities. The public keyring contains the identities of the people with whom a user has exchanged messages, as well as from any imported public keys. The public keyring is analogous to the list of contacts of a user.

