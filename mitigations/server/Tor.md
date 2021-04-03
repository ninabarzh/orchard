# Tor

The Tor network consists of volunteer operated servers that improve the privacy and security of data. A series of virtual tunnels are created between relays of the network, and for each data transmission a random relay path is chosen.

* [Entry/Guard](#entryguard-relays) relays are best set up on servers.
* In countries where Tor is blocked by governments and/or corporations, set up [bridge relays](#bridge-relay) instead of Entry/Guard relays.
* Running a [middle relay](#middle-relay) is most suitable for users who want to support the network and/or use Tor from a PC at home.
* Only run an [exit relay](#exit-relay) if you are ready to receive multiple complaints, legal notices, take down notices or DMCA notices.

## Entry/Guard relays

Entry/Guard relays are the entry point to the Tor network. A client that wants to connect to the Tor network will first connect to a guard node. Guard nodes can see the real IP address of the connecting client. The list of guard nodes is available in the public list of Tor nodes. 

## Bridge relay

Bridge relays are entry relays too, but are not publicly listed. The below is for debian and friends.

### Installation

Create the `/etc/apt/sources.list.d/torserver.list` file and append:

```
# echo 'deb http://deb.torproject.org/torproject.org <distribution> main' >> /etc/apt/sources.list.d/torserver.list
# echo 'deb http://deb.torproject.org/torproject.org obfs4proxy main' >> /etc/apt/sources.list.d/torserver.list
```
Add the `gpg` key used to sign the packages and update apt:
```
# curl https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc | gpg --import
# gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | apt-key add -
# apt update
```
Also install and enable Pluggable transports. This helps users in heavily censored regions to get access:

```
# apt-get install tor tor-geoipdb obfs4proxy
```
### Configuration

Stop the service:
```
# service tor stop
```
Get the bridge torrc:
```
# cd /etc/tor
# mv torrc torrc.dist
# wget -O torrc https://www.torservers.net/misc/config/torrc-bridge
```
Restart the tor service:
```
# service tor start
```
### Firewall

Punch a hole in the firewall for incoming connections on TCP port 443.

### Verify

Verify by looking in `/var/log/tor/log`:
```
<timestamp>  [notice] Bootstrapped 100%: Done.
<timestamp>  [notice] Now checking whether ORPort XXX.XXX.XXX.XXX:443 is reachable... 
...
<timestamp>  [notice] Self-testing indicates your ORPort is reachable from the outside. Excellent.
<timestamp>  [notice] Performing bandwidth self-test...done.
```
## Middle relay

Middle relays cover the largest part of the Tor circuit in a transmission and pass data to other relays in encrypted format. No middle relay knows more than its predecessor or its descendant. All the available middle relay nodes show themselves to guard and exit nodes so that any may connect to them for transmission.

Note: Even if any middle relay is known to transmit malicious traffic (such as an exploit or an attack) they are not held responsible as they are neither the source nor destination of the traffic. A middle relay will never be allowed to act as an exit node.

## Exit relay

An exit relay is the final relay in a Tor circuit. They send the data to their destination and their IP address will be visible to that destination. They are often considered the culprit because of being perceived as the origin of the traffic.



