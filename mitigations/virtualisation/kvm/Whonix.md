# Whonix

A security research workstation.

## Installation

Installation went mostly without a glitch with [Whonix ™ for KVM](https://www.whonix.org/wiki/KVM). During first boot of both I got a:

    Error starting domain: Requested operation is not valid: blkio device weight is valid only for bfq or cfq scheduler

Which were quickly solved by removing

    <blkiotune>
        <weight>250</weight>
    </blkiotune>

from their configuration files:

    $ sudo virsh edit Whonix-Gateway

and 

    $ sudo virsh edit Whonix-Workstation
    
## VPN

Next up is [Connecting to a VPN before Tor](https://www.whonix.org/wiki/Tunnels/Connecting_to_a_VPN_before_Tor) (chaining)
