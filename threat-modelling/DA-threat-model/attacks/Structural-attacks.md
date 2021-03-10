# Structural attacks

This type of attack typically exploits social network structures by using graph matching on network datasets. Many people have accounts through various social networks such as Facebook, Twitter, etc. With structure-based attacks an individual's network context can be used to identify them even if other identifying information is removed. Even when equipped with advanced anonymisation techniques, the privacy of structural data can suffer from de-anonymisation attacks assuming that adversaries have access to rich auxiliary information from other channels.

## Methods

Abstractly there is a graph G from which two graphs Gt (for “target”) and Ga (for “auxiliary”) are derived via some stochastic process. There is thus a natural notion of (partial) correspondence between the nodes of Gt and Ga; the goal of de-anonymization is to recover this correspondence.

The stochastic process involved could be as simple as the deletion of random edges. At the other extreme, if we're considering two entirely different online social networks, say Facebook and LinkedIn, then $ G$ is the underlying social graph of human relationships, and Gt and Ga are generated according to the processes by which users join online social networks, which has no simple algorithmic description.

## Algorithms

The privacy-sensitive data closely related to individual behaviour usually contain rich graph structural characteristics. For example, social network data can be modelled as graphs and mobility traces (WiFi contacts, Instant Message contacts) can also be modelled as graph topologies. Even general spatio-temporal data (mobility traces) with the classical (latitude, longitude, timestamp) format can be converted to structural data. The resulting graphs represent entities connected by edges representing relations such as friendship, communication or shared activity, and can be combined for de-anonymisation purposes. Heuristics such as eccentricity, edge directionality, and reverse match receive an entirely new meaning.

Backstrom designed both active and passive attacks to break the privacy of SN users (leveraging the success of a “sybil” attack before actual anonymised data publication, therefor less practical); Narayanan effectively de-anonymised a Twitter dataset by using a Flickr dataset as auxiliary information based on the inherent cross-site correlations; Nilizadeh exploited the community structure of graphs to de-anonymise social networks; Srivatsa proposed to de-anonymise a set of location traces based on a social network (only suitable for small datasets due to the computational infeasibility of finding a proper land-mark mappings for large datasets); and the Grasshopper technique has a higher de-anonymisation effectiveness than other structural attacks.

Recently, in 2017 a novel blind structure-based de-anonymization attack, which does not require the attacker to have prior information (seeds), saw the light. The method experimentally demonstrated to be robust to data perturbations and claims to significantly outperform state-of-the-art de-anonymization techniques by up to 10× improvement. The method uses multi-hop neighbourhood information, and optimises the process of de-anonymization by exploiting enhanced machine learning techniques.

## Mitigation

Several papers have claimed to provide k-anonymity, or variants thereof, for graphs. These have only been evaluated against graphs with a small number of nodes and small average degree, and only consider the threat of adversaries with restricted types of auxiliary information, which does not include global information such as another graph that is structurally related to the target graph.

Differential privacy might offer a potential method to bypass the need for anonymisation. A differentially private dataset (primarily, a sanitised item-item covariance matrix) instead of raw user data could be used, but restricts the class of machine learning algorithms that can be applied, and may require a shift from the “release-and-forget” model to an online privacy-preserving computation model.

