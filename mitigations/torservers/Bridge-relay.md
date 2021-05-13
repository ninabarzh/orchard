# Bridge relay

Bridge relays are entry relays too, but are not publicly listed. The below is for debian and friends.

## Installation

Create the `/etc/apt/sources.list.d/torserver.list` file and append:

    # echo 'deb http://deb.torproject.org/torproject.org <distribution> main' >> /etc/apt/sources.list.d/torserver.list
    # echo 'deb http://deb.torproject.org/torproject.org obfs4proxy main' >> /etc/apt/sources.list.d/torserver.list

Add the `gpg` key used to sign the packages and update apt:

    # curl https://deb.torproject.org/torproject.org/A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89.asc | gpg --import
    # gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | apt-key add -
    # apt update

Also install and enable Pluggable transports. This helps users in heavily censored regions to get access:

    # apt-get install tor tor-geoipdb obfs4proxy

## Configuration

Stop the service:

    # service tor stop

Get the bridge torrc:

    # cd /etc/tor
    # mv torrc torrc.dist
    # wget -O torrc https://www.torservers.net/misc/config/torrc-bridge

Restart the tor service:

    # service tor start

## Firewall

Punch a hole in the [firewall] for incoming connections on TCP port 443.

## Verify

Verify by looking in `/var/log/tor/log`:

    <timestamp>  [notice] Bootstrapped 100%: Done.
    <timestamp>  [notice] Now checking whether ORPort XXX.XXX.XXX.XXX:443 is reachable... 
    ...
    <timestamp>  [notice] Self-testing indicates your ORPort is reachable from the outside. Excellent.
    <timestamp>  [notice] Performing bandwidth self-test...done.

