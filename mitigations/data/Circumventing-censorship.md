# Circumventing censorship

Increasingly, states have adopted wide-scale internet blocking as a technical resource for extending their practice of information control into the online world. The answer has been the development of circumvention tools for

  * Seeking, reading and disseminating unauthorised content
  * Creating unauthorised content
  * Distributing unauthorised content
  * Leaking confidential or otherwise privileged information

Internet malware can be developed and installed by governments to attack, monitor, or disrupt dissident computer systems and communication. Malware specifically targeted at a regional, racial, or language group is very difficult to intercept and identify by any anti-malware products available today and I wouldn't put it past regimes to try to create a range of fake circumvention tools under established names. 

One might also expect government authorities to profile users of circumvention tools. When circumventing censorship, it is important to do this while anonymised and protected. The resources and continuous effort required to constantly evade blocking activities while remaining anonymous is not to be underestimated, and requires careful planning and implementation.

## Which tools to use?

Just a getting started ... As with anonymising traffic, it depends on where you are, what the state adversary makes available in terms of resources and what the consequences of discovery in your country may be. 

|Method                      |Description                    |DPI |Cost for censor |Circumvention |
| --- | :-- | :-- | :-- | :-- |
|IP blocking                  |A certain IP address is denied|No  |Low  |[Find proxies that have access](https://snowflake.torproject.org/)|
|DNS filtering and redirection|DNS doesn't resolve domain names or returns incorrect IP addresses|No |Low|Find a domain name server that resolves domain names correctly or [bypass DNS](https://skipdns.link/) if the IP address is obtainable from other sources and is not blocked. ([modify hosts file](traffic/Edit-hosts-file.md)) or type the IP address instead of the domain name)|
|URL filtering                |Permits or denies access to specific websites based on information contained in an URL list|Yes|Medium|[Use escaped characters in the URL](https://www.w3schools.com/tags/ref_urlencode.asp), or use encrypted protocols such as [VPN](traffic/VPN.md) and [Tor](traffic/Tor.md)|
|Packet filtering             |TCP packet transmissions are terminated when a certain number of controversial keywords are detected|Yes|Low|Use encryption, such as [VPN](traffic/VPN.md) and [Tor](traffic/Tor.md)|
|Man-in-the-middle attack     |A root certificate is replaced with a self-signed certificate in the state by its agencies| |Low|Websites implementing HSTS|
|TCP connection reset         |If a previous TCP connection is blocked by the filter, future connection attempts from both sides will also be blocked for up to 30 minutes. Depending on the location of the block, other users or Web sites may be also blocked if the communications are routed to the location of the block. This was used by the [Great Firewall of China in 2007](http://pages.cs.wisc.edu/~rist/642-spring-2014/chinafirewall.pdf). I seriously doubt is still in use. |Yes |Medium |Ignore the reset packet sent by the firewall|
|VPN and Tor blocking                 |A firewall is able to "learn, discover and block" the encrypted communications methods used by a number of different VPN systems, and connection is terminated|Yes|High|Add a form of data obfuscation (steganographic coding); [Tor: Pluggable Transports](https://www.torproject.org/docs/pluggable-transports.html.en)




