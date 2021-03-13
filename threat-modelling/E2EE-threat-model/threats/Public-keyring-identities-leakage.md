# Public keyring identities leakage

Identities present in a public keyring hold the information of who an E2EE user has communicated with. Some information leaks are inevitable, as this information can be obtained from other sources. For example, if an E2EE messaging or email application does not remove the Key IDs from outgoing messages, they will be accessible to a relevant server, web application and MitM adversaries.
