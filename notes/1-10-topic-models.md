## 1-10 Topic Models

Before we explore topic models a bit more, it’s useful to revise the essentials of creating a document-term matrix.

When tokenizing, there are a number of ways to reduce complexity: lowercase tokens, remove punctuation, remove stop words, create equivalence classes (lemmatize/stem), and filter by frequency (words that are too common or too few). 

In moving immediately to topic models, we skipped past one of the early (and still) common data and text analytics which those of you who have had an introduction to statistical or machine learning will recognize as supervised learning. 

In **supervised learning** models are built on labeled examples and then evaluated on their to make correct predictions. For example, in our examination of Shakespeare’s corpus, we might train a model on most of the the plays, telling it which ones are tragedies, comedies, or histories. We then input a play the model has not seen before and ask it to determine the genre of the play, or, in some cases, the probability distribution over the genres: *Comedy of Errors* might be evaluated as a distribution of 20% tragedy, 50 percent comedy, and 30% history.

**Unsupervised learning** models do not rely on labeled data but on an assumption that patterns in the data are sufficiently strong that different *latent* classes within the observations will make themselves visible.

### If it’s a Matrix, It Can Be Factorized

Once you have your corpus transformed into a vector space, one of the most common things to do is to try to understand how the documents clump together by the words they have in common. In particular, we are looking for clusters of words they have in common, such that we can distinguish between the cluster *bank grass water side river* and *bank street money teller*. That is, words are allowed to occur in more than one cluster. 

Another name for cluster is *topic* and we tend to describe words within them as *co-occuring*. *Co-occurrence* stretches across an entire text, so words at the beginning and end of a document still co-occur. Collocation is usually defined by words being within a certain distance of each other, usually within a certain window, which is how most algorithms generate *n-grams*, by capturing a series of snapshots of a text as a window of *n* words. Such that the sentence “We don’t need no stinking badges” has 6 tokens (none repeating) and would generate the following n-grams:

```
5 x 2-grams: We don’t, don’t need, need no, no stinking, stinking badges. 

4 x 3-grams: We don’t need, don’t need no, need no stinking, no stinking badges
```

We will return to collocations in a moment, because they reflect how we assemble sentences and so they represent how words mean something in relationship to each other. 

Returning to the, er, topic at hand, we have our corpus broken into a document-term matrix in which the documents are in rows and the words are features of those documents, usually represented as the TF or as the TF-IDF. The idea behind topic models is that there are unseen topics which generate documents. You can imagine that someone writing about the retail banking industry already has certain words queued in their mind as they write. This makes a certain amount of sense based on what we know about how the brain works: when we activate certain ideas, ideas adjacent to them “light up” and are more readily called to mind than other words. This is why fresh metaphors or analogies can be so appealing and useful: those words are not in that ready activation zone and so they make our brains work to call them into our current mental working space.

All documents consist of a mixture of topics, some more *significant* than others—significant is important here because we are suggesting that these words are part of the signal the sender of the document is trying to communicate to us. Each topic consists of a collection of words. 

At the end of Unit 1, we derived a topic model from a small corpus of texts using Non-Negative Matrix Factorization (usually abbreviated as **NMF**). In my experience NMF works well with small corpora and enjoys the advantage of producing sparse representations, suggesting (usually correctly) that most documents do not contain a large number of topics. Essentially NMF takes our matrix and assumes it is a product of multiplying two underlying matrices, one of topics made up of words and the other of the documents made up of topics. NMF factors, or decomposes, our high-dimensional document-word matrix in order to arrive at the low-dimensional matrices. 

The SciKit-Learn implementation of NMF will ask you to determine the number of iterations you want: NMF iterates over the projected two underlying matrices, usually called ***W*** and ***H***, so that their product most closely approaches the original matrix. That is, the algorithm is going to compare its approximation against the known matrix, calculate the amount of error, and then approximate again to see if it’s higher or lower. It will return the two matrices that produced the lowest error. (Conventionally, the original matrix is called ***A***.)

### How Many Topics?

One step that arises in all topic models is determining the number of topics. There are a couple of options here, and they also reflect two different ways of thinking about, and using, topic models. (More on the latter in a moment.) 

The first option is to begin either with the number of topics that best fit the workflow or output or with some other external consideration: this is usually the case if you are working with materials and either have subject matter expertise or you are working with a subject matter expert. On the humanities side of text analytics, this sometimes involves guesstimating to start and then “tuning” the number of topics as you review the word clusters with reference to subject matter expertise. 

This latter way of working is not automatable and not objective, which makes sense: one would expect a subject matter expert to be *subjective*. Having a way to automatically select the best number of topics is preferred in those situations where you either do not have access to subject matter expertise, wish to explore the differences between automated and supervised processes, or if the workflow is going into a production environment. 

