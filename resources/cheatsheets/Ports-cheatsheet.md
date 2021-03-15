# Port scanning cheatsheet

The [Ports Database](https://www.speedguide.net/ports.php) is a comprehensive, searchable database of official and unofficial tcp/udp port assignments, known vulnerabilities, trojans, applications use and more.

* System Ports (0-1023)
* User Ports (1024-49151)
* Dynamic / Private Ports (49152-65535)

|TCP/UDP Ports &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  |Service Description  |Notes  |
| :------------- | :---------- | :---------- |
|0 | | Reserved port |
|[7](https://www.speedguide.net/port.php?port=7)	|Echo||
|[19](https://www.speedguide.net/port.php?port=19)	|Chargen||
|[20](https://www.speedguide.net/port.php?port=20) - [21](https://www.speedguide.net/port.php?port=21)	|FTP|Most common|
|[22](https://www.speedguide.net/port.php?port=22)	|SSH/SCP|Most common|
|[23](https://www.speedguide.net/port.php?port=23)	|Telnet||
|[25](https://www.speedguide.net/port.php?port=25)	|SMTP||
|[42](https://www.speedguide.net/port.php?port=42)	|WINS Replication||
|[43](https://www.speedguide.net/port.php?port=43)	|WHOIS||
|[49](https://www.speedguide.net/port.php?port=49)	|TACACS||
|[53](https://www.speedguide.net/port.php?port=53)	|DNS||
|[67](https://www.speedguide.net/port.php?port=67) - [68](https://www.speedguide.net/port.php?port=68)	|DHCP/BOOTP||
|[69](https://www.speedguide.net/port.php?port=69)	|TFTP||
|[70](https://www.speedguide.net/port.php?port=70)	|Gopher||
|[79](https://www.speedguide.net/port.php?port=79)	|Finger||
|[80](https://www.speedguide.net/port.php?port=80)	|HTTP| Most common|
|[88](https://www.speedguide.net/port.php?port=88)	|Kerberos||
|[102](https://www.speedguide.net/port.php?port=102)	|MS||
|[110](https://www.speedguide.net/port.php?port=110)	|POP3|Most common|
|[113](https://www.speedguide.net/port.php?port=113)	|Ident||
|[119](https://www.speedguide.net/port.php?port=119)	|NNTP (Usenet)||
|[123](https://www.speedguide.net/port.php?port=123)	|NTP||
|[135](https://www.speedguide.net/port.php?port=135)	|Microsoft RPC||
|[137](https://www.speedguide.net/port.php?port=137) - [139](https://www.speedguide.net/port.php?port=139)	|NetBIOS||
|[143](https://www.speedguide.net/port.php?port=143)	|IMAP4|Most common|
|[161](https://www.speedguide.net/port.php?port=161) - [162](https://www.speedguide.net/port.php?port=162)	|SNMP||
|[177](https://www.speedguide.net/port.php?port=177)	|XDMCP||
|[179](https://www.speedguide.net/port.php?port=179)	|BGP||
|[201](https://www.speedguide.net/port.php?port=201)	|AppleTalk||
|[264](https://www.speedguide.net/port.php?port=264)	|BGMP||
|[318](https://www.speedguide.net/port.php?port=318)	|TSP||
|[381](https://www.speedguide.net/port.php?port=381) - [383](https://www.speedguide.net/port.php?port=383)	|HP Openview||
|[389](https://www.speedguide.net/port.php?port=389)	|LDAP||
|[411](https://www.speedguide.net/port.php?port=411) - [412](https://www.speedguide.net/port.php?port=412)	|Direct Connect||
|[443](https://www.speedguide.net/port.php?port=443)	|HTTP over SSL|The standard port for all secured HTTP traffic.|
|[445](https://www.speedguide.net/port.php?port=445)	|Microsoft DS|Used for direct TCP/IP MS Networking access without the need for a NetBIOS layer (windows machines). Block to prevent internal spreading of ransomware. If file and printer sharing are required, leave open on some internal firewalls.      |
|[464](https://www.speedguide.net/port.php?port=464)	|Kerberos||
|[465](https://www.speedguide.net/port.php?port=465)	|SMTP over SSL||
|[497](https://www.speedguide.net/port.php?port=497)	|Retrospect||
|[500](https://www.speedguide.net/port.php?port=500)	|ISAKMP||
|[512](https://www.speedguide.net/port.php?port=512)	|rexec||
|[513](https://www.speedguide.net/port.php?port=513)	|rlogin||
|[514](https://www.speedguide.net/port.php?port=514)	|syslog||
|[515](https://www.speedguide.net/port.php?port=515)	|LPD/LPR||
|[520](https://www.speedguide.net/port.php?port=520)	|RIP||
|[521](https://www.speedguide.net/port.php?port=521)	|RIPng (IPv6)||
|[540](https://www.speedguide.net/port.php?port=540)	|UUCP||
|[554](https://www.speedguide.net/port.php?port=554)	|RTSP||
|[546](https://www.speedguide.net/port.php?port=546) - [547](https://www.speedguide.net/port.php?port=547)	|DHCPv6||
|[560](https://www.speedguide.net/port.php?port=560)	|rmonitor||
|[563](https://www.speedguide.net/port.php?port=563)	|NNTP OVER SSL||
|[587](https://www.speedguide.net/port.php?port=587)	|SMTP||
|[591](https://www.speedguide.net/port.php?port=591)	|FileMaker||
|[593](https://www.speedguide.net/port.php?port=593)	|Microsoft DCOM||
|[631](https://www.speedguide.net/port.php?port=631)	|Internet Printing||
|[636](https://www.speedguide.net/port.php?port=636)	|LDAP OVER SSL||
|[639](https://www.speedguide.net/port.php?port=639)	|MSDP (PIM)||
|[646](https://www.speedguide.net/port.php?port=646)	|LDP (MPLS)||
|[691](https://www.speedguide.net/port.php?port=691)	|MS Exchange||
|[860](https://www.speedguide.net/port.php?port=860)	|iSCSI||
|[873](https://www.speedguide.net/port.php?port=873)	|rsync||
|[902](https://www.speedguide.net/port.php?port=902)	|VMware Server||
|[989](https://www.speedguide.net/port.php?port=989) - [990](https://www.speedguide.net/port.php?port=513)	|FTP OVER SSL||
|[993](https://www.speedguide.net/port.php?port=993)	|IMAP4 OVER SSL|Most common|
|[995](https://www.speedguide.net/port.php?port=995)	|POP3 OVER SSL|Most common|
|[1025](https://www.speedguide.net/port.php?port=1025)	|Microsoft RPC||
|[1026](https://www.speedguide.net/port.php?port=1026) - [1029](https://www.speedguide.net/port.php?port=1029)	|Windows Messenger||
|[1080](https://www.speedguide.net/port.php?port=1080)	|SOCKS PROXY and MyDoom||
|[1194](https://www.speedguide.net/port.php?port=1194)	|OpenVPN||
|[1214](https://www.speedguide.net/port.php?port=1214)	|KAZAA||
|[1241](https://www.speedguide.net/port.php?port=1241)	|Nessus||
|[1311](https://www.speedguide.net/port.php?port=1311)	|Dell OpenManage||
|[1337](https://www.speedguide.net/port.php?port=1337)	|WASTE||
|[1433](https://www.speedguide.net/port.php?port=1433) - [1434](https://www.speedguide.net/port.php?port=1434)	|Microsoft SQL||
|[1512](https://www.speedguide.net/port.php?port=1512)	|WINS||
|[1589](https://www.speedguide.net/port.php?port=1589)	|Cisco VQP||
|[1701](https://www.speedguide.net/port.php?port=1701)	|L2TP||
|[1723](https://www.speedguide.net/port.php?port=1723)	|MS PPTP||
|[1725](https://www.speedguide.net/port.php?port=1725)	|STEAM||
|[1741](https://www.speedguide.net/port.php?port=1741)	|CiscoWorks 2000||
|[1755](https://www.speedguide.net/port.php?port=1755)	|MS MEDIA SERVER||
|[1812](https://www.speedguide.net/port.php?port=1812) - [1813](https://www.speedguide.net/port.php?port=513)	|RADIUS||
|[1863](https://www.speedguide.net/port.php?port=1863)	|MSN||
|[1985](https://www.speedguide.net/port.php?port=1985)	|Cisco HSRP||
|[2000](https://www.speedguide.net/port.php?port=2000)	|Cisco SCCP||
|[2002](https://www.speedguide.net/port.php?port=2002)	|Cisco ACS||
|[2049](https://www.speedguide.net/port.php?port=2049)	|NFS||
|[2082](https://www.speedguide.net/port.php?port=2082) - [2083](https://www.speedguide.net/port.php?port=513)	|cPanel||
|[2100](https://www.speedguide.net/port.php?port=2100)	|Oracle XDB||
|[2222](https://www.speedguide.net/port.php?port=2222)	|DirectAdmin||
|[2302](https://www.speedguide.net/port.php?port=2302)	|HALO||
|[2483](https://www.speedguide.net/port.php?port=2483) - [2484](https://www.speedguide.net/port.php?port=2484)	|Oracle DB||
|[2745](https://www.speedguide.net/port.php?port=2745)	|Bagle.H||
|[2967](https://www.speedguide.net/port.php?port=2967)	|Symantec AV||
|[3050](https://www.speedguide.net/port.php?port=3050)	|Interbase DB||
|[3074](https://www.speedguide.net/port.php?port=3074)	|XBOX Live|
|[3124](https://www.speedguide.net/port.php?port=3124)	|HTTP Proxy||
|[3127](https://www.speedguide.net/port.php?port=3127)	|MyDoom||
|[3128](https://www.speedguide.net/port.php?port=3128)	|HTTP Proxy||
|[3222](https://www.speedguide.net/port.php?port=3222)	|GLBP||
|[3260](https://www.speedguide.net/port.php?port=3260)	|iSCSI Target||
|[3306](https://www.speedguide.net/port.php?port=3306)	|MySQL||
|[3389](https://www.speedguide.net/port.php?port=3389)	|Terminal Server||
|[3689](https://www.speedguide.net/port.php?port=3689)	|iTunes||
|[3690](https://www.speedguide.net/port.php?port=3690)	|Subversion||
|[3724](https://www.speedguide.net/port.php?port=3724)	|World of Warcraft||
|[3784](https://www.speedguide.net/port.php?port=3784) - [3785](https://www.speedguide.net/port.php?port=3785)	|Ventrilo||
|[4333](https://www.speedguide.net/port.php?port=4333)	|mSQL||
|[4444](https://www.speedguide.net/port.php?port=4444)	|Blaster||
|[4664](https://www.speedguide.net/port.php?port=4664)	|Google Desktop||
|[4672](https://www.speedguide.net/port.php?port=4672)	|eMule||
|[4899](https://www.speedguide.net/port.php?port=4899)	|Radmin||
|[5000](https://www.speedguide.net/port.php?port=5000)	|UPnP||
|[5001](https://www.speedguide.net/port.php?port=5001)	|Slingbox & Iperf||
|[5004](https://www.speedguide.net/port.php?port=5004) - [5005](https://www.speedguide.net/port.php?port=5005)	|RTP||
|[5050](https://www.speedguide.net/port.php?port=5050)	|Yahoo! Messenger||
|[5060](https://www.speedguide.net/port.php?port=5060)	|SIP||
|[5190](https://www.speedguide.net/port.php?port=5190)	|AIM/ICQ||
|[5222](https://www.speedguide.net/port.php?port=5222) - [5223](https://www.speedguide.net/port.php?port=5223)	|XMPP/Jabber||
|[5432](https://www.speedguide.net/port.php?port=5432)	|PostgreSQL||
|[5500](https://www.speedguide.net/port.php?port=5500)	|VNC Server||
|[5554](https://www.speedguide.net/port.php?port=5554)	|Sasser||
|[5631](https://www.speedguide.net/port.php?port=5631) - [5632](https://www.speedguide.net/port.php?port=5632)	|pcAnywhere||
|[5800](https://www.speedguide.net/port.php?port=5800)	|VNC over HTTP||
|[5900+](https://www.speedguide.net/port.php?port=5900)	|VNC Server||
|[6000](https://www.speedguide.net/port.php?port=6000) - [6001](https://www.speedguide.net/port.php?port=6001)	|X11||
|[6112](https://www.speedguide.net/port.php?port=6112)	|Battle.net||
|[6129](https://www.speedguide.net/port.php?port=6129)	|DameWare||
|[6257](https://www.speedguide.net/port.php?port=6257)	|WinMX||
|[6346](https://www.speedguide.net/port.php?port=6346) - [6347](https://www.speedguide.net/port.php?port=6347)	|Gnutella||
|[6500](https://www.speedguide.net/port.php?port=6500)	|GameSpy Arcade||
|[6566](https://www.speedguide.net/port.php?port=6566)	|SANE||
|[6588](https://www.speedguide.net/port.php?port=6588)	|AnalogX||
|[6665](https://www.speedguide.net/port.php?port=6665) - [6669](https://www.speedguide.net/port.php?port=6669)	|IRC||
|[6679](https://www.speedguide.net/port.php?port=6679) and [6697](https://www.speedguide.net/port.php?port=6697)	|IRC over SSL||
|[6699](https://www.speedguide.net/port.php?port=6699)	|Napster||
|[6881](https://www.speedguide.net/port.php?port=6881) - [6999](https://www.speedguide.net/port.php?port=6999)	|BitTorrent||
|[6891](https://www.speedguide.net/port.php?port=6891) - [6901](https://www.speedguide.net/port.php?port=6901)	|Windows Live||
|[6970](https://www.speedguide.net/port.php?port=6970)	|Quicktime||
|[7212](https://www.speedguide.net/port.php?port=7212)	|GhostSurf||
|[7648](https://www.speedguide.net/port.php?port=7648) - [7649](https://www.speedguide.net/port.php?port=7649)	|CU-SeeMe||
|[8000](https://www.speedguide.net/port.php?port=8000)	|Internet Radio||
|[8080](https://www.speedguide.net/port.php?port=8080)	|HTTP Proxy||
|[8086](https://www.speedguide.net/port.php?port=8086) - [8087](https://www.speedguide.net/port.php?port=8087)	|Kaspersky AV||
|[8118](https://www.speedguide.net/port.php?port=8118)	|Privoxy||
|[8200](https://www.speedguide.net/port.php?port=8200)	|VMware Server||
|[8500](https://www.speedguide.net/port.php?port=8500)	|Adobe ColdFusion||
|[8767](https://www.speedguide.net/port.php?port=8767)	|TeamSpeak||
|[8866](https://www.speedguide.net/port.php?port=8866)	|Bagle.B||
|[9100](https://www.speedguide.net/port.php?port=9100)	|HP JetDirect||
|[9101](https://www.speedguide.net/port.php?port=9101) - [9103](https://www.speedguide.net/port.php?port=9103)	|Bacula||
|[9119](https://www.speedguide.net/port.php?port=9119)	|MXit||
|[9800](https://www.speedguide.net/port.php?port=9800)	|WebDAV||
|[9898](https://www.speedguide.net/port.php?port=9898)	|Dabber||
|[9988](https://www.speedguide.net/port.php?port=9988)	|Rbot/Spybot||
|[9999](https://www.speedguide.net/port.php?port=9999)	|Urchin||
|[10000](https://www.speedguide.net/port.php?port=10000)	|Webmin||
|[10000](https://www.speedguide.net/port.php?port=10000)	|BackupExec||
|[10113](https://www.speedguide.net/port.php?port=10113) - [10116](https://www.speedguide.net/port.php?port=10116)	|NetIQ||
|[11371](https://www.speedguide.net/port.php?port=11371)	|OpenPGP||
|[12035](https://www.speedguide.net/port.php?port=12035) - [12036](https://www.speedguide.net/port.php?port=12036)	|Second Life||
|[12345](https://www.speedguide.net/port.php?port=12345)	|NetBus||
|[13720](https://www.speedguide.net/port.php?port=13720) - [13721](https://www.speedguide.net/port.php?port=13721)	|NetBackup||
|[14567](https://www.speedguide.net/port.php?port=14567)	|Battlefield||
|[15118](https://www.speedguide.net/port.php?port=15118)	|Dipnet/Oddbob||
|[19226](https://www.speedguide.net/port.php?port=19226)	|AdminSecure||
|[19638](https://www.speedguide.net/port.php?port=19638)	|Ensim||
|[20000](https://www.speedguide.net/port.php?port=20000)	|Usermin||
|[24800](https://www.speedguide.net/port.php?port=24800)	|Synergy||
|[25999](https://www.speedguide.net/port.php?port=25999)	|Xfire||
|[27015](https://www.speedguide.net/port.php?port=27015)	|Half-Life||
|[27374](https://www.speedguide.net/port.php?port=27374)	|Sub7||
|[28960](https://www.speedguide.net/port.php?port=28960)	|Call of Duty||
|[31337](https://www.speedguide.net/port.php?port=31337)	|Back Orifice||
|[33434+](https://www.speedguide.net/port.php?port=33434)	|traceroute||

