# MitM server-to-server HTTPS communication

## ARP spoofing

* Use static, read-only entries for critical services in the ARP cache of a host (prevents only simple attacks and does not scale).
* Switches do cross-checking of ARP responses (combined with certification).
* OS of devices ignore unsolicited replies. The different OS's respond differently:
    * Linux ignores, but accepts responses to requests from other machines to update its cache.
    * Windows ARP cache can be configured through registry entries.
* Packet filtering: a spoofed packet can contain packets from outside the network that shows source addresses from inside the network and vice-versa.
* Authentication and encryption
* The above mitigations can only prevent simple ARP attacks. Use anti-ARP tools to identify and stop the more sophisticated adversary.

## DNS cache poisoning

* Use Passive DNS databases for near-real-time detection of fraudulent delegation changes and cache poisoning. The databases can be queried frequently to know more about the addresses being mapped by the major domain names at the time. All the information will come directly from the passive Data sensors and in the case of any deviations from the regular mappings of data gathered from an authoritative source, it could mean a breach of web security. Passive DNS data is rich, and can also be used to help administrators block the resolution of suspicious new domain names, identify potential infringements and as source for threat intelligence.

## BGP hijacking

* Some proposed mitigations mention measuring the Time to Live (TTL) field of incoming IP packets and filtering on that, but TTL is also easy to forge by a MitM. Measuring Round-Trip Time (RTT) would not be so easy to forge.
* A hijacked route is relatively easy to detect and mitigate. RPKI and BGPsec address this issue (to some extent). Global hijacking is rare, local hijacking possible under certain conditions, but also opens the possibility to hijack a prefix in such way that the hijack will not be seen by large ISPs, and RTT for most customers will not change either.
* A route leak is much harder to understand and prevent without a complex network monitoring solution.
* Using data aggregation from global route collection (DNS analytics) to filter prefix announcements coming from peers before passing them on to others (prefix de-aggregation, invalid originations, invalid AS (Autonomous System) adjacencies, and perhaps even improbable AS paths) may work, but none of that makes sense if ISP's do not even secure their networks properly.
* In general, large ISPs often implement some measures to prevent hijacking and leaking, but probably for the same reasons small ISPs often leave their network equipment and even the border routers unpatched and vulnerable, small ISPs seem not to care about prefix filtering.

## Certificate validation

* There are proposals for being able to “pin” domains to a specific certificate authority (for a fee of course), in which a certificate authority is to do extra diligence before considering issuing a certificate for a “pinned” domains.
* A new “pinning” header is being implemented by servers and browsers to protect against fraudulent certificates, but are not widely used yet.
* Some certificate authorities use multiple clients around the world to do their domain control validation. That will not stop a local BGP hijacking of a target domain, but does stop hijacking of the certificate authority validation test traffic itself.
* The Extended Validation (EV) process for certificates requires additional validation, including based on contact details provided in a qualified information source. An adversary would have to compromise that third-party source in addition to doing the BGP hijacking.
* The Certificate Transparency (CT) project is working on a global repository of domains, certificates, and associated certificate authorities. CT encourages domain owners to register with a monitoring service that will notify them if another certificate is ever issued. At the moment, only EV certificates are required to be registered with CT Logs.
