# Ubuntu with KVM

The new Thinkpad X1 Carbon Gen 9 did not accept Qubes or Debian yet, but did install Ubuntu.

* [Secure host](../pc)
* [Installation KVM](Installation.md)
* [Default VM for communication (debian)](Default.md)
* [Development VM (debian)](Development.md)
* [Whonix Gateway VM](Whonix.md)
* [Pentesting VM (blackarch)](Pentesting-blackarch.md)
* [Pentesting VM (kali)](Pentesting-kali.md)
* [Digital forensics VM](Forensics.md)
* [Server with docker VM (CentOS)](Server-with-docker.md)
* [SSH](ssh.md)

## Notes

* Host security is critically important, because if a host is compromised, then all VMs running on it can be compromised. The security measures are not different than for non-virtualised hosts. The usual tools can be used, including firewall and SELinux. Additional measures could be isolating VM network traffic from host traffic. 
* VM security involves not just securing the OS running on the VMs, but also securing the VM images from within the host. Because VM images are accessible from the host either on local or remote storage, VM images can additionally be secured using [SSH](ssh.md), VM image encryption and the `svirt` service.
* For remote management SSH tunnels and SASL (Simple Authentication and Security Layer) can be used.
  * SSH Tunnels can remotely connect to the host and do not require configuration in advance. It requires SSH login credentials on the host for a user that can manage virtualisation resources, which by default only ‘root’ can do (can be changed to allow non-root accounts).
  * SASL gives secure authentication and data encryption. In its most simple implementation, a separate user credential database is created to authenticate with the `libvirtd` daemon (non-login user ids can be used to manage virtualised resources on a KVM host). 
* Make backups of each .vmdk image just after install, and set up incremental backups. Backup images manually after major changes.