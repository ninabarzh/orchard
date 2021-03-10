# Linkage attacks

Linkage attacks are another common form of de-anonymisation attacks. In this attack, adversaries collect and combine auxiliary information about a certain individual from multiple data sources with their anonymised records in a dataset to form a whole picture about their target, which is often an individual’s personally identifiable information.

## Methods

For example, the adversary downloads a sanitised production network dataset that was released in the past. The dataset contains captured traces in which all MAC addresses have been sanitised and are thus unknown to the adversary. The adversary observes a sequence of AP association records of a target victim for a short period of time, to infer the MAC address from the released dataset that is associated with the victim. The attacker then obtains broader knowledge of the victim’s mobility history from the released dataset, which leads to an infringement on the privacy of the user.

The possibilities are endless

* A health care provider shares anonymised data with for example researchers from a pharmaceutical or health assurance company about medical conditions. The export contains “Gender,” “Postal code,” “Date of birth,” and “Medical condition description.” An adversary can easily use an open data (public made) voter list that contains “Name,” “Gender,” “Postal code,” and “Date of birth” to cross-reference the patients.
* Netflix published data about movie rankings for 500,000 customers, and researchers showed they could de-anonymise the data using a few additional inputs from IMDb.
* AOL published search data for 650,000 users, thinking it was enough to anonymise their name using a unique ID. Unfortunately, most users often query their own name.
* Someone with access to an anonymous dataset of telephone records, might partially de-anonymise it by correlating it with a telephone order database of a catalogue merchant.
* Amazon online book reviews can be key to partially de-anonymising a database of credit card purchases, or a larger database of anonymous book reviews.
* Search engine databases with logs of internet searches, could easily be used de-anonymise a database of internet purchases, or zoom in on searches of medical terms to de-anonymise a public health database.
* And vice versa, detailed customer and purchase information datasets can be used to partially de-anonymise any released large anonymised search engine data set.
* A data broker holding databases of several companies might be able to de-anonymise most of the records in those databases.

## Mitigation

The most common approach to mitigate linkage or correlation attacks is to anonymise data before exporting by removing personally identifiable information (PII). This does not suffice. At all. A better approach to protect against correlation attacks is to simply not share.

It was proposed, that if data is shared — to create layers of abstraction or generalisation by redacting parts of the data. If only microdata that contain spatial information in an aggregated form are released, the choice of applicable techniques for analysis becomes drastically reduced because distance calculations that are based on aggregated data become difficult and imprecise, especially for entities that are spatially close to each other. This then leads to the conclusion that to continue to do research on large datasets with privacy protection for the owners of the data, it is necessary to investigate the extent to which additionally published (approximate) inter-record distances influence the risk of identity disclosure and how a possible non-acceptable increase of this risk can be prevented.

That will not suffice either. [Advanced anonymisation techniques of target datasets](../assets/Target-dataset.md) are needed.

