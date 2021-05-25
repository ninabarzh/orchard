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

Next up is deciding whether to use ([chaining](../data/../../data/traffic/Chaining.md)) or not, and if so, to use [TorPlusVPN (torproject)](https://gitlab.torproject.org/legacy/trac/-/wikis/doc/TorPlusVPN) for [combining tunnels with Tor](https://www.whonix.org/wiki/Tunnels/Introduction). 

In my circumstances and for my purpose of security research, using a Whonix Gateway to use Tor without leaks suffices.
