# Information-Retrieval-Project
TF-IDF and Clustering based models for retrieving documents given a query
Abstract:
Given a corpora of documents, we design two types of models. One based on Term Frequency and Inverse Document
Frequency. Another model based on clustering algorithms like K-means and Hierarchical Agglomerative clustering. Then we issue
queries to fetch the documents relevant to the queries using both the models. Finally accuracy comparison is done among
various models to evaluate their performance based on precision and recall values.
Dataset:
Initially we have dataset of that contains corpora of 6000+ documents. For the purpose of the project we select
randomly a set of 1000 documents from the actual set of documents. Then we have a set of queries and their true annotations
(relevant document IDs). We randomly select 10 queries (each query has around 50 documents that are relevant in the corpora)
that can be later imposed on the documents.
Work Flow:
The first step is to create an Inverted Index for the set of documents chosen. Next we sort the inverted index in
decreasing order so as to get the most frequently used words on top, which are usually stop words.
For a query say “aspirin helps prevent cancer”, to retrieve the documents for this query, our model for tokenizes the
query, then for each word retrieves the documents, based on the inverted index say aspirin is in (1 5 10), helps is in (5 10 20 30),
prevent is in (2 3 4) and cancer is in (1 10 11 12) documents. Finally we take union of all the documents and show them as
result.
To measure the accuracy of a model, we find precision and recall, values. Precision gives the fraction of relevant results
that are returned. Recall gives the fraction of relevant documents in the entire collection of documents were returned. To
improve these precision and recall values, we try to make few changes to the model that includes stemming and lemmatization.
Let this improved model be M1.
Why do we need another model? The current model although retrieves the documents for a query it does not order
them based on which document is the most relevant. So we introduce changes on top of the existing model, based on Term
Frequency (TF) and Inverse Document Frequency (IDF). In term frequency we assign a weight to each term for its total number
of occurrences. However the issue with plain term frequency is, all terms are given equal importance that is a term like “limit” is
present in almost every page of a book related to “calculus”. So to decrease this effect and give rare words more support, we
multiply raw term frequency with Inverse Document Frequency. This means rare terms get more weight than frequently
occurring terms. Let this model be M2. Now after we pose a query, we sort the results according to the TF-IDF scores and show
the most relevant documents on top.
We can clearly see the improvement that model M2 makes over model M1 in the figure below. Here the value “k”
implies the top k documents retrieved for the query. Here for comparing results we take the top 15 documents.
Machine Learning Based Models: Now we design retrieval models based on machine learning algorithms like K-Means
and Agglomerative clustering. The idea is that, each document or query is represented as a vector in an n-dimensional space
where each word represents one dimension. Now since we already have TF-IDF scores we represent each document as a vector
of TF-IDF scores. Now depending on the algorithm say K-Means with Euclidean distance. We cluster the entire document set
into k clusters. Now when a query is issued, the query is represented as a vector of TF-IDF scores. Then the distance between all
k-centroids and the query is calculated. The cluster with the highest score with all the documents is retrieved.
In the figures below we compare various models with the TF-IDF model.
How to select the number of clusters “k” depends on various factors. The goal is to minimize the intra cluster distance
and maximize the inter cluster distance. For this we can try the models with varying parameters and select the best model.
One approach would be to plot the accuracy values and select an optimal point in the graph which usually is the Elbow point.
After which we get diminishing returns. (Model Optimization).
References
 Introduction to information retrieval Book by Christopher D. Manning, Hinrich Schütze, and Prabhakar Raghavan
 https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html
