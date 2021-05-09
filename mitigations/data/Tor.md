# Using Tor

Onion routing networks like [Tor](../network/Tor.md) are designed to resist a local adversary, one that can only see a subset of the network and the traffic on it. In a (sort of) mixnet like that, each node will only know the relay path in which it is involved, but not the whole path from the source to destination.

## Warnings

* If a government makes their own national internet, or routes traffic through specific servers to use deep packet inspection (DPI), running Tor does not provide security because the government is able to see the entire path. 
* Sometimes the Tor network is censored, and clients can't connect to it. An increasing number of censoring countries are using Deep Packet Inspection (DPI) to classify Internet traffic flows by protocol. While Tor uses bridge relays to get around a censor that blocks by IP address, the censor can use DPI to recognize and filter Tor traffic flows even when they connect to unexpected IP addresses. With pluggable transports, censorship against Tor can be bypassed.
* Not only that. If an attacker can see your traffic, and can see the website you're visiting, even with a path outside the adversary's control - they will still be able to correlate the traffic and learn you are visiting the website.
* If the same connection (the same set of relays) were to be used for a longer period of time a Tor connection could be vulnerable to statistical analysis, which is why the client software changes the entry node every ten minutes.

## SSH with Tor

In some countries, proving that you connected to a particular server is enough to be prosecuted, but SSH doesn't provide a native way to obfuscate to whom it connects. For that, SSH with Tor (Tor proxy) can be used.

### Installation

Create the `/etc/apt/sources.list.d/torproxy.list` file and append:
```
echo 'deb http://deb.torproject.org/torproject.org <distribution> main' >> /etc/apt/sources.list.d/torproxy.list
```
Add the `gpg` key used to sign the packages and update apt:

```
# curl https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc | gpg --import
# gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | apt-key add -
# apt update
```

Also install `connect-proxy`, a simple relaying command to make tunnel TCP connections via SOCKS or HTTPS proxies. It is mainly intended to be used as proxy command of OpenSSH.
```
# apt-get install tor tor-geoipdb connect-proxy
```
### Configuration

Create or open `~/.ssh/config`
```
$ vi ~/.ssh/config
```
Append the below entry (replacing XXX.XXX.XXX.XXX with actual server domain name or IP and user with actual user):
```
Host jumphost
HostName XXX.XXX.XXX.XXX
User user
CheckHostIP no
Compression yes
Protocol 2
ProxyCommand connect -4 -S localhost:$orport $(tor-resolve %h localhost:$orport) %p
```

## Blocking Tor

Even the introduction of Bridge nodes did not stop certain organizations and governments from trying to detect and block the usage of Tor. The usual suspects for attempts at blocking Tor are:

* Blocking of the publicly available list of Tor relays.
* Creating Application Filter Policies in firewalls where only certain approved networks (LAN Networks) will be able to use specified proxy services.
* Creating an SSL Decryption policy in firewalls. IDS/IPS can be used to decrypt SSL certificates and detect traffic related to websites hosted on Tor.
* Tor browsing involves two types of ports, ORPort and DirPort. ORPorts (port 80 and 443) are used to make connections and transmissions and DirPorts (port 9001 and 9003) are used to fetch updates from the directory servers. Firewalls and IDS filters can be configured to monitor any traffic going towards or coming from the ports 9001 and 9003.

## Pluggable transports

Pluggable transports are tools that Tor can use to disguise the traffic it sends out. This can be useful in situations where an Internet Service Provider or other authority is actively blocking connections to the Tor network.

* `obfs3` makes Tor traffic look random, so that it does not look like Tor or any other protocol. While still included by default, it is recommended to use `obfs4` instead, as it has several security improvements over obfs3.
* `obfs4` makes Tor traffic look random like `obfs3`, and also prevents censors from finding bridges by Internet scanning. obfs4 bridges are less likely to be blocked than obfs3 bridges.
* FTE (format-transforming encryption) disguises Tor traffic as ordinary web (HTTP) traffic.
* meek transports all make it look like you are browsing a major web site instead of using Tor. meek-amazon makes it look like you are using Amazon Web Services; meek-azure makes it look like you are using a Microsoft web site; and meek-google makes it look like you are using Google search.
* Snowflake is an improvement upon Flashproxy. It sends your traffic through WebRTC, a peer-to-peer protocol with built-in NAT punching.

## Applications

* The free Firefox-based [Tor Browser Bundle](https://www.torproject.org/projects/torbrowser.html) integrates the Tor network's enhanced privacy and security. Its installation is easy and it works out of the box.
* [Orbot](https://guardianproject.info/apps/orbot/) creates a private mobile internet connection on Android
* [OnionShare](https://onionshare.org/) is an open source tool that lets you securely and anonymously share a file of any size.
* The [relay search tool](https://metrics.torproject.org/rs.html) displays data about single relays and bridges in the Tor network. It provides useful information on how relays are configured along with graphs about their past.
* [Stem](https://stem.torproject.org/) is a Python implementation of Tor's directory and control specifications, a controller library that can be used to interact with Tor. With it you can write scripts and applications with capabilities similar to Vidalia and arm. 
* [Nyx](https://nyx.torproject.org/) is a command-line monitor for Tor
