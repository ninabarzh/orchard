# E2EE Threat Modelling

After Snowden’s revelation, E2EE received a lot of attentions as a technology to protect user privacy from mass interception and surveillance of communications carried out by governmental organizations such as NSA and GCHQ. Supposedly, end-to-end encryption (E2EE) is a defence against MitM attacks.

Yet most E2EE systems are secure against only the weakest passive adversaries, breakable not by cryptanalysis of underlying cryptographic algorithms but by flawed system designs and security assumptions. Unencrypted metadata and access patterns make these systems susceptible to inference attacks. And recently made laws seem to have been made to prepare the way for agencies to legitimately gather encrypted data via backdoors and ghost protocols. 

    Adversaries
        E2EE adversary
        Service provider
        Malicious user
        Malicious group member
        Us
    Assets
        Cipher
        Messages/Emails
        Keyrings
        Cloud/Storage Systems
        Databases
        Identity providers
        Web applications
    Attack vectors
        Vulnerable endpoints
        Unencrypted metadata
        Unencrypted backups
        Insecure encryption algorithms
        Backdoors
        Automated verification
        Ghost protocols
    Attacks
        Chosen plaintext attack
        Impersonation attack
        Chosen ciphertext attack
        Forgery attack
        Replay attack
        Side-channel attack
    Threats
        Plaintext leaks
        Data tampering
        Changed message order and delivery
        Public keyring identities leakage