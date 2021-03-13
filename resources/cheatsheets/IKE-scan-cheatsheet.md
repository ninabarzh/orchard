# IKE-scan cheatsheet

[IKE-scan](https://github.com/royhills/ike-scan) discovers IKE hosts and can also fingerprint them using the retransmission backoff pattern. See the [Ike-scan Documentation](http://www.royhills.co.uk/wiki/index.php/Ike-scan_Documentation)

### IKE Main mode

    # ike-scan [address]

### IKE Aggressive mode

    # ike-scan -A [address]

In in IKE Main Mode the hash is already encrypted. In IKE Aggressive mode the authentication hash based on a preshared key (PSK) is transmitted as response to the initial packet of a vpn client that wants to establish an IPSec Tunnel (Hash_R). This hash is not encrypted. 

    # ike-scan -A [address] --id=myid -P[address]key

### 

psk-crack attempts to crack IKE Aggressive Mode pre-shared keys that have previously been gathered using ike-scan with the --pskcrack option and can operate in two different modes:

Dictionary cracking mode: the default mode in which psk-crack tries each candidate word from the dictionary file in turn until it finds a match, or all the words in the dictionary have been tried:

    # psk-crack -d /path/to/dictionary [address]key

Brute-force cracking mode: in this mode, psk-crack tries all possible combinations of a specified character set up to a given length:

    # psk-crack -b 5 [address]key

Or with a different charset;

    # psk-crack -b 5 --charset="01233456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz" [address]key



