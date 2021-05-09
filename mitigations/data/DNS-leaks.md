# DNS leaks

![Leaky boat](https://github.com/tymyrddin/orchard/blob/main/mitigations/assets/images/leaky-boat.png)

In addition to [VPN connection failures](VPN-fail-open.md), the other big threat to your anonymity when using a VPN service is that of DNS leaks, which can result in for example, your ISP being able to ‘see’ and monitor your online activity even though you think you are safely protected by an encrypted VPN tunnel.

## Use wireshark to check for leaks 

This is an example in a debian virtualbox VM, but is also valid in general for other setups.

Virtual machines receive their network address and configuration on the private network from a DHCP server integrated into VirtualBox. The IP address assigned to the virtual machine is on a completely different network than the host (but can be seen with Traffic monitoring from the host). As more than one card of a virtual machine can be set up to use Network address translation (NAT), the first card is connected to the private network 10.0.2.0, the second card to the network 10.0.3.0 and so on.

To check if you have DNS leaks, fire up wireshark:

  * Start capturing on eth0 and connect to the VPN.
  * After capturing either a fixed number of packets, or an amount of data or for a specific time period, go to //Statistics -> Endpoints//

![Wireshark endpoints](https://github.com/tymyrddin/orchard/blob/main/mitigations/assets/images/statistics-endpoints.png)

There should only be one public IP address, namely that of the VPN server that you’re connected to. The ''10.0.2.15'' in this image is a local address.

![Wireshark endpoints](https://github.com/tymyrddin/orchard/blob/main/mitigations/assets/images/statistics-endpoints2.png)


