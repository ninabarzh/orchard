# Phases of pentesting

## Pre-Engagement Interactions (Scoping)

1. Outline the logistics of the test, expectations, legal implications, objectives and goals to be achieved.
1. All parties understand the risks.
1. Understand organisational culture as much as possible.
1. Determine pentesting strategy ([type](Types-of-pentesting.md) and [purpose](Purpose-of-pentesting.md))
1. Decide on what is explicitly out of scope, for example pentesting cloud services or zero-day attack simulations.

## Reconnaissance

Depending on which type of pentest was agreed on, a penetration tester may have varying degrees of information about an organisation or may need to identify critical information on their own to uncover vulnerabilities and entry points in your environment.

1. Search engine queries
1. Domain name searches/WHOIS lookups
1. Social Engineering
1. Tax Records
1. Email addresses, usernames, social networks, ...
1. Ping sweeps, port scanning, reverse DNS, packet sniffing
1. Dumpster Diving
1. Tailgating

## Threat Modelling
During the [threat modelling and vulnerability identification](https://github.com/tymyrddin/orchard/tree/main/threat-modelling) phase, the tester identifies targets and maps the attack vectors. Any information gathered during the Reconnaissance phase is used to inform the method of attack during the penetration test.

Assets – identify and categorise high-value assets
1. People data (including users and/or customers if applicable)
1. Technical data

Threats – identify and categorise internal and external threats
1. Internal threats – Management, employees, vendors, etc.
1. External threats – Ports, Network Protocols, Web Applications, Network Traffic, etc.

## Exploitation

<br />
<img align="right" src="https://github.com/tymyrddin/orchard/blob/main/trees/assets/images/roadrunner.png" size="25%">

Testing the possible exploits found within network, applications, and data. The goal for an ethical hacker is to see exactly how far they can get into the environment, identify high-value targets, and avoid any detection. Rather standard are: 
1. Web Application Attacks
1. Network Attacks
1. Memory-based attacks
1. Wi-Fi attacks
1. Zero-Day Angle
1. Physical Attacks
1. Social engineering

_Loosen that bird, but stay within scope!_

## Post-Exploitation

1. Everything (methods, etc) has been documented
1. Determine impact of the compromised systems and any value associated with the sensitive data captured.
1. Provide recommendations on how to remediate the vulnerabilities within the environment.
1. Remove any executables, scripts, and temporary files from compromised systems
1. Reconfigure settings back to the original parameters prior to the pentesting
1. Eliminate any rootkits installed in the environment
1. Remove any user accounts created to connect to the compromised system

## Reporting

1. Make a report and present results