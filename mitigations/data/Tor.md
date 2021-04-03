# Tor

The Internet is rife with [adversaries that are after our identity and information](../../threat-modelling/DA-threat-model/adversaries), and readily provides vulnerabilities that can be exploited for that. Many journalists, activists and researchers work have been exploited due to its vulnerable structure, sometimes with severe (life threatening) consequences. In some countries, proving that you connected to a particular server is enough to be prosecuted, but SSH doesn't provide a native way to obfuscate to whom it connects. For that, SSH with Tor (Tor proxy) can be used.

Onion routing networks are designed to resist a local adversary, one that can only see a subset of the network and the traffic on it. In a (sort of) mixnet like that, each node will only know the relay path in which it is involved, but not the whole path from the source to destination.

* If a government makes their own national internet, or routes traffic through specific servers to use deep packet inspection (DPI), running Tor does not provide security because the government is able to see the entire path. 
* Sometimes the Tor network is censored, and clients can't connect to it. An increasing number of censoring countries are using Deep Packet Inspection (DPI) to classify Internet traffic flows by protocol. While Tor uses bridge relays to get around a censor that blocks by IP address, the censor can use DPI to recognize and filter Tor traffic flows even when they connect to unexpected IP addresses. With pluggable transports, censorship against Tor can be bypassed.
* Not only that. If an attacker can see your traffic, and can see the website you're visiting, even with a path outside the adversary's control - they will still be able to correlate the traffic and learn you are visiting the website.
* If the same connection (the same set of relays) were to be used for a longer period of time a Tor connection could be vulnerable to statistical analysis, which is why the client software changes the entry node every ten minutes.

