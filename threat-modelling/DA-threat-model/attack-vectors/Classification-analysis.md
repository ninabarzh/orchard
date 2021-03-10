# Classification analysis

Classification analysis is a data mining technique that enables recognising patterns (recurring schemes) inside a dataset. It is considered an effective solution to improving marketing strategy performance, deleting superfluous information and creating subclasses.

## Classifiers

### Link-based classifiers

Real-world datasets, such as scientific publication datasets and social network datasets, contain interlinked entities and exhibit correlations among labels of the interlinked entities (for example, friendships and group memberships). Link-based classification can exploit such correlations in the link structure to identify private attributes.

### Group-based classifiers

Group-based classifiers can be combined with [auxiliary information](../assets/Auxiliary-information.md) to identify users in social networks (or to significantly reduce the set of possible candidates). Meaning that rather than tracking a user’s browser with cookies, it is possible to track a person. To determine the group membership of a user, well-known web browser history stealing attacks have been used: whenever a social network user visits a malicious website, this website can launch the de-anonymisation attack and learn the identity of its visitors.

### Similarity classifiers

This approach uses local features such as activity over time, text, geographic, and social features to form similarity classifiers that predict whether or not two accounts from two different social platforms are belonging to the same individual by deciding on similarities between them.

## Resources

* [To Join or Not to Join: The Illusion of Privacy in Social Networks with Mixed Public and Private User Profiles](https://users.soe.ucsc.edu/~getoor/Papers/zheleva-www09.pdf), Elena Zheleva and Lise Getoor, 2009
* [A Practical Attack to De-Anonymize Social Network Users](https://sites.cs.ucsb.edu/~chris/research/doc/oakland10_sonda.pdf), Gilbert Wondracek, Thorsten Holz, Engin Kirda, Christopher Kruegel, 2010
* [De-anonymizing Users Across Heterogeneous Social Computing Platforms](http://vision.soic.indiana.edu/papers/deanonymize2013icwsm.pdf), Mohammed Korayem, David Crandall, 2013

