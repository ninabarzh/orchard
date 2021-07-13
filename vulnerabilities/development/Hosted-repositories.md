# Hosted repositories

Git platforms have become the world's source code repositories. And with success come security and privacy concerns. Hosted repositories like Sourceforge, Launchpad, GitLab and BitBucket carry many of the same risks.

## GitHub

* [GitHub Security](https://help.github.com/articles/github-security/) itself is pretty good. 
  * Login is protected from brute force attacks with rate limiting
  * Passwords are filtered from all logs 
  * Passwords are one-way encrypted in a database using bcrypt. 
  * Login information is always sent over SSL 
  * GitHub recommends users to set up two-factor authentication (2FA)
  * [Bounty hunting is used](https://bounty.github.com/index.html#open-bounties) to make it more secure.

## What can possibly go wrong?

* [GitHub can be scraped](../../../resources/cheatsheets/Github-mining.md) to find private encryption keys and login credentials buried in code checked in to GitHub, and with those can be hacked, after which uploaded source code can be used in [supply chain attacks](Supply-chain-attacks.md).
* On GitHub C beats a path to examples of [ugly hacks](https://www.itworld.com/article/2918583/open-source-tools/c-leads-the-way-in-ugly-hacks.html) (read vulnerable code) in a wide range of applications, some of which are pretty interesting.


