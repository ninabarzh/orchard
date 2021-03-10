# Recommendation engines

Recommendation engines are a marketer tool especially for e-commerce/online businesses and is used to increase turn around (sales, profits). A typical recommendation engine processes data through collection, storing, analysing and filtering.

Several marketers and advertisers are using de-anonymised content to match and recommend products, services and people to users on the basis of user profile feature matching and behavioural analysis. For example, LinkedIn applies this approach for its ‘People You May Know’ feature and Amazon applies it to suggest related products to purchase. 

## Types of recommendation engines
There are three important types of recommendation engines, collaborative filtering, content-based filtering and hybrid recommendation systems.

### Collaborative filtering

Collaborative filtering is based on collecting and analysing information on behaviours, activities or preferences and predicting what a user will like based on the similarity with other users. It does not rely on machine analysable content and is capable of accurately recommending complex items without requiring an “understanding” of the item itself. The assumption is that people who agreed in the past will agree in the future, and will like similar kinds of items as they liked in the past.

* User-user collaborative filtering searches for lookalike customers and offer products based on what his/her lookalike has chosen. The algorithm is effective but takes a lot of time and resources because it requires computing every customer pair information which takes time.
* Item-item collaborative filtering is similar to user-user collaborative filtering, but instead of finding a customer look alike, an item look alike is used. From an item look alike matrix, alike items are recommended to a customer who has purchased any item from the store. This algorithm requires fewer resources because similarity scores between customers are not needed. This is the approach used by Amazon.
* Other simpler algorithms like market basket analysis, generally do not have the high predictive power that user-user collaborative filtering and item-item collaborative filtering have.

### Content-based filtering

In content-based filtering, the algorithms try to recommend products which are similar to the ones that a user has liked in the past. It has its roots in information retrieval and information filtering research. Keywords are used to describe the items and a user profile is built to determine the type of item a user likes. The idea behind content-based filtering is that if you like an item you will also like a “similar” item. The system is able to learn user preferences from users actions about one content source and replicates them across other different content types.

### Hybrid recommendation systems

Combining content-based and collaborative-based predictions, or adding content-based capabilities to a collaborative-based approach and vice versa or unifying the approaches into one model can be highly effective. It can be used to overcome common problems in recommendation systems such as cold start and the data paucity problem. Netflix uses hybrid recommender systems in which it compares the watching and searching habits of similar users (collaborative filtering) and offers movies that share characteristics with films that a user has rated highly (content-based filtering).

## DIY

Any organisation can develop its own recommendation engine architecture using open source tools.

## Future

Deep learning, social learning, and tensor factorisation are based on machine learning and neural networks. Such cognitive computing methods are likely to develop next.

