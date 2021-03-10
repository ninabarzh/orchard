# Target dataset

The set of anonymous data (also known as de-identified data). 

## Methods

The most common methods for de-identification (anonymisation) are by removing personal identifiable information (PII) such as ID and phone numbers, and using sophisticated anonymisation schemes such as k-anonymity, l-diversity, and t-closeness. The new kid on the block is differential privacy.

### Removing PII

Personal data, also known as personal information, personally identifying information (PII), or sensitive personal information (SPI), is any information relating to an identifiable person. Personally identifying information is a legal concept, not a technical concept, and is not used in the same way in all jurisdictions. Plus that with current re-identification attacks, the absence of PII data does not mean that the remaining data does not identify individuals.

### k-anonymity

A dataset provides k-anonymity protection if the information for each individual in the dataset cannot be distinguished from at least k − 1 individuals whose information also appears in the dataset.

k-anonymity and its variants can protect the privacy of structural data to some extent, but are susceptible to structure-based de-anonymisation attacks due to the limitations of the schemes (they are syntactic properties based) and the rich amount of [auxiliary information](Auxiliary-information.md) available to adversaries.

### Differential privacy

With static anonymization, an analyst must decide ahead of time which fields contain sensitive data, and then either remove or alter these fields before running the analysis, which reduces the quality of the data set. Plus, the analyst must also consider any auxiliary information a potential hacker might have that could lead to re-identification of the sensitive fields. With dynamic anonymisation, also called interactive anonymisation, data is anonymised on a query-by-query basis, without destroying the quality of the data set.

In differential privacy a query should not reveal whether any one person is present in a dataset or what their data are. Imagine two otherwise identical datasets, one with an individual's information in it, and one without it. The probability that a query will produce a given result is nearly the same whether conducted on the first or second dataset. If an individual's data does not affect the outcome of a query, then it might be okay to give this information because it is unlikely that the information would be tied back to the individual. And, if an analysis on a dataset finds a correlation between two characteristics, then interpretation of and assigning significance to the correlation, might have an effect on an individual with that characteristic, regardless of whether the individual's dataset was included in the study.

In short, differential privacy supposedly offers the benefits of data research without sacrificing privacy and supports “Legitimate Interest” processing by overcoming shortcomings of “static” data protection techniques that do not adequately protect data subjects against unauthorized re-identification when data is combined from multiple sources or used for various purposes.

Jane Bambauer, Krishnamurty Muralidhar, and Rathindra Sarathy have shown that by itself differential privacy will usually produce either wrong research results or useless privacy protections. Differential privacy was developed to protect the privacy of interactive data release. It cannot defend against structural data de-anonymisation attacks which can breach the privacy of non-interactive data releases.

