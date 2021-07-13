# Common database vulnerabilities

* Excessive privilege abuse: When users (or applications) are granted database access privileges that exceed the requirements of their function, these privileges may be abused for malicious purpose.
* Legitimate privilege abuse: Users may also abuse legitimate database privileges for unauthorised purposes. This can be intentional (for money), more likely it is not (like when taking work home), but it can happen. Even if the structure of an application normally limits users to viewing records (multiple records cannot be viewed simultaneously and electronic copies are not allowed) this can be circumvented by connecting to the database using an alternative client.
* Privilege elevation: Attackers can take advantage of database platform software vulnerabilities to convert access privileges from those of an ordinary user to those of an administrator. Vulnerabilities may be found in stored procedures, built-in functions, protocol implementations, and SQL statements.
* Vulnerabilities in the underlying OS and additional services installed on a database server may lead to unauthorised access, data corruption, or denial of service.
* In an [SQL injection attack](../../../trees/application-hacking/SQL-injection.md), an adversary typically injects unauthorised database statements into a vulnerable SQL data channel. Targeted data channels include stored procedures and web application input parameters. These injected statements are then passed to the database where they are executed. Using SQL injection, attackers may gain unrestricted access to an entire database. The problem with NoSQL databases is that often there are not yet or not deeply enough tested API's available (for a language). This means writing it ourselves, and there might always be something we overlook.
* Weak audit trail: Logging of all sensitive and/or unusual database transactions should be part of the foundation underlying any database deployment. Weak database audit policy represents a serious organisational risk on many levels:
    * Regulatory risk: Organisations with weak (or sometimes non-existent) database audit mechanisms will increasingly find that they are at odds with government regulatory requirements.
    * Deterrence: Database audit mechanisms serve to deter attackers who know that database audit tracking provide investigators with forensics link intruders to a crime. If not there, not happening.
    * Detection and recovery: If an adversary circumvents other defences, audit data can identify the existence of a violation after the fact and can then be used to link a violation to a particular user and/or repair the system. If not there, not happening.
* What can possibly go wrong?
    * Lack of user accountability: When users access the database via web applications, native audit mechanisms have no awareness of specific user identities. All user activity is associated with the web application account name. When native audit logs reveal fraudulent database transactions, there is no link to the responsible user.
    * Performance degradation: Native database audit mechanisms are notorious for consuming CPU and disk resources. The performance decline experienced when audit features are enabled, causes decision makers in many organisations to scale back or even eliminate auditing.
    * Separation of duties: Users with administrative access (either legitimately or maliciously obtained can simply turn off auditing to hide fraudulent activity. Audit duties should ideally be separate from both database administrators and the database server platform.
    * Limited granularity: Many native audit mechanisms do not record details necessary to support attack detection, forensics and recovery. Database client application, source IP addresses, query response attributes, and failed queries (an important attack reconnaissance indicator) are not recorded by many native mechanisms.
    * Proprietary: Audit mechanisms are unique to database server platforms. All logs are different from each other. When having mixed database environments, this virtually eliminates implementation of a uniform, scalable audit process.
* [Denial of Service (DOS)](../../../trees/network-attacks/DoS.md) is a general attack category in which access to network applications or data is denied to intended users. Denial of service conditions may be created via many techniques, data corruption, network flooding, and server resource overload (the most common).
* Database communication protocol: A growing number of security vulnerabilities are appearing in the database communication protocols of all database vendors.
* Weak authentication schemes allow attackers to assume the identity of legitimate database users by stealing or otherwise obtaining login credentials. An adversary may employ any number of strategies to obtain credentials:
    * Brute force: repeatedly entering username/password combinations until in, either via guessing or systematic (and automated) enumeration of all possible username/password combinations.
    * Social engineering: taking advantage the natural human tendency to trust in order to convince others.
    * Direct credential theft: stealing login credentials by copying post-it notes, password files, whatever is useful.
* Backup data exposure: Backup database storage media are often completely unprotected from attack.
