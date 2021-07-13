# Snapping us some dark matter

Making attack trees from researching security issues to help us organise our thoughts. Another work in progress. [Work in progress]

Pentesting is not a linear process, more like a spontaneous choreography, a sequence of chosen movements as the dance unfolds. It is also highly [context and purpose dependent](https://github.com/tymyrddin/orchard/wiki/Purpose-of-pentesting).

Attack Trees (based on security research) represent often used movements and can help organise our thoughts around [which tools and scripts may be reuseful for which type of pentesting](https://github.com/tymyrddin/orchard/wiki/Types-of-pentesting) and/or various audits (and which mitigations we may need for our own development efforts).

## Attack trees

<img align="left" src="assets/images/warning.png">_Do not implement and execute these on a network or system you do not own. Execute only on your own systems for learning purposes. Do not execute these on any production network or system, unless "Rules of engagement" have been agreed on, and you have a "Get out of jail free" card of some sort._

The below categorisation is somewhat arbitrary, some trees have more detail, some lack such detail because we haven't tried them yet, and some are just mere paragraphs with intent to make the tree.

### Index

* [Reconnaissance](reconnaissance)
  * [Gather public information](reconnaissance/Gather-public-information.md)
  * [Web scraping](reconnaissance/Web-scraping.md)
  * [Traceroute analysis](reconnaissance/Traceroute-analysis.md)
  * [War-dialing-driving-flying-shipping](reconnaissance/War-dialing-driving-flying-shipping.md)
  * [Initial scanning](reconnaissance/Initial-scanning.md)
  * [Hide your tracks](reconnaissance/Hide-your-tracks.md)
* [Scanning](scanning)
  * [Ping sweep](scanning/Ping-sweep.md)
  * [Port scanning](scanning/Port-scanning.md)
  * [Service and OS detection](scanning/Service-and-OS-detection.md)
  * [Stealth](scanning/Stealth.md)
* [Enumeration](enumeration)
  * [Windows enumeration](enumeration/Windows-enumeration.md)
  * [Linux enumeration](enumeration/Linux-enumeration.md)
  * [Network enumeration](enumeration/Network-enumeration.md)
* [System hacking](system-hacking)
  * [Gain unauthorised access](system-hacking/Gain-unauthorised-access.md)
  * [Access password database](system-hacking/Access-password-database.md)
  * [Unauthorised privilege escalation on a web server](system-hacking/Unauthorised-privilege-escalation-on-web-server.md)
  * [Unauthorised privilege escalation on hosts](system-hacking/Unauthorised-privilege-escalation-on-hosts.md)
* [Malware](malware)
  * [RouterSploit](malware/Router-sploit.md)
* [Network attacks](network-attacks)
  * [Sniffing](network-attacks/Sniffing.md)
  * [Compromise router](network-attacks/Compromise-router.md)
  * [ARP spoofing](network-attacks/ARP-spoofing.md)
  * [Port redirection](network-attacks/Port-redirection.md)
  * [Replay attack](network-attacks/Replay-attack.md)
  * [IP spoofing](network-attacks/IP-spoofing.md)
  * [Hijack session (network)](network-attacks/Hijack-session-(network).md)
  * [Man-in-the-Middle (MitM)](network-attacks/Man-in-the-Middle-(MitM).md)
  * [Attack domestic WiFi](network-attacks/Attack-domestic-WiFi.md)
  * [TCP sequence prediction attack](network-attacks/TCP-sequence-prediction-attack.md)
  * [Hijack BGP](network-attacks/Hijack-BGP.md)
  * [Denial of Service (DoS)](network-attacks/DoS.md)
  * [Distributed Denial of Service (DDoS)](network-attacks/DDoS.md)
  * [Distributed Deflection Denial of Service (DrDoS)](network-attacks/DrDoS.md)
* [Application hacking](application-hacking)
  * [Hijack session (application)](application-hacking/Hijack-session-(application).md)
  * [SSL stripping](application-hacking/SSL-stripping.md)
  * [SSL hijacking](application-hacking/SSL-hijacking.md)
  * [SSL BEAST](application-hacking/SSL-BEAST.md)
  * [HTTPS spoofing](application-hacking/HTTPS-spoofing.md)
  * [DNS attacks](application-hacking/DNS-attacks.md)
  * [DNS spoofing](application-hacking/DNS-spoofing.md)
  * [Man-in-the-Browser (MitB)](application-hacking/Man-in-the-Browser-(MitB).md)
  * [SEO poisoning](application-hacking/SEO-poisoning.md)
  * [Virtual host confusion attack](application-hacking/Virtual-host-confusion-attack.md)
* [Web hacking](web-hacking)
  * [Cross-Site Scripting (XSS)](web-hacking/Cross-Site-Scripting-(XSS).md)
  * [Cross-Site Request Forgery (CSRF)](web-hacking/Cross-Site-Request-Forgery-(CSRF).md)
  * [Clickjacking](web-hacking/Clickjacking.md)
  * [Browser-based attacks](web-hacking/Browser-based-attacks.md)
* [Crypto attacks](crypto-attacks)
  * [Brute-force](crypto-attacks/Brute-force.md)
  * [Read a PGP encrypted message](crypto-attacks/Read-a-PGP-encrypted-message.md)
  * [Chosen plaintext attack](crypto-attacks/Chosen-plaintext-attack.md)
  * [Chosen ciphertext attack](crypto-attacks/Chosen-ciphertext-attack.md)
  * [Side-channel attack](crypto-attacks/Side-channel-attack.md)
  * [Impersonation attack (Group message)](crypto-attacks/Impersonation-attack-(Group-message).md)
  * [Unknown key share attack](crypto-attacks/Unknown-key-share-attack.md)
* [Social engineering](social-engineering)
  * [Create a botnet](social-engineering/Create-a-botnet.md)
  * [Credential stuffing](social-engineering/Credential-stuffing.md)
  * [Pharming](social-engineering/Pharming.md)
  * [Phishing](social-engineering/Phishing.md)

## Problems or Suggestions

This project welcomes contributions and suggestions. 

[Open an issue here](https://github.com/tymyrddin/orchard/issues)

