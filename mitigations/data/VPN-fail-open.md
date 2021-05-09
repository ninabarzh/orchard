# Fail open

If you simply add a VPN using common instructions, it generally //fails open//. That means, if the VPN breaks down, because the connection is interrupted, traffic will be sent without the VPN. It is much safer when it //fails closed//, meaning that when the VPN connection breaks down, the whole internet connection must be down as long as the VPN connection is not restored.

## Use a firewall 

As an example, `ufw` can be set up as a fail safe mechanism (aka kill switch). 

Set all traffic to deny:

    $ sudo ufw default deny outgoing
    $ sudo ufw default deny incoming

Permit OpenVPN traffic (if using OpenVPN adapter is probably tun0 but check.)

    $ sudo ufw allow out on tun0 from any to any

For added security you may want to keep incoming traffic disabled but if desired or required then allow it:

    $ sudo ufw allow in on tun0 from any to any

With this rule all non VPN traffic (and subsequently DNS requests not routed though VPN) will be blocked.

But, this set up requires that you disable the firewall to connect to the VPN and then enable it once connection is made. To allow establishment of a connection to the VPN server even when the firewall is enabled:

    $ sudo ufw allow out from any to [VPN server IP address]

Add multiple rules for all VPN servers you will be using. If you want more strict rules and better security then only allow desired ports on tun0.

## VPNfirewall script 

The [VPNfirewall script by Adrelanos](https://github.com/adrelanos/VPN-Firewall)

  * Forbids outgoing traffic after the VPN software broke down for some reason.
  * Has tight firewall rules, using iptables policy drop.
  * Only tested with OpenVPN. Should work with other VPN clients such as PPTP in theory, you should test if it does what it claims anyway.
  * Only tested on Debian Wheezy and Whonix. Should work on any other Linux distribution in theory, you should test if it does what it claims.
  * Is Open Source / Free Software 
