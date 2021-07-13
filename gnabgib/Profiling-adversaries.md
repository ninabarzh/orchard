# Pofiling attackers

Every attacker/adversary has an intent and a motive to attack a target and for a successful attack their capabilities are also important. From highly sophisticated state and non-state adversaries to script kiddies they have objectives. Profiling adversaries requires an in-depth understanding of the motivations, psychology and decision-making of potential adversaries of attacks on a particular target.

## Re-useful questions
* Who are the possible adversaries?
* Why would they be targeting us?
* What kind of information would they be after and why?
* What kind of resources/skills/data/information would they be leveraging?

## Potential adversaries

* Insiders – Disgruntled employees, (economic) spies, ...
* Outsiders – Ex-Employees, Nation State attackers, cyber criminals, script kiddies, hacktivists, ...

## Motivations/intentions

* Financial gain (the most likely motivation, maybe we can use [the diamond model](https://www.isc.hbs.edu/competitiveness-economic-development/frameworks-and-key-concepts/Pages/the-diamond-model.aspx))
* Fame 
* Proving oneself and/or gaining trust of a group of hackers
* Intellectual challenge
* Wanting to damage or disrupt services
* Cyber espionage
* Personal grievances and grudges
* Political motivation
* Terrorism

## Targets
* Individuals
* Organisations
* Nations/countries

## Understanding the adversary

* Assume adversaries are also profiling and spending days, weeks or months to collect information about their targets. 
* To launch an attack or gather information, they will rely on the available tools and capabilities that they have.

Monitoring such tools and understanding them can assist in preparing against what could be coming.

### Tools available to all

* Kali Linux comes with plethora of tools starting from gathering information to launch attacks.
* AutoSploit
* MetaSploit
* PowerSploit
* Exploit builders (usually for sale/rent)
* XXXXX-as-a-service (malware, ransomware, crypto, etc for sale or rent, even customised services such as banking injects). 
* Services like BlackTDS (available on underground markets)
* Cracked vendor tools
* Tools on Github

### Underground marketplaces

* exploit.in
* antichat.ru
* cop.su
* zloy.bz
* hackersoft.ru
* darkweb.ws

## Example: Lazarus

Take for example, the [phishing attacks on UN and NGO staff that work on DPRK of October 2019](https://blog.lookout.com/lookout-phishing-ai-discovers-phishing-attack-targeting-humanitarian-organizations). 

### Geopolitical context

The most likely adversary was the Lazarus Group of North Korea (alias Silent Chollima, Group 123, Hidden Cobra, Zinc, DarkSeoul, Blockbuster, Operation Troy, and 10 Days of Rain), looking for the “[decapitation plan](http://www.koreaherald.com/view.php?ud=20170709000290)”, now also among UN staff working on DPRK. 

### A bit of background

The earliest known attack that the Lazarus group is held responsible for is “Operation Troy” (2009–2012), a cyber-espionage campaign that used unsophisticated distributed denial-of-service attack (DDoS) techniques to target the South Korean government in Seoul. They are also considered responsible for attacks in 2011 and 2013 and possibly also a 2007 attack targeting South Korea. A notable attack was the 2014 attack on Sony Pictures, showing more sophisticated techniques. Currently [the group is thought to have two subgroups](https://media.kasperskycontenthub.com/wp-content/uploads/sites/43/2018/03/07180244/Lazarus_Under_The_Hood_PDF_final.pdf):

* Bluenoroff, named after the tools used in attacks on financial networks. hacking into financial institutions (Unit 180), hijacking gambling sessions, selling pirated and cracked software, all of which is focused on funnelling funds to North Korea
* Andariel, focusing on gathering intelligence from other nations, and in some cases disrupting rival states and military targets (Unit 121), and it seems like classified wartime contingency plans jointly drawn by the United States and South Korea are of interest, including the military’s “decapitation” plan (removal of Kim Jong-un), if and when war breaks out.

### Tools, techniques, procedures (TTP's) of Lazarus

According to the South China Morning Post, North Korea’s most promising hackers are sent to Shenyang, in China to learn how to put malware of all kinds on hosts (vulnerable endpoints). Domestic education includes the Kim Chaek University of Technology and Kim il Sung University. North Korean adversaries have left many clues in their wake and throughout the evolution of their malware arsenal.

When a malware campaign becomes less successful, it is common practice to change some of its basics such as using a different packer to bypass defences. By identifying reused code, valuable insights about “[ancestral relations](https://www.mcafee.com/blogs/blogs/other-blogs/mcafee-labs/examining-code-reuse-reveals-undiscovered-links-among-north-koreas-malware-families/?hilite=%2527SMB%2527)” can be gleaned. Lazarus then appears to be a collective name for many DPRK cyber operations, and there seem to be links between malware families used in different campaigns. The malwares most likely created by Unit 123 seem connected to each other but separate from those used by Lazarus. Although these are different units focusing on different areas, there seems to be a parallel structure in which they collaborate during certain campaigns.

The group [is known for spear phishing attacks](https://www.group-ib.com/resources/threat-research/lazarus.html) like emails with a fake first content and attached document, which when opened encourages the user to “enable content” to see a document they're told was created with an earlier version of Word (but really enables Visual Basic macros and allows the attackers to begin the process of implanting malware) or by hijacking sites, like apparently used in this attack.

### Attack scenario

* Motive : Finding a copy of the plan
* Targets : UN and NGO staff that work on DPRK.
* Tools : A phishing kit, first-stage dropper malware and a C&C. Phishing document templates and pages are readily available.
* Hijacking sites the targets are most likely to visit : JavaScript code logic on the phishing pages detects if the page is being loaded on a mobile device and delivers mobile-specific content. 
* Actions : The malware starts exfiltration over an alternative protocol or a C&C takes over for privilege escalation, lateral movement and collection (staged, from local system and input capture)

### Threat
People have been taught that one of the key steps in protecting their personal information online is to ensure that it is entered only over an encrypted connection (check for the lock symbol in the browser address bar or that the web address begins with https://). And that makes attacks using SSL certificates extremely dangerous because most users associate the presence of a valid SSL certificate with an increased level of security. In these attacks, bona fide certificate owners find that they are unwittingly providing facilities for phishing because their site has been compromised by an adversary.