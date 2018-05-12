k-Means

一种聚类Clustering算法，Unsupervised无监督的（不像kNN那样需要用到训练数据的label）。We are trying to minimize the sum of distances from each observation point to its cluster's centroid so that every cluster will be highest closely tighted.

一些关键词，centroids, observations, minimize SSE Sum of Squares, WSS Within-Cluster Sum of Squares, 要使用k-means续符合两个prerequisites, within-cluster variation is minimized

Algorithm: choose randomly on k centroids, k clusters, assign every observation to its centroid/cluster, until convergence which means no more observations switch over between clusters. 初始centroid的coordinates值往往可以取某个cluster里所有observation points的X,Y坐标的各自均值。

Sikit-learn: KMeans(n_clusters=4), .fit(), .predict(), 使用kmeans.inertia_可以看到这种情况下的最终收敛的Within-Cluster Sum of Squares (WSS).

Problem: k-means有个趋势，k越大（越接近于observations数），WSS越小（因为此时没有observations都会是自己的centroids，但这明显是不合理的），如何避免？使用Elbow method（肘部法则），让k用GridSearchCV逐步增大、然后画出每个k对应的Within-Cluster Sum of Squares、看k是多少的时候、WSS的减少率开始变小、即再增大k、对WSS减小的贡献已经很少了、就选哪个k最合理。

使用k-means的potential issues: