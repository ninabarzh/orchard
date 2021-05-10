# Architecture and design validation

Tools that [test design decisions](https://www.owasp.org/index.php/OWASP_Secure_Application_Design_Project) for adhering to some basic security policies do not exist (yet) because there are no hard rules or silver bullets regarding what security concerns should be considered for a particular application, but some general secure design principles can help (and some of these are trade-offs with one or some of the other principles):

  * Minimise attack surface – Reduce the number and size of entry points that can be exploited by adversaries as much as possible
  * Principle of least privilege – Give just enough access level to do a job
  * Separate duties – Different entities have different roles
  * Defence in depth – Multiple layers of control make it harder to exploit a system
  * Fail secure – Limit the amount of information that is exposed when a system encounters errors
  * Economy of mechanisms – Keep things as simple as possible
  * Complete mediation – Validate all access to all resources of a system, always
  * Open design – Use proven open standards
  * Psychological acceptability – Protect a system but do not hamper users of the system
  * Weakest link – Any system is only as strong as its weakest link
  * Single point of failure – Add redundancy to critical systems


