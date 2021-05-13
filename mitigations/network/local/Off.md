# Off (Home)

## Turn router off when not in use 
Consider disabling it during travel or extended periods when you will not need to be online. Depending on manufacturer of the WLAN router, it may be impractical to turn the Wi-Fi signal off and on frequently. Some routers have a button for quickly turning off Wi-Fi and some even offer the option to configure a wireless schedule that will automatically disable the Wi-Fi at specified times.
    
# Disable services when not needed

Make services like Telnet, Universal Plug and Play (UPnP), Secure Shell (SSH), and Home Network Administration Protocol (HNAP) unreachable from the internet. Turn them off on the local network if they're not needed. 

Universal Plug and Play (UPnP) is a handy feature that allows networked devices to seamlessly discover and establish communication with each other on the network. The UPnP feature eases initial network configuration and is also a security risk. Malware within a network can use UPnP to bypass a router’s firewall and allow attackers to take control of devices remotely to spread malware to other devices. 

* Get your router's IP address

    $ host myip.opendns.com resolver1.opendns.com

* [Scan your router's public IP address](../../../resources/cheatsheets/Nmap-cheatsheet.md) for open ports.

 
