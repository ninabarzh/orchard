# Graph matching

Graph matching is a network structure vector and the most common approach. It focuses on matching two graphs from the same target domain or two different domains. Privacy can be breached once its network structure is revealed, as a standard technique of re-identification can be developed based on that.

* Find the largest common sub-graph between a pair of ego nets
* Focus on common nodes of two graphs that are at 1-hop from the center
* Use the degree distribution of nodes and observe the 1-hop neighbourhood degree distribution of the common nodes, storing each node's degrees in a list as a signature.
* If matching signatures are found between a pair of nodes from the two graphs, those nodes are considered to be the same.

This simple version does not work with graphs where common nodes are 2-hops away from the centre, but n-hop algorithms have been developed and can de-anonymise more data. Naive anonymisation of social network graphs often uses deleting all identifying information of the users, while maintaining the original graph structure.

## Methods

### Seed & Grow

Graph matching can start by creating a node (for example a user account) in a social graph and building up links with other nodes. Some call this graph matching expansion process “seed & grow”. When combined with link prediction it can give high accuracy and coverage for an attack.

Active attacks in which the adversary registers a number of fake users (sybils) with the social network, allows for creating unique structural patterns that can be used used to re-identify the sybil nodes and other users after anonymisation. Studies showed that adding a small amount of noise to the published graph sufficed to mitigate such active attacks, but new robust active attacks merely see that as an optimisation problem for which various heuristics can be used.

### Threading

Graph matching can also start with threading. The threading method can be used for correlating sequential releases that are then matched. This works best in dynamic social networks that grow fast. In later research it was noted this can be used to detect users with multiple accounts (sybils).

