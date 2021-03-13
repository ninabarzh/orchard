# Dig cheatsheet

dig is a network administration command-line tool for querying the Domain Name System. dig is useful for network troubleshooting and for educational purposes. It can operate based on command line option and flag arguments, or in batch mode by reading requests from an operating system file.

﻿Basic dig

    # dig [domain]

Just get the ip address

    # dig [domain] +nocomments +noauthority +noadditional +nostats 
OR

    # dig [domain] +noall +answer

OR
    # dig [domain] +short

For a specific query type

    # dig -t [query type] [domain] [options]

OR

    # dig [domain] [query type] [options]

Viewing ALL DNS record types use query ANY

    # dig -t ANY [domain] [options]

OR

    # dig [domain] ANY [options]

DNS reverse look up 

    # dig -x [ip address] +short

Specific DNS server

    # dig @[specific DNS] [domain]

Bulk DNS query (file.txt contains all the domains, one per line)

    # dig [domain1] [options] [domain2] [options]

OR

    # dig -f file.txt [options]

Any DNS server connected to the Internet is likely to have a copy of the InterNIC’s <code>named.root</code> file that lists the root name servers for the entire Internet. These can be downloaded from the InterNIC’s ftp server (ftp://ftp.internic.net/domain/named.root). Or...

    # dig +nocmd . NS +noall +answer +additional

Tracing:

    # dig [domain] +trace

Grabbing SOA information (provides a clear accounting of said public servers)

    # dig [domain] +nssearch





