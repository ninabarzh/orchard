# IKE-scan cheatsheet

[IKE-scan](https://github.com/royhills/ike-scan) discovers IKE hosts and can also fingerprint them using the retransmission backoff pattern. See the [Ike-scan Documentation](http://www.royhills.co.uk/wiki/index.php/Ike-scan_Documentation)

### IKE Main mode

    # ike-scan [address]

### IKE Aggressive mode

    # ike-scan -A [address]

In in IKE Main Mode the hash is already encrypted. In IKE Aggressive mode the authentication hash based on a preshared key (PSK) is transmitted as response to the initial packet of a vpn client that wants to establish an IPSec Tunnel (Hash_R). This hash is not encrypted. 

    # ike-scan -A [address] --id=myid -P[address]key

