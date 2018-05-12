Others

### Ordinary Least Squares (OLS), Gradient Descent, Maximum Likelihood Estimation (MLE)
 
 ML homework_02.ipynb Question 1

### supervised & unsupervised learning：

 BMA-2笔记搜索"监督"，difference: we know the response or not (do we have training data? Can we label that manually?)

 (1) supervised learning: Linear/Polynomial Regression, Logistic Regression (actually for classification), Decision Tree, Random Forest, SVM, kNN (uses training data's labels), Naive Bayes

 (2) unsupervised learning: k-means, Apriori, FP-Growth, PCA, SVD

### 解释一下Gradient Descent有哪些种类，大致有哪些区别？

Stochastic Gradient Descent, Batch Gradient Descent, Mini-batch Gradient Descent

批量梯度下降法（Batch Gradient Descent）是梯度下降法最常用的形式，具体做法也就是在更新参数时使用所有的样本来进行更新。

随机梯度下降法（Stochastic Gradient Descent）其实和批量梯度下降法原理类似，区别在与求梯度时没有用所有的m个样本的数据，而是仅仅选取一个样本j来求梯度。随机梯度下降法，和4.1的批量梯度下降法是两个极端，一个采用所有数据来梯度下降，一个用一个样本来梯度下降。自然各自的优缺点都非常突出。对于训练速度来说，随机梯度下降法由于每次仅仅采用一个样本来迭代，训练速度很快，而批量梯度下降法在样本量很大的时候，训练速度不能让人满意。对于准确度来说，随机梯度下降法用于仅仅用一个样本决定梯度方向，导致解很有可能不是最优。对于收敛速度来说，由于随机梯度下降法一次迭代一个样本，导致迭代方向变化很大，不能很快的收敛到局部最优解。那么，有没有一个中庸的办法能够结合两种方法的优点呢？有！这就是4.3的小批量梯度下降法。

小批量梯度下降法（Mini-batch Gradient Descent）是批量梯度下降法和随机梯度下降法的折衷，也就是对于m个样本，我们采用x个样子来迭代，1<x<m。一般可以取x=10，当然根据样本的数据，可以调整这个x的值。

### 到底什么叫梯度Gradient

先说梯度（Gradient）是什么？它其实是一个vector，就是向量，向量就是既包含值也包含方向的一个数学含义，那么这个梯度向量求出来有什么意义呢？它的意义从几何意义上讲，就是函数的值（loss function）变化增加最快的方向。沿着梯度我们就可以找到极值。

 步长（Learning rate） 假设函数（hypothesis function） 损失函数（loss function）

### Gradient Descent和Gradient Boost有啥区别？

在机器学习算法中，在最小化损失函数时，可以通过梯度下降法来一步步的迭代求解，得到最小化的损失函数，和模型参数值。反过来，如果我们需要求解损失函数的最大值，这时就需要用梯度上升法来迭代了。<br />
梯度下降法和梯度上升法是可以互相转化的。比如我们需要求解损失函数f(θ)的最小值，这时我们需要用梯度下降法来迭代求解。但是实际上，我们可以反过来求解损失函数 -f(θ)的最大值，这时梯度上升法就派上用场了。

### 如何调优梯度下降？

1. 算法的步长选择。在前面的算法描述中，我提到取步长为1，但是实际上取值取决于数据样本，可以多取一些值，从大到小，分别运行算法，看看迭代效果，如果损失函数在变小，说明取值有效，否则要增大步长。前面说了。步长太大，会导致迭代过快，甚至有可能错过最优解。步长太小，迭代速度太慢，很长时间算法都不能结束。所以算法的步长需要多次运行后才能得到一个较为优的值。<br />
2. 算法参数的初始值选择。 初始值不同，获得的最小值也有可能不同，因此梯度下降求得的只是局部最小值；当然如果损失函数是凸函数则一定是最优解。由于有局部最优解的风险，需要多次用不同初始值运行算法，关键损失函数的最小值，选择损失函数最小化的初值。<br />
3.归一化。由于样本不同特征的取值范围不一样，可能导致迭代很慢，为了减少特征取值的影响，可以对特征数据归一化。迭代次数可以大大加快。

### 梯度下降法和其他无约束优化算法比如OLS的比较

在机器学习中的无约束优化算法，除了梯度下降以外，还有前面提到的最小二乘法，此外还有牛顿法和拟牛顿法。

梯度下降法和最小二乘法相比，梯度下降法需要选择步长，而最小二乘法不需要。梯度下降法是迭代求解，最小二乘法是计算解析解。如果样本量不算很大，且存在解析解，最小二乘法比起梯度下降法要有优势，计算速度很快。但是如果样本量很大，用最小二乘法由于需要求一个超级大的逆矩阵，这时就很难或者很慢才能求解解析解了，使用迭代的梯度下降法比较有优势。