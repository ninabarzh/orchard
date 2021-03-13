# Port scanning

The most common type of scan in the discovery phase is a `SYN` scan (or SYN stealth scan), named for the `TCP SYN` flag used in the `TCP` connection sequence. To perform the default SYN (`-sS`)scans, privileges are required. If privileges are insufficient a TCP connect (`-sT`) scan is used. 

## Attack tree

    1 Port scanning (AND)
        1.1 Do a TCP scan (OR)
                1.1.2 Use the default SYN (`-sS`)scans (privileges are required) (OR)
                1.1.3 Use the connect (`-sT`) scan (privileges are not required)
        1.2 Do a UDP scan
    2 Check for potential known problems with found ports

## Resources

There are many different ports scanners that all operate in pretty much the same way. 

* [Nmap cheatsheet](../../resources/cheatsheets/Nmap-cheatsheet.md)
* [Nessus](../../resources/cheatsheets/Nessus-cheatsheet.md)
* [Metasploit cheatsheet](../../resources/cheatsheets/Metasploit-cheatsheet.pdf)
* [Unicornscan cheatsheet](../../resources/cheatsheets/Unicornscan-cheatsheet.md)
* [IKE-scan cheatsheet](../../IKE-scan-cheatsheet.md)

