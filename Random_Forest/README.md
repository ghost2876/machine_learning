Random Forest

BMA笔记中搜索“森林”

sqrt(M)

ensemble learning的一种

主要overcome单棵decision tree的overfitting问题

taking the majority vote in the case of classification trees

use random forest to evaluate the importance of features and select the most important features.
Random forest consists of a number of decision trees. Every node in the decision trees is a condition on a single feature, designed to split the dataset into two so that similar response values end up in the same set. The measure based on which the (locally) optimal condition is chosen is called impurity. For classification, it is typically either Gini impurity or information gain/entropy and for regression trees it is variance. Thus when training a tree, it can be computed how much each feature decreases the weighted impurity in a tree. For a forest, the impurity decrease from each feature can be averaged and the features are ranked according to this measure.

Link: http://blog.datadive.net/selecting-good-features-part-iii-random-forests/
	  https://blog.csdn.net/zjupeco/article/details/77371645 (finally normolization the importance)