# Sparsity-based

Sparse data share few relationships, but the activity stream of the target within anonymised sets of streams can be gathered from other users. Activity relationship mining consists of rules that link various aspects of two captured activity types and can help decide if two activities were probably achieved by the same individual or not. Existing sparsity-based techniques have been adapted to exploit mobile sensor data characteristics, indicating significant threats to user anonymity within shared mobile sensor data.

Several studies looked at the advantages of sparsity for de-anonymisation. De-anonymisation could improve due to database sparsity and if the auxiliary information consists of values matching with rare attributes of a target database, then the de-anonymisation achieved is greater. It is not the sparsity, but in what way it is sparse that provides information.

In 2017, the social network de-anonymisation problem was converted into a binary classification problem between node pairs ([De-anonymizing Social Networks with Random Forest Classifier, Jiangtao Ma, Yaqiong Qiao, Guangwu Hu, Yongzhong Huang, 2017](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8051053)). Using the spectral partition method, large sparse social networks were partitioned into a number of small sub graphs. The features of the network structure were used to train the random forest classifier. As a result, candidate node pairs from anonymous network and auxiliary network can be classified as matched pair by the random forest classifier.

