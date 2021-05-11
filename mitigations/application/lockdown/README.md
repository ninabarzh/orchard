# Lock down environment

Lock down the development and production environment, using available security features to limit the scope of what the software under development can do to its host systems and adjacent networks. Even if an adversary finds and exploits a vulnerability, an environmental lockdown can restrict what the adversary can do, reducing the overall severity of the problem and making the adversary work harder. In some cases, the lockdown may prevent the problem from becoming a vulnerability in the first place.

* Run as an unprivileged user. Run any software with the lowest privileges possible.
* When using third-party libraries, use [libraries with an established record of good security](../libraries).
* Use operating system and hardware features that limit the impact of a successful attack. 
* Use [isolation and separation](Containers.md) such as sandboxes, docker, or similar, to limit access (and potential damages) to the environment. 
* Adopt secure configurations using security benchmarks or hardening guides.
* Proactively monitor for updates and patches to servers, scripts, software and applications. Use [vulnerability scanners](testing) and regularly apply security patches to check that the system does not have any known vulnerabilities. 
* Use some security by obscurity (robots.txt, .htaccess, nginx .conf, etc.) (SQL Injection Attacks)
* Use an application firewall (WAF)
* Search the domain for sensitive information, or strings that might not be secure. Dork it. (SQL Injection Attacks)
* [Allow locked-down clients](Allow-locked-down-clients.md)

