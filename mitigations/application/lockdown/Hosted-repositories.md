# Hosted repositories

* Set up 2FK
* Use GitHub's search features as well as [scraping tools](../../../resources/cheatsheets/Github-mining.md) to check your own code for potential data leaks.
* Identify, configure and [audit](https://github.com/mozilla-services/GitHub-Audit) production branches to
  * Not allow force pushes.
  * Only give commit privileges to a small set of users.
  * Enforce those restrictions on admins & owners too!
  * Require all commits to be PGP signed (keys known in advance).
* Read [more recommendations by Mozilla](https://wiki.mozilla.org/GitHub/Repository_Security) (they learned the hard way, no need to repeat that for ourselves).
* As of November 2017, [GitHub tracks reported vulnerabilities](https://help.github.com/articles/about-security-alerts-for-vulnerable-dependencies/) in certain dependencies and provides security alerts to affected repositories.