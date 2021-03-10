# Information exposure

The intentional or unintentional disclosure of information to an actor (adversary) not explicitly authorised to have access to that information.

## Development and operations

* Developer comments left in page responses can disclose information (server directory structure, query structure, and internal network information) that can be used in attacks.
* [Improper security configurations](../attack-vectors/Misconfigurations.md) can leak information (software version numbers and verbose error messages for debugging and troubleshooting purposes) that will greatly assist an attacker (detailed insight into the framework, languages, or pre-built functions being used) in constructing attacks against the front end.

## Search results

* Search results can show documents that the user has no read access for (pages from default web server installations, /etc directories in ftp search results, for example)
* The total count of documents found for a query can show an exact number and includes documents to which the user has no read access.
* The total count of facets found for a query can show an exact number and include documents to which the user has no read access.
* Some search engines return a little context with each result, which is very helpful for attackers if they wish to know the content of a private file, if it is returned as a result but not retrievable. Some engines do not provide such data, but … if an attacker is willing to throw a lot of queries at the engine, a file (or sections of it) may still be reconstructed. Not trivial, but feasible. And this vector can be much improved by taking into account language syntax and probabilities for pairs of words.
* Search results can include information from [documents](../assets/Documents.md) that by the [GDPR is considered sensitive personal data](GDPR-non-compliance.md) – including “special categories” of data relating to racial or ethnic origin, political opinion, sexuality, religious or philosophical beliefs, trade union membership, health or genetic data, or criminal convictions, and other sensitive data such as identity related or financial data.

## Data industry

* Search engines can track personal information of a user to serve that user with ads that match his or her personal preferences. The search engine caches search terms and pages visited and associates it with a particular user. Adding encryption to user search terms, does not keep that information from going to the search engine and anyone it chooses to share that information with.

