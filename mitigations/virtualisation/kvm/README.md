# Ubuntu with KVM

The new Thinkpad X1 Carbon Gen 9 did not accept Debian yet, but did install Ubuntu.

* [Secure host](../pc)
* [Installation KVM](Installation.md)
* [Default VM for communication (debian)]
* [Development VM (debian)]
* [Whonix Gateway VM]
* [Pentesting VM (kali or blackarch)]
* [Digital forensics VM]
* [Server with docker VM (CentOS)](Server-with-docker.md)

## Notes

* Host security is critically important, because if a host is compromised, then all VMs running on it can be compromised. This is no different than for non-virtualised hosts. The usual tools can be used, including firewall and SELinux. Additional measures could be isolating VM network traffic from host traffic. 
* VM security involves not just securing the OS running on the VMs, but also securing the VM images from within the host. Because VM images are accessible from the host either on local or remote storage, VM images can additionally be secured using VM image encryption and the `svirt` service.
* For remote management SSH tunnels and SASL (Simple Authentication and Security Layer) can be used.
  * SSH Tunnels can remotely connect to the host and do not require configuration in advance. It requires SSH login credentials on the host for a user that can manage virtualisation resources, which by default only ‘root’ can do (can be changed to allow non-root accounts).
  * SASL gives secure authentication and data encryption. In its most simple implementation, a separate user credential database is created to authenticate with the `libvirtd` daemon (non-login user ids can be used to manage virtualised resources on a KVM host). 