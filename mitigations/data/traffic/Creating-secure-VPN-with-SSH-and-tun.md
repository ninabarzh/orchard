# Creating a secure VPN with SSH and tun

Not all programs have the ability to use a SOCKS proxy, while what is really needed is an all-encompassing proxy, one that just takes all outgoing and incoming traffic and sends it over that secure encrypted link. In effect, a secure [VPN](VPN.md).

In the situation described in [SSH explained](SSH.md) root access to a remote machine running an ssh server, a SSH client, install the tun kernel module locally and remotely.

    # modprobe tun    
    
To establish a new network interface on both sides of the connection, ''tun0'', locally run the command:

    # ssh -w 0:0 -f -C -q -N root@host.tld    

And:

    # ifconfig tun0 10.0.0.200 pointopoint 10.0.0.100    

SSH into the remote machine, and run these commands:

    # ifconfig tun0 10.0.0.100 pointopoint 10.0.0.200
    # ping -c 3 10.0.0.200    

If you get a ping response, it works. 

Routing your traffic through the remote machine, requires setting it up to enable packet forwarding and configuring iptables to act as a gateway (for which [William Budington](https://www.inputoutput.io) has written a script ([Download sharedconnection.sh script](https://www.inputoutput.io/shareconnection.sh)) that can serve as a starting point). 

Set up routing tables locally to direct all traffic (except the traffic that is still needed to keep the tun0 interface alive!) through the tun0 interface (in this case for a router with IP address ''192.168.0.1'', and default interface ''eth0''):

    # route add host.tld gw 192.168.0.1 eth0
    # route del default gw 192.168.0.1 eth0
    # route add default gw 10.0.0.100 tun0    

All outbound and incoming traffic is now routed through the remote machine. Get friends to use it as well, this reduces fingerprinting risks for all involved.

It is also possible to set up iptables to forward all traffic through a socks proxy without remote root and the tun module. IOW, more to follow ...