### The Kinds of Topics

When approaching texts mathematically, we are in some ways assuming that they are generated either using *probability* or using an *algorithm*.

In probabilistic models, which are the most common in statistics (and thus tend to dominate the data science side of text analytics), we assume a version of reality in which texts are generated by probabilities. That is, if text *i* contains these topics made up of those words in these proportions then text *i* is the probable outcome.

This is important enough to repeat: consider our initial data set of “The Most Dangerous Game” plus seven contemporaneous texts. If we were to attempt stylometric analyses in order to determine the rates of function words. We would then see if we could match that text which best matches the *author function* that is, in our model, Richard Connell. Imagined this way, author’s determine, albeit unconsciously, the rate at which function words are used. When we describe and analyze texts in this way, we are isolating the “author signal” from other signals, like topic. (You can imagine this as composite signal which we then use a Fourier transform to break apart.)

The appeal of probabilistic models is that they foreground their assumptions and thanks to the reliance on probability in statistics, there are a host of ways to optimize the model and quantify uncertainty.

The other way to approach texts mathematically is to specify a series of steps which solve the problem. The goal of creating an algorithmic model is to optimize our results (which often means minimizing errors). 

### The Algorithms Involved

- LDA
- NMF
- LSA

### LDA

## Clustering

### k-means

The ***k*-means clustering** method is an [unsupervised machine learning](https://en.wikipedia.org/wiki/Unsupervised_learning) technique used to identify clusters of data objects in a dataset. There are many different types of clustering methods, but *k*-means is one of the oldest and most approachable. These traits make implementing *k*-means clustering in Python reasonably straightforward, even for novice programmers and data scientists.

Clustering is a set of techniques used to partition data into groups, or clusters. **Clusters** are loosely defined as groups of data objects that are more similar to other objects in their cluster than they are to data objects in other clusters.

All clustering approaches have three components, whether they are specified explicitly or fixed implicitly: (1) an assumption (and notion) of document similarity and dissimilarity, (2) an objective function to measure the quality of the partition between dissimilar documents, and (3) a method for optimizing over the set of partitions. 

***k*-means** uses squared Euclidean distance to measure document dissimilarity. 





### More Reading

* [Topic Modelling using LDA and LSA in Sklearn | Kaggle](https://www.kaggle.com/code/rajmehra03/topic-modelling-using-lda-and-lsa-in-sklearn)
* [Topic Modeling with LSA, pLSA, LDA, NMF, BERTopic, Top2Vec: a Comparison | by Nicolo Cosimo Albanese | Towards Data Science](https://towardsdatascience.com/topic-modeling-with-lsa-plsa-lda-nmf-bertopic-top2vec-a-comparison-5e6ce4b1e4a5)
* [How Stuff Works: A Comprehensive Topic Modelling Guide with NMF, LSA, PLSA, LDA & lda2vec (Part-1) | by Sourav Bose | Medium](https://medium.com/@souravboss.bose/comprehensive-topic-modelling-with-nmf-lsa-plsa-lda-lda2vec-part-1-20002a8e03ae)
* [Topic Modeling Articles with NMF. Extracting topics is a good… | by Rob Salgado | Towards Data Science](https://towardsdatascience.com/topic-modeling-articles-with-nmf-8c6b2a227a45)
* [Evaluation of Topic Modeling: Topic Coherence | DataScience+](https://datascienceplus.com/evaluation-of-topic-modeling-topic-coherence/)
* [Text Clustering (TFIDF, PCA...) Beginner Tutorial | Kaggle](https://www.kaggle.com/code/albeffe/text-clustering-tfidf-pca-beginner-tutorial)

#### Iterative k-means

* [K-Means Clustering in Python: A Practical Guide – Real Python](https://realpython.com/k-means-clustering-python/)
* [The Ultimate Guide to Clustering Algorithms and Topic Modeling | by Zijing Zhu, PhD | Towards Data Science](https://towardsdatascience.com/wthe-ultimate-guide-to-clustering-algorithms-and-topic-modeling-4f7757c115)
* [A Practical Guide on K-Means Clustering | by Dhruvil Karani | Towards Data Science](https://towardsdatascience.com/a-practical-guide-on-k-means-clustering-ca3bef3c853d)
* [In Depth: k-Means Clustering - Python DataScience Handbook (updated version)](https://marcelmaatkamp.github.io/PythonDataScienceHandbook/notebooks/05.11-K-Means/#k-means-algorithm-expectationmaximization)
* [2-5-data-clu… - JupyterLab](http://localhost:8888/lab/tree/Developer/text-as-data/notebooks/2-5-data-clustering.ipynb)

