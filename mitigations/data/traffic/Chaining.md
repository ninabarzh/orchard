# Chaining 

Suppose you visit a website with a torified Browser. Tor processes the traffic. Your adversary uses a vulnerability to remotely execute code. An adversary who can talk to the control port, can use Tor's getinfo address, setconf a proxy or alternate directory authorities or bridges, listen to events (including log events) that give away details that can be correlated. 

Not only an end to end correlation attack, many more vulnerabilities exist. Any successful attack against Tor on a Tor based anonymity operating system will naturally deanonymise the user. Some of the attacks can be protected from by chaining. [Whonix uses this approach](https://www.whonix.org/wiki/Chaining_Anonymizing_Gateways).

![Chaining](https://github.com/tymyrddin/orchard/blob/main/mitigations/assets/images/chaining.png)

