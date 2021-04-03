# Tor

Onion routing networks like Tor are designed to resist a local adversary, one that can only see a subset of the network and the traffic on it. In a (sort of) mixnet like that, each node will only know the relay path in which it is involved, but not the whole path from the source to destination.

* If a government makes their own national internet, or routes traffic through specific servers to use deep packet inspection (DPI), running Tor does not provide security because the government is able to see the entire path. 
* Sometimes the Tor network is censored, and clients can't connect to it. An increasing number of censoring countries are using Deep Packet Inspection (DPI) to classify Internet traffic flows by protocol. While Tor uses bridge relays to get around a censor that blocks by IP address, the censor can use DPI to recognize and filter Tor traffic flows even when they connect to unexpected IP addresses. With pluggable transports, censorship against Tor can be bypassed.
* Not only that. If an attacker can see your traffic, and can see the website you're visiting, even with a path outside the adversary's control - they will still be able to correlate the traffic and learn you are visiting the website.
* If the same connection (the same set of relays) were to be used for a longer period of time a Tor connection could be vulnerable to statistical analysis, which is why the client software changes the entry node every ten minutes.

In some countries, proving that you connected to a particular server is enough to be prosecuted, but SSH doesn't provide a native way to obfuscate to whom it connects. For that, SSH with Tor (Tor proxy) can be used.

## Installation

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
## Configuration

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
