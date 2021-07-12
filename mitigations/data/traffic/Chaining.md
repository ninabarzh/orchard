# Chaining 

Suppose you visit a website with a torified Browser. Tor processes the traffic. Your adversary uses a vulnerability to remotely execute code. An adversary who can talk to the control port, can use Tor's getinfo address, setconf a proxy or alternate directory authorities or bridges, listen to events (including log events) that give away details that can be correlated. 

Not only an end to end correlation attack, many more vulnerabilities exist. Any successful attack against Tor on a Tor based anonymity operating system will naturally deanonymise the user. Some of the attacks can be protected from by chaining. [Whonix uses this approach](https://www.whonix.org/wiki/Chaining_Anonymizing_Gateways). With some notes ...

For deciding whether to use chaining or not, and if so, whether to use [TorPlusVPN (torproject)](https://gitlab.torproject.org/legacy/trac/-/wikis/doc/TorPlusVPN) for [combining tunnels with Tor](https://www.whonix.org/wiki/Tunnels/Introduction), summarising: It all depends on where you live, what you do, what your resources are, and what skills you have. 

## You -> VPN/SSH -> Tor
[Routing Tor through VPN/SSH services](https://www.whonix.org/wiki/Tunnels/Connecting_to_a_VPN_before_Tor) might prevent your ISP etc from seeing that you're using Tor (VPN/SSH Fingerprinting). Using VPN's may or may not make you stand out as much, as in some countries replacing an encrypted Tor connection with an encrypted VPN or SSH connection (which is what it will look like), will be suspicious as well. SSH tunnels may make you stand out even more. 

It also prevents Tor from seeing who you are behind the VPN/SSH. If an adversary breaks Tor and learns the IP address your traffic is coming from, and your VPN/SSH really does not watch, does not remember, and makes magically sure nobody else is watching either, you'll be safer.

## You -> Tor -> VPN/SSH
[Routing VPN/SSH services through Tor](https://www.whonix.org/wiki/Tunnels/Connecting_to_Tor_before_a_VPN) hides and secures your Internet activity from Tor exit nodes (a major vulnerability because some governments create exit nodes to do just that). You are still exposed to VPN/SSH exit nodes and will want to pay for the VPN anonymously (cash in the mail [mind your fingerprint and printer fingerprint], Liberty Reserve, well-laundered Bitcoin, etc). 

This is impossible to do without using virtual machines and is not easy to set up. It also creates a bottleneck where all your traffic goes, making correlations easy and the VPN/SSH can over time build a profile of everything you do, and over time de-anonymise your traffic.

![Chaining](../../assets/images/chaining.png)