# Linux server

Minimally ...

* Stay updated with subscriptions to security notification services.
* Update the OS regularly (within hours of critical updates).
* Update the control panel regularly (if any).
* Reduce information disclosure.
* Don’t install software that is not used. Remove software that is not used.
* Use private networks for internal server traffic.
* Use encryption when appropriate.
* Harden default service settings in webserver, SSH and other services.
* Disable direct root login in SSH.
* Get rid of passwords with SSH keys.
* Make sure logs are working properly.
* Make sure you log all information needed to track a common intruder.
* Consider intrusion detection.
* Enable SELinux if possible.

Note: In these notes commands preceded with `#` do not mean to do it as root, it means root privileges are required (`su -` or `sudo`). When `$` is used that most likely does not mean just any user. Often, services and applications have their own user.

* [SSH](ssh)
  * [Installing SSH](ssh/Installing-SSH.md)
  * [Harden ssh server](ssh/Harden-ssh-server.md)
  * [Key management](ssh/Key-management.md)
  * [Jumping hosts](ssh/Jumping-hosts.md)
  * [ForwardAgent](ssh/ForwardAgent.md)
  * [ProxyCommand](ssh/ProxyCommand.md)
  * [ProxyJump](ssh/ProxyJump.md)
  * [Authentication error](ssh/Authentication-error.md)
  * [Keeping current](ssh/Keeping-current.md)
* [Firewall](firewall) 
  * [IPTables](firewall/IPTables.md)
  * [NFTables](firewall/NFTables.md)
  * [FirewallD](firewall/FirewallD.md)
  * [FireHOL](firewall/FireHOL.md)
  * [UFW](firewall/UFW.md)
  * [Packet filtering with I/O Control](firewall/PF.md)
  * [Fail2ban](firewall/Fail2ban.md)
  * [SSHguard](firewall/SSHguard.md)
  * [WAF](firewall/WAF.md)
  * [Blacklists](firewall/Blacklists.md)
  * [Port spoofing](firewall/Port-spoofing.md)

## Problems or Suggestions

[Open an issue here](https://github.com/tymyrddin/orchard/issues)

## Contributing

This project welcomes contributions and suggestions. 
