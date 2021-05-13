# Middle relay

Middle relays cover the largest part of the Tor circuit in a transmission and pass data to other relays in encrypted format. No middle relay knows more than its predecessor or its descendant. All the available middle relay nodes show themselves to guard and exit nodes so that any may connect to them for transmission.

Note: Even if any middle relay is known to transmit malicious traffic (such as an exploit or an attack) they are not held responsible as they are neither the source nor destination of the traffic. A middle relay will never be allowed to act as an exit node.
