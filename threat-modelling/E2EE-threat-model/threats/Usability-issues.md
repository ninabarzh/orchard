# Usability issues

Svenja Schroeder, Markus Huber, David Wind, and Christoph Rottermanner, did a user study with 28 participants on the usability of Signal's security features, the state-of-the-art application for secure mobile messaging [When SIGNAL hits the Fan: On the Usability and Security of State-of-the-Art Secure Mobile Messaging, Svenja Schröder, Markus Huber, David Wind, Christoph Rottermanner, 2016](https://web.archive.org/web/20160828135326/https://www.internetsociety.org/sites/default/files/09%20when-signal-hits-the-fan-on-the-usability-and-security-of-state-of-the-art-secure-mobile-messaging.pdf). Their study consisted of two parts: a usability study of the app with focus on it’s instant messaging and security features, and the execution of an actual MITM attack with a subsequent assessment of the users’ reactions. Their results showed that 21 of 28 participants failed to compare encryption keys to verify the identity of other users. The majority of these users however believed they succeeded while in reality they failed.

Usability problems, in terms of missing support, can lead to serious security breaches, e.g. aborting the re-establishment of a secure connection after an attack. The gaps between self-assessment, mental models of differing correctness respectively level of detail as well as actual outcome (un/successful defense) could be explained in several ways (not necessarily excluding each other):

* Either participants lacked the required knowledge
* The app failed to support the users
* Users simply had a different understanding of what “verification” meant
* The effort for successful defense was simply too high

During the MITM attack, SIGNAL was explicitly hinting at the fact that the connection could have been compromised. The fact that only 7 participants assumed the possibility of a MITM attack and only 3 thought that Bob reinstalled the app seem quite surprising. Either those users ignored, or did not read, the informational error message or simply excluded the possibility of an attack/reinstallation while remaining under the false illusion of security. The different strategies for verification and mitigation definitely hint at flawed mental models: users seem to lack an understanding of end-to-end encryption in general, possible attack scenarios and risk potentials [Secure Messaging? More Like A Secure Mess., EFF, 2018](https://www.eff.org/deeplinks/2018/03/secure-messaging-more-secure-mess).


