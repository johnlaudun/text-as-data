## 2-3 Topic Models & K-Means Elbows

Clustering is an unsupervised machine-learning technique. It is the process of division of the dataset into groups in which the members in the same group possess similarities in features. K-Means is one of the most common clustering techniques. It’s easily implemented and opens the door for you to explore other clustering techniques. We are going to use the K-Means clustering algorithm available in Sci-Kit Learn to plot a line in order to see where clustering drops off in efficiency and forms an elbow.

### Terms

Supervised versus unsupervised. 

K-Means works by finding the WCSS (Within-Cluster Sum of Square) for a centroid. It works by:

- selecting the number of clusters (K) for the dataset,
- selecting the centroids for each of the K clusters,
- using a distance (Euclidean or Manhattan) to calculate which points are nearest the centroid creating “clusters,”

WCSS (Within-Cluster Sum of Squares) is the sum of the squared distance between each point and the centroid in the cluster. As the number of clusters (K) increases, the WCSS decreases. Typically, there is a moment where further increases in K does not decrease the WCSS by much. That moment looks like an “elbow” on a graph. That moment or K is considered optimal. A more precise way of saying this is that the rate at which the variance of WCSS decreases levels off, sometimes sharply, at that K, suggesting an appropriate cluster count for analysis or model training. Put more simply, the elbow method is a graphical representation of K that allows us to discern an “optimal K.”

### Downsides

- Subjectivity: The choice of the “elbow point” can be subjective and might vary between individuals analyzing the same data.
- Non-Gaussian Data: It assumes that clusters are spherical and equally sized, which may not hold for complex datasets with irregularly shaped or differently sized clusters.
- Sensitivity to Initialization: K-means itself is sensitive to initial cluster centroids, which can affect the WCSS values and, consequently, the choice of the optimal K.
- Inefficient for Large Datasets: For large datasets, calculating WCSS for a range of K values can be computationally expensive and time-consuming.
- Unsuitable for All Distributions: The elbow method is not suitable for all data distributions, especially when clusters have varying densities or are non-convex.
- Limited to K-means: It specifically applies to K-means clustering and may not be suitable for other clustering algorithms with different objectives.



* K-Means Clustering in Python: A Practical Guide – Real Python](https://realpython.com/k-means-clustering-python/)
* [The Ultimate Guide to Clustering Algorithms and Topic Modeling | by Zijing Zhu, PhD | Towards Data Science](https://towardsdatascience.com/wthe-ultimate-guide-to-clustering-algorithms-and-topic-modeling-4f7757c115)
* [A Practical Guide on K-Means Clustering | by Dhruvil Karani | Towards Data Science](https://towardsdatascience.com/a-practical-guide-on-k-means-clustering-ca3bef3c853d)
* [In Depth: k-Means Clustering - Python DataScience Handbook (updated version)](https://marcelmaatkamp.github.io/PythonDataScienceHandbook/notebooks/05.11-K-Means/#k-means-algorithm-expectationmaximization)
* [2-5-data-clu… - JupyterLab](http://localhost:8888/lab/tree/Developer/text-as-data/notebooks/2-5-data-clustering.ipynb)

* [Elbow Method to Find the Optimal Number of Clusters in K-Means](https://www.analyticsvidhya.com/blog/2021/01/in-depth-intuition-of-k-means-clustering-algorithm-in-machine-learning/)
* [K-Means Clustering in Python: A Practical Guide – Real Python](https://realpython.com/k-means-clustering-python/)
* [USAJOBS - Job Announcement](https://www.usajobs.gov/job/778460800?share=linkedin)
* [Python's Requests Library (Guide) – Real Python](https://realpython.com/python-requests/?utm\_source=notification\_summary&utm\_medium=email&utm\_campaign=2024-03-05)
* [“Deep Learning is Rubbish” — Karl Friston & Yann LeCun Face Off at Davos 2024 World Economic Forum | by Denise Holt | 𝐀𝐈 𝐦𝐨𝐧𝐤𝐬.𝐢𝐨 | Jan, 2024 | Medium](https://medium.com/aimonks/deep-learning-is-rubbish-karl-friston-yann-lecun-face-off-at-davos-2024-world-economic-forum-494e82089d22)



### More reading

* [python - How do I get the components for LDA in scikit-learn? - Stack Overflow](https://stackoverflow.com/questions/13973096/how-do-i-get-the-components-for-lda-in-scikit-learn)
* [sklearn.decomposition.LatentDirichletAllocation — scikit-learn 1.4.1 documentation](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.LatentDirichletAllocation.html#sklearn.decomposition.LatentDirichletAllocation)
