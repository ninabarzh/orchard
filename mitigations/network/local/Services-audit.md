# Services audit

## Questions

  * Is this service really necessary?
  * Is the service running on interfaces that it doesn't need to? Is it better to bound it to a single IP?
  * Do the firewall rules allow legitimate traffic to pass through to this service?
  * Do the firewall rules block traffic that is not legitimate?
  * Is there some way security alerts about vulnerabilities for each of these services can be received?

Use `netstat` (if not available install net-tools):
    $ sudo netstat -plunt

Pay attention to `Proto`, `Local Address`, and `PID/Program` name. If the address is `0.0.0.0`, then the service is accepting connections on all interfaces. 


