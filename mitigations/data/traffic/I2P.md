# I2P 

[I2P](https://geti2p.net/en/) is a Distributed Peer to Peer Anonymous Network Layer that is strictly message-based. It allows you to send data between computers running I2P anonymously with multilayer end-to-end encryption. The name I2P derived from Invisible IRC Project (IIP) which was one of FreeNet's sister projects. I2P focuses exclusively on internal communication and not on proxying to the regular internet. I2P uses so-called garlic routing which involves clumping packets together into bigger packets. 

The combination of garlic routing, multilayer encryption -even the end points ("destinations") are cryptographic identifiers- and random padding on packets makes analysis of the content and detection of the origin of I2P traffic by third-party observers highly impractical if not nearly impossible.

The best use for I2P is for peer to peer file sharing and communication. 

## Garlic routing

[Garlic routing](https://geti2p.net/en/docs/how/garlic-routing) is a variant of onion routing that encrypts multiple messages together to make it more difficult for attackers to perform traffic analysis. I2P implements a packet switched routing instead of circuit switched (like Tor). Tunnels are unidirectional, and Tor's circuits are bidirectional. I2P bundles and encrypts in three places:

  * For building and routing through tunnels (layered encryption)
  * For determining the success or failure of end to end message delivery (bundling)
  * For publishing some network database entries (dampening the probability of a successful traffic analysis attack)

## Tunnels 

An I2P tunnel is a directed path through an explicitly selected list of routers. The first router that belongs to a tunnel is named gateway. The communication within a tunnel in unidirectional, this means that it is impossible to send back data without using another separated tunnel:

  * //outbound tunnels// are those tunnels used to send messages away from the tunnel creator.
  * //inbound tunnels// are those tunnels used to bring messages to the tunnel creator.

## Routers

There is no rigid distinction between a server and a pure client like there is in the Tor architecture. Information transits on network routers are able to decrypt only the respective layer. The information managed by each single node is composed by the IP address of the next router and the encrypted data to transfer.

## Layered encryption 

I2P is end-to-end encrypted. No information is sent in clear or decrypted. Each node has an internal network address different from the network IP address (and is not used). 

  * During connecting (build up of tunnel) only the routing instructions for the next hop are exposed to each peer.
  * During data transfer, messages are passed through the tunnel. Message and its routing instructions are only exposed to the endpoint of the tunnel.
  * An additional end to end layer of encryption hides the data from the outbound tunnel endpoint and the inbound tunnel gateway.
  * Each tunnel has an encryption layer to avoid unauthorized disclosure to peers inside the network.

## Installation

I2P is available for Windows, Mac OS X, GNU/Linux / BSD / Solaris, Debian /Ubuntu and Android. 

[Download the bundle for your device](https://geti2p.net/en/download) and install. That easy.