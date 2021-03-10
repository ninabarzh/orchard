# Predictive analysis

Predictive analytics is the practice of extracting information from existing current and historical data sets in order to determine patterns and predict future outcomes and trends by statistical techniques from modelling, machine learning, and data mining. Predictive analytics does not tell you what will happen in the future.

# Method

* Understanding the problem
* Tying prediction variables to the problem
* Choosing statistical models relevant to the problem
* Preparing the input data for application of the models
* Validating the models with test data
* Apply real life data, observing accuracy over time and making adjustments

## Examples

### Clustering

Cluster analysis can be used when there are a lot of content nodes that are to be divided into different content clusters, and no idea how to create them. Rather than defining groups before looking at the data, clustering allows for finding and analysing groups that have formed “organically” (based on similarity). Applications for cluster analysis include gene sequence analysis, market research, and object recognition.

When choosing a clustering algorithm, consider whether the algorithm scales to the dataset. Not all clustering algorithms scale efficiently. Many clustering algorithms work by computing the similarity between all pairs of examples. This means runtime increases as the square of the number of examples.

* Centroid-based clustering organises the data into non-hierarchical clusters. K-means is the most widely-used centroid-based clustering algorithm. Centroid-based algorithms are efficient but sensitive to initial conditions and outliers.
* Connectivity-based (alias hierarchical) algorithms create a tree of clusters. An advantage is that any number of clusters can be chosen by cutting the tree at the right level.
* Density-based algorithms connect areas of high example density into clusters, allowing for arbitrary-shaped distributions. These algorithms have difficulty with data of varying densities and high dimensions. And by design, these algorithms do not assign outliers to clusters. With the OPTICS algorithm one can view intrinsic clustering structure that could otherwise be identified only in a process of repeated clustering with different parameter settings.
* Probabilistic (alias distribution-based) algorithms assume data is composed of distributions. As distance from the distribution's centre increases, the probability that a point belongs to the distribution decreases. Do not use if distribution is not known.
* Dimensionality reduction reduces the number of features under consideration, where each feature is a dimension that partly represents the objects. With too many features, the data matrices become sparse and analysis suffers from the curse of dimensionality (loss of statistical significance). Plus that it is easier to process smaller data sets. This is achieved by feature selection or feature extraction (combining existing features). The main technique used for feature extraction is Principle Component Analysis (PCA)
* Neural networks/Deep learning are a set of algorithms, modelled loosely after the human brain, that are designed to recognise patterns. They interpret sensory data through a kind of machine perception, labelling or clustering raw input. The patterns are numerical, contained in vectors, as translations of images, sound, text or time series.

Clustering algorithms can be used in [social graph analysis](../uses/Social-network-analysis.md).

### Classification

Classification models classify input data into categories. Typical applications include medical imaging, speech recognition, and credit scoring.

Classification is the process of finding a model (or function) that describes and distinguishes data classes or concepts, for the purpose of being able to use the model to predict the class of objects whose class label is unknown. The derived model is based on the analysis of a set of training data (data objects whose class label is known). The derived model can take the form of classification (IF-THEN) rules, decision trees, mathematical formulae, or neural networks.

* A decision tree is a flow-chart-like tree structure, where each node denotes a test on an attribute value, each branch represents an outcome of the test, and tree leaves represent classes or class distributions. Decision trees can easily be converted to classification rules.
* A neural network, when used for classification, is a collection of neuron-like processing units with weighted connections between the units.
* There are many other methods for constructing classification models, such as support vector machines, Naïve Bayesian Classification, and Nearest Neighbour Classification.

Classification algorithms can be for [customer retention](../uses/Customer-churn-analysis.md) or developing a [recommendation engine](../uses/Social-network-analysis.md).

### Regression

Regression analysis is a form of predictive modelling technique which investigates the relationship between a dependent (target) and independent variable(s) (predictor). This technique is used for forecasting, time series modelling and finding the causal effect relationship between the variables. Typical applications include electricity load forecasting and algorithmic trading.

Regression analysis:

* Indicates the significant relationships between dependent variable and independent variable.
* Indicates the strength of impact of multiple independent variables on a dependent variable.
* Can be used to compare the effects of variables measured on different scales.

Regression algorithms can be used for predicting the next outcome of time-driven events, for example in [network monitoring](../uses/Network-monitoring.md.md).



