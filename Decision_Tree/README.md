Decision Tree,

### 0. 为什么单棵decision tree有时候performance不好？

因为它本身recursive splitting的时候、每一步splitting基于的就是greedy、本身就是“当时”的最优解、但可能不是globally optimistic answer全局最优解。

### 1. smaller gini, more pure

   smaller entropy, more pure, more information gain

   information gain, entropy 信息增益代表信息不确定性(不纯)的减少程度, use which feature as the current classifier that most decreases the system's entropy, we use that feature as the classifier for the current step

### 2. ID3, CART, C4.5
   ID3 - information gain (entropy) - 可能生成的不是binary tree
   C4.5 - gain ratio (information gain / splitinfo) - 可能生成的不是binary tree
   CART - gini index - 生成的肯定是binary tree，怎么保证？1, {rest}, Link: https://www.cnblogs.com/yonghao/p/5135386.html compare gini and decide

   C4.5克服了ID3的2个缺点：
   (1) overfitting, 用信息增益选择属性时偏向于选择分枝比较多的属性值，即取值多的属性，比如用ID作classifier，这肯定可以分特别pure，但明显不合理
       参见公式http://www.cnblogs.com/zhangchaoyang/articles/2842490.html
   (2) 不能处理连续属性Numeric value（no research）

### 3. Formula for calculation of gini index, information gain (entropy) and gain ratio
   Information gain (entropy): http://www.saedsayad.com/decision_tree.htm
   Gini: http://www.learnbymarketing.com/481/decision-tree-flavors-gini-info-gain/
   Gain ratio: BMA-2笔记

### 4. pruning
   Prepruning
   Postpruning
   	Cost-Complexity Pruning, Link: https://www.cnblogs.com/yonghao/p/5135386.html
   	Reduced error pruning
   Link： https://en.wikipedia.org/wiki/Pruning_(decision_trees)

### 5. scalable decision tree - (no research)
   two algorithms: Rain Forest雨林算法, Bootstrapped Optimistic Algorithm for Tree Construction (BOAT)树构造的自助乐观算法