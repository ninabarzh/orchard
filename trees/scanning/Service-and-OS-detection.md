# Service and OS detection

Service and OS detection use different methods to determine the operating system or service running on a particular port.

## Attack tree

    1 Detect OS and services (AND)
    2 Detect services (AND)
    3 Grab banner

## Resources

* [Nmap cheatsheet][../../resources/cheatsheets/Nmap-cheatsheet.md]
* [Nessus](../../resources/cheatsheets/Nessus-cheatsheet.md)
* [Metasploit cheatsheet](../../resources/cheatsheets/Metasploit-cheatsheet.pdf)
* [Unicornscan cheatsheet](../../resources/cheatsheets/Unicornscan-cheatsheet.md)
* [IKE-scan cheatsheet](../../IKE-scan-cheatsheet.md)

## Examples

    # nmap -sn -T4 -oG Discovery.gnmap 192.168.1.1/24
    # grep “Status: Up” Discovery.gnmap | cut -f 2 -d ‘ ‘ > LiveHosts.txt



