# Man-in-the-Middle (MitM)

A Man-in-the-Middle (MitM) attack is a general term for when an adversary positions herself in the middle of a conversation (usually between a user and an application on the application or cryptograhic layer). A MitM attack allow an adversary to proxy communication between two parties allowing any data to either be read or altered. For example to eavesdrop or to steal personal information such as login credentials, account details, tokens and credit card numbers. This information can then further be used for unapproved fund transfers, password changes, impersonation, complete identity theft and for gaining a foothold during the infiltration stage of a structured hack.

In a classical attack:
   * The adversary first subverts the address infrastructure (intercepts traffic). In passive interception forms, an adversary makes, for example, an infected WiFi hotspot available to the public. Active forms use some sort of spoofing. 
  * After subverting the address infrastructure, any two-way SSL traffic needs to be decrypted. This can be done by, for example, SSL spoofing (does not attack SSL itself, but the transition from non-encrypted to encrypted communications), spoofing HTTPS, an SSL BEAST attack, or hijacking SSL
* Session replay and hijacking attacks can be used to bypass authentication.
* If a root certificate can be installed on the target, the adversary can replace it and maintain a secure connection.
* When used for BGP session hijacking, DNS spoofing is likely not very useful because of hostnames not being used in router configurations.

## Attack

    1 Gain write access to network segment of one or more peers (AND)

    2 Subvert address infrastructure (AND)

        2.1 IP spoofing (OR)

        2.2 ARP/MAC spoofing (OR)

        2.2 DNS spoofing (OR)

    3 Decrypt (AND)

        3.1 Spoof HTTPS (OR)

        3.2 SSL BEAST (OR)

        3.3 Hijack SSL (OR)

        3.4 Strip SSL

    4 Proxy sessions 
