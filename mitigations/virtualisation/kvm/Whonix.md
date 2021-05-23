# Whonix gateway and workstation

A security research workstation.

## Installation

Installation went mostly without a glitch with the [Whonix ™ for KVM](https://www.whonix.org/wiki/KVM) guide. During first boot of both I got a:

    Error starting domain: Requested operation is not valid: blkio device weight is valid only for bfq or cfq scheduler

Which were quickly solved by removing

    <blkiotune>
        <weight>250</weight>
    </blkiotune>

from their configuration files:

    $ sudo virsh edit Whonix-Gateway

and 

    $ sudo virsh edit Whonix-Workstation
    
## Chaining

Next up is deciding whether to use ([chaining](../data/../../data/traffic/Chaining.md)) or not, and if so, use [TorPlusVPN (torproject)](https://gitlab.torproject.org/legacy/trac/-/wikis/doc/TorPlusVPN) for [combining tunnels with Tor](https://www.whonix.org/wiki/Tunnels/Introduction). Summarising:

### You -> VPN/SSH -> Tor
[Routing Tor through VPN/SSH services](https://www.whonix.org/wiki/Tunnels/Connecting_to_a_VPN_before_Tor) might prevent your ISP etc from seeing that you're using Tor (VPN/SSH Fingerprinting). Using VPN's may or may not make you stand out as much, as in some countries replacing an encrypted Tor connection with an encrypted VPN or SSH connection (which is what it will look like), will be suspicious as well. SSH tunnels may make you stand out even more. 

It also prevents Tor from seeing who you are behind the VPN/SSH. If an adversary breaks Tor and learns the IP address your traffic is coming from, and your VPN/SSH really does not watch, does not remember, and makes magically sure nobody else is watching either, you'll be safer.

### You -> Tor -> VPN/SSH
[Routing VPN/SSH services through Tor](https://www.whonix.org/wiki/Tunnels/Connecting_to_Tor_before_a_VPN) hides and secures your Internet activity from Tor exit nodes (a major vulnerability because some governments create exit nodes to do just that). You are still exposed to VPN/SSH exit nodes. You will want to pay for the VPN anonymously (cash in the mail [beware of your fingerprint and printer fingerprint], Liberty Reserve, well-laundered Bitcoin, etc). This is impossible to do without using virtual machines. And you'll need to use TCP mode for the VPNs (to route through Tor). Not easy to set up.
Even if you manage to pay anonymously, you're making a bottleneck where all your traffic goes, making correlations easy and the VPN/SSH can over time build a profile of everything you do, and over time de-anonymise your traffic.

In my circumstances and for my purpose of security research, I will stick to using Whonix Gateway to use Tor without leaks.
