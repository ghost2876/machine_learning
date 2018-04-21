周五：kNN，k-means，logistic regression，LASSO/Ridge
周六：linear regression，SVM (ML Lab 3)
周日：bagging，boosting，Adaboost，GBDT，XGBoost，DL (working on traverse USFederalAgencies) (回Sanket邮件准备KT list)
周一：big data processing


都是二叉树还是不是？
Decision Tree,
1. smaller gini, more pure

   smaller entropy, more pure, more information gain

   information gain, entropy 信息增益代表信息不确定性(不纯)的减少程度, use which feature as the current classifier that most decreases the system's entropy, we use that feature as the classifier for the current step

2. ID3, CART, C4.5
   ID3 - information gain (entropy)
   C4.5 - gain ratio (information gain / splitinfo)
   CART - gini index

   C4.5克服了ID3的2个缺点：
   (1) 用信息增益选择属性时偏向于选择分枝比较多的属性值，即取值多的属性，比如用ID作classifier，这肯定可以分特别pure，但明显不合理
       参见公式http://www.cnblogs.com/zhangchaoyang/articles/2842490.html
   (2) 不能处理连续属性Numeric value（这个没有研究）

3. Formula for calculation of gini index, information gain (entropy) and gain ratio
   Information gain (entropy): http://www.saedsayad.com/decision_tree.htm
   Gini: http://www.learnbymarketing.com/481/decision-tree-flavors-gini-info-gain/
   Gain ratio: BMA-2笔记

4. pruning
   Prepruning
   Postpruning
   

5. evaluation
   overfitting