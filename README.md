# wine-clustering
wine clustering using KMeans and GMM

# Introduction
The data set is downloaded from Kaggle website, and it contains information about wine data. There are 13 features in this dataset, most of them are chemical constituents. All the features are continuous. This dataset is categorized into 3 clusters.

When running the K-Means algorithm, several parameters can be specified to fine-tune the performance of the algorithm. To ensure that the initial centroids are selected in an optimal way, the "k-means++" method was used, which is known to provide good initial centroids that are far apart from each other. This helps to avoid the algorithm stopping prematurely without reaching the optimal clustering solution. To prevent the algorithm from getting stuck in infinite loops due to an inability to find the optimal solution, a maximum number of iterations of 300 was set. Additionally, the algorithm was run multiple times, with different centroid seeds (Li 2013, p.3)., by setting n_init = 10. This approach allows to select the best result among the multiple iterations. Finally, the number of clusters was chosen after determining the optimum value through evaluating different metrics and using the elbow method.
For GMM model covariance type is selected as full to cluster any kind of datasets (with complex shapes and orientations), init_params is selected as kmeans, after trial and error, because the model is performing well in this parameter compared to ‘random’, it may indicate the clusters are more and more circular shape, but analysis of other performance metrics are needed to confirm this. Interestingly with this method the performance metrics values are changing each time when running the code, as the kmean is got run with different centroids each time when we run the code. n_init is set to 1 as increase of this value is esulting in poor value for Davies Boulden score, one reason could be the algorithm may stuck in local optimum point.

<p align="center">
  <img src="https://github.com/Plymouth-University/2023-comp5013-gp-neural_ninjas/blob/main/Picture_work_flow.png">
  <br />
  <em>Figure 3: Flow chart of the work </em>
</p>


Cluster analysis is an unsupervised learning method (Bellier, 2012) to optimize an objective function based on features similarities. It appears that the k-means and GMM clustering approaches perform similarly. Both have a Calinski-Harabasz index (Baarsch & Celebi, 2012) of around 340, indicating that the models have a good balance of compact clusters and high separation between clusters. Both have a silhouette (Shutaywi & Kachouie, 2021) score of around 0.56, which is relatively low and suggests that the clusters are not very well-separated or that the data points within each cluster are not very similar to one another. And Both have a Davies-Bouldin score around 0.6, indicating that the clusters are not well separated or that the means of the clusters are very similar to each other.
However, there are some key differences between the k-means and GMM clustering approaches. K-means is a centroid-based algorithm and assumes that the clusters have a spherical shape, and all clusters have the same variance and similar sizes. GMM, is a probability-based algorithm and the clusters are modelled as a mixture of Gaussian distributions. k-means algorithm is sensitive to the initialization of centroids while GMM is not sensitive to initialization of parameters.

<p align="center">
  <img src="https://github.com/Dharmendra04/wine-clustering/blob/main/Screenshot%202023-06-02%20at%2002.18.49.png">
  <br />
  <em>Figure 1: Flow chart of the work </em>
</p>


In general, these results suggest that neither k-means nor GMM are able to identify very distinct clusters in the data. It may be worthwhile to explore other clustering methods.
The main limitation or drawback of the k-means and GMM clustering approaches seems to be that they are not able to identify very distinct clusters in the data. The Calinski-Harabasz index, silhouette score, and Davies-Bouldin score are all relatively low, which suggests that the clusters are not very well-separated or that the data points within each cluster are not very similar to one another.
Some possible reasons for this include:

* The data may not be naturally separable into distinct clusters. The clusters may be overlapping or there may be a lot of noise in the data.

* The number of clusters used may not be the optimal number for the data. The k-means and GMM algorithms require the number of clusters to be specified in advance, and if this number is not chosen correctly, the resulting clusters may not be meaningful.

* Assumptions of k-means algorithm may not be satisfied. k-means assumes that the clusters are spherical and have similar variances, if these assumptions are not met, the results may not be accurate.

* For instance, if the underlying structure of the data is such that the clusters have different shapes or sizes or even overlapping clusters, K-Means algorithm might not be able to identify them accurately. This is because the algorithm tries to fit clusters into spheres with a unique centre point. When clusters have different shapes or sizes, or when clusters overlap, the algorithm may have difficulty finding well-defined clusters.

Therefore, the K-Means algorithm may be less capable of capturing the underlying structure of the data and in this case, the algorithm may overfit the data by trying to fit clusters that do not accurately represent the underlying structure of the data. This overfitting (Ying, 2019) can lead to poor generalization and poor performance on unseen data.

Another limitation of k-means is that the algorithm is sensitive to the initialization of centroids, this means that the final clusters obtained may be different with different starting points, this can be mitigated by running the algorithm multiple times and with different initial values.
Additionally, as both K-Means and GMM clustering are model-based, they may fail to accurately represent the underlying structure of the data if the chosen model does not match the true underlying structure.
To overcome these limitations, one can try using different clustering techniques or pre- processing the data in a way that makes it more amenable to clustering. For example, one could try using a density-based clustering algorithm or a hierarchical clustering algorithm that doesn't require the number of clusters to be specified in advance. One could also try applying dimensionality reduction techniques, such as PCA, to the data to reduce noise and make clusters more distinct.
