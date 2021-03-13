# NMap CheatSheet

* [Basic scanning techniques](#Basic-scanning-techniques)
* [Discovery options](#Discovery-options)
* [Advanced scanning functions](#Advanced-scanning-functions)
* [Port scanning options](#Port-scanning-options)
* [Version detection](#Version-detection)
* [Timing options](#Timing-options)
* [Firewall evasion techniques](#Firewall-evasion-techniques)
* [Output options](#Output-options)
* [Troubleshooting and debugging](#Troubleshooting-and-debugging)
* [Nmap scripting engine](#Nmap-scripting-engine)
* [Ndiff](#Ndiff)

### Basic scanning techniques
Scan a Single Target

    nmap [target]

Scan Multiple Targets

    nmap [target1, target2, etc]

Scan a List of Targets

    nmap -iL [list.txt]

Scan a Range of Hosts

    nmap [range of ip addresses]

Scan an Entire Subnet

    nmap [ip address/cdir]

Scan Random Hosts

    nmap -iR [number]

Excluding Targets from a Scan

    nmap [targets] --exclude [targets]

Excluding Targets Using a List

    nmap [targets] --excludefile [list.txt]

Perform an Aggressive Scan

    nmap -A [target]

Scan an IPv6 Target

    nmap -6 [target]

...

### Discovery options

Perform a Ping Only Scan

    nmap -sP [target]

Don’t Ping

    nmap -PN [target]

TCP SYN Ping

    nmap -PS [target]

TCP ACK Ping

    nmap -PA [target]

UDP Ping

    nmap -PU [target]

SCTP INIT Ping

    nmap -PY [target]

ICMP Echo Ping

    nmap -PE [target]

ICMP Timestamp Ping

    nmap -PP [target]

ICMP Address Mask Ping

    nmap -PM [target]

IP Protocol Ping
    nmap -PO [target]

ARP Ping

    nmap -PR [target]

Traceroute

    nmap --traceroute [target]

Force Reverse DNS Resolution

    nmap -R [target]

Disable Reverse DNS Resolution

    nmap -n [target]

Alternative DNS Lookup

    nmap --system-dns [target]

Manually Specify DNS Server(s)

    nmap --dns-servers [servers] [target]

Create a Host List

    nmap -sL [targets]

# Advanced scanning functions

TCP SYN Scan

    nmap -sS [target]

TCP Connect Scan

    nmap -sT [target]

UDP Scan

    nmap -sU [target]

TCP NULL Scan

    nmap -sN [target]

TCP FIN Scan

    nmap -sF [target]

Xmas Scan

    nmap -sX [target]

TCP ACK Scan

    nmap -sA [target]

Custom TCP Scan

    nmap --scanflags [flags] [target]

IP Protocol Scan

    nmap -sO [target]

Send Raw Ethernet Packets

    nmap --send-eth [target]

Send IP Packets

    nmap --send-ip [target]

### Port scanning options

Perform a Fast Scan

    nmap -F [target]

Scan Specific Ports

nmap -p [port(s)] [target]

Scan Ports by Name

    nmap -p [port name(s)] [target]

Scan Ports by Protocol

    nmap -sU -sT -p U:[ports],T:[ports] [target]

Scan All Ports

    nmap -p "*" [target]

Scan Top Ports

    nmap --top-ports [number] [target]

Perform a Sequential Port Scan

    nmap -r [target]

### Version detection

Operating System Detection

    nmap -O [target]

Submit  TCP/IP Fingerprints

    www.nmap.org/submit/

Attempt to Guess an Unknown OS

    nmap -O --osscan-guess [target]

Service Version Detection

    nmap -sV  [target]

Troubleshooting Version Scans

    nmap -sV --version-trace [target]

Perform a RPC Scan

    nmap -sR [target]

### Timing options

Timing Templates

    nmap -T[0-5] [target]

Set the Packet TTL

    nmap --ttl [time] [target]

Minimum # of Parallel Operations

    nmap --min-parallelism [number] [target]

Maximum #  of Parallel Operations

    nmap --max-parallelism [number] [target]

Minimum Host Group Size

    nmap --min-hostgroup [number] [targets]

Maximum Host Group Size

    nmap --max-hostgroup [number] [targets]

Maximum RTT Timeout

    nmap --initial-rtt-timeout [time] [target]

Initial RTT Timeout

    nmap --max-rtt-timeout [TTL] [target]

Maximum Retries

    nmap --max-retries [number] [target]

Host Timeout

    nmap --host-timeout [time] [target]

Minimum Scan Delay

    nmap --scan-delay [time] [target]

Maximum Scan Delay
    nmap --max-scan-delay [time] [target]

Minimum Packet Rate

    nmap --min-rate [number] [target]

Maximum Packet Rate

    nmap --max-rate [number] [target]

Defeat Reset Rate Limits

    nmap --defeat-rst-ratelimit [target]

### Firewall evasion techniques

Fragment Packets

    nmap -f [target]

Specify a Specific MTU

    nmap --mtu [MTU] [target]

Use a Decoy

    nmap -D RND:[number] [target]

Idle Zombie Scan

    nmap -sI [zombie] [target]

Manually Specify a Source Port

    nmap --source-port [port] [target]

Append Random Data

    nmap --data-length [size] [target]

Randomize Target Scan Order

    nmap --randomize-hosts [target]

Spoof MAC Address

    nmap --spoof-mac [MAC|0|vendor] [target]

Send Bad Checksums

    nmap --badsum [target]

### Output options

Save Output to a Text File

    nmap -oN [scan.txt] [target]

Save Output to a XML File

    nmap -oX [scan.xml] [target]

Grepable Output

    nmap -oG [scan.txt] [targets]

Output All Supported File Types

    nmap -oA [path/filename] [target]

Periodically Display Statistics

    nmap --stats-every [time] [target]

133t Output

    nmap -oS [scan.txt] [target]

### Troubleshooting and debugging

Getting Help

    nmap -h

Display Nmap Version

    nmap -V

Verbose Output

    nmap -v [target]

Debugging

    nmap -d [target]

Display Port State Reason

    nmap --reason [target]

Only Display Open Ports

    nmap --open [target]

Trace Packets

    nmap --packet-trace [target]

Display Host Networking

    nmap --iflist

Specify a Network  Interface

    nmap -e [interface] [target]

### Nmap scripting engine

Execute Individual Scripts

    nmap --script [script.nse] [target]

Execute Multiple Scripts

    nmap --script [expression] [target]

Script Categories

    all, auth, default, discovery, external, intrusive, malware, safe, vuln

Execute Scripts by Category

    nmap --script [category] [target]

Execute Multiple Script Categories

    nmap --script [category1,category2,etc]

Troubleshoot Scripts

    nmap --script [script] --script-trace [target]

Update the Script Database

    nmap --script-updatedb

### Ndiff

Comparison Using Ndiff

    ndiff [scan1.xml] [scan2.xml]

Ndiff Verbose Mode

    ndiff -v [scan1.xml] [scan2.xml]

XML Output Mode

    ndiff --xml [scan1.xml] [scan2.xml]
