# Server services audit

A number services of may be running by default:

* Public services accessible to anyone on the internet (anonymously). For example, a web server allowing access to a site.
* Private services intended to be only accessible by a select group of accounts or locations. Examples are a VPN server or a database control panel.
* Internal services intended to be only accessible from within the server itself, without exposing the service to the outside world. For example, a database that only accepts local connections.

## Questions

* Is this service really necessary?
* Is the service running on interfaces that it doesn't need to? Is it better to bound it to a single IP?
* Do the firewall rules allow legitimate traffic to pass through to this service?
* Do the firewall rules block traffic that is not legitimate?
* Is there some way security alerts about vulnerabilities for each of these services can be received?

## Means and methods

Use netstat:

    $ sudo netstat -plunt

Pay attention to Proto, Local Address, and PID/Program name. If the address is 0.0.0.0, then the service is accepting connections on all interfaces. 