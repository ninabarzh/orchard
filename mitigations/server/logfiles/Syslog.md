# Syslog

The rsyslogd service is a system utility providing support for message logging. Support of both internet and unix domain sockets enables this utility to be used for remote and local logging. [Rsyslog](https://www.rsyslog.com/) is a multi-threaded implementation of syslogd.

* A combined audit system for linux
* Allows for local and remote log collection. Remote logging makes day-to-day maintenance and incident response easier, log storage more secure, auditing more effective and analysis easier across multiple platforms.
* Allows for a single point of management 
* Controlled per device in ''/etc/syslog.conf''
* All reported messages are collected in a message file
* Log replication can copy the audit data to multiple remote-logging hosts

## Setting it up

* Set up a separate server for only logging purposes.
* Keep it in a secure location behind a (physical) firewall.
* Have no unnecessary services running on it.
* Delete all other user accounts.
* Add two snort boxes (IDS) that are actually syslog servers (yet have no IP address) and copy each packet intended for syslog server. With two boxes doing that independently from one another, court cases can be very convincingly supported. **Thank you, Dean Bushmiller, that is a very, very good idea**.
  * Promiscuous mode
  * Rule: Only listen for this IP address on this port (of syslog server)

## Configuration resources 

* [Configuring remote syslog from Unix/Linux and BSD/macOS](https://help.papertrailapp.com/kb/configuration/configuring-remote-syslog-from-unixlinux-and-bsdos-x/)
* [Configuring remote syslog from Windows](https://help.papertrailapp.com/kb/configuration/configuring-remote-syslog-from-windows/)

