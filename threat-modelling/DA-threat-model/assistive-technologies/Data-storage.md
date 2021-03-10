# Data storage

The type of storage (NoSQL database, standard SQL database, or some kind of object storage), depends on the type of data (user input or behavioural) and on factors such as ease of implementation, the amount of data that the storage can manage, integration with the rest of the environment, and portability.

Online frameworks such as Apache Hadoop (a software framework for distributed storage and processing of big data using the MapReduce programming model) and Apache Spark (a unified analytics engine for big data processing, with built-in modules for streaming, SQL, machine learning and graph processing) allow for storing data in multiple devices to reduce dependability on one machine. Hadoop uses HDFS to split files into large blocks for distribution across nodes in a cluster. The dataset can be processed faster and more efficiently than it would be in an architecture that relies on a parallel file system.

_Spark has been found to run 100 times faster in-memory, and 10 times faster on disk. It’s also been used to sort 100 TB of data 3 times faster than Hadoop MapReduce on one-tenth of the machines. Spark has particularly been found to be faster on machine learning applications, such as Naive Bayes and k-means. _


