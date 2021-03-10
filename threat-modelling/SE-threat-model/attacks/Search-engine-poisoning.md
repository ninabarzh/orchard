# Search engine poisoning

"Gotta feel kind of bad for nation-state hackers who spend years implanting and cultivating some hardware exploit, only to discover the entire target database is already exposed to anyone with a web browser."

The phrase search engine optimization poisoning (SEO poisoning) is in use to describe one of two types of activities:

* [Black hat SEO](../adversaries/Black-hat-SEO.md) techniques used to achieve high search engine ranking, usually (but not only) to attack visitors. The techniques often involve [content spamming](Content-spamming.md), (all sorts of) [link spamming](Link-spamming.md), [cloaking](../attack-vectors/Cloaking.md), [doorway pages](../attack-vectors/Doorway-pages.md) and [redirection](../attack-vectors/Redirection.md). These attacks often follow trending [search terms](../assets/Search-terms.md). For example during natural disasters, when attackers attempt to have victims send monetary aid to fake accounts or during major political campaigns and other major world events. If its intent is malicious, the attacker aims to install [malware](https://github.com/tymyrddin/trees/blob/main/application-hacking/SEO-poisoning.md) (attack tree) such as trojans, attack the user’s machine, or trick the user into providing sensitive data.
* Exploiting typical web vulnerabilities on existing high-ranking web pages and using them to spread malware. If, for example, a high-ranking web page has a stored XSS vulnerability, the code may either directly attempt to spread malware or redirect the user to a different site (using redirection like used in black hat SEO).

