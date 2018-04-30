Logistic Regression

### Logistic Regression、LASSO Regression(L1 norm)和Ridge Regression(L2 norm)三种回归的探讨

L1常用于特征选择feature selection，当样本集含有大量变量（也即特征值、维度），甚至变量数比样本数还要多的时候，比如1000个变量时，我们如何能从中判定出对我们有用的变量

L2常用于消除过拟合overfitting

L1正则化是指权值向量w中各个元素的绝对值之和，通常表示为||w|| 1   

L2正则化是指权值向量w中各个元素的平方和然后再求平方根（可以看到Ridge回归的L2正则化项有平方符号），通常表示为||w|| 2

L1正则化和L2正则化可以看做是损失函数的惩罚项。所谓『惩罚』是指对损失函数中的某些参数做一些限制。

scikit-learn中使用的方法就是在logisticRegression函数里加一个penalty惩罚项，指定是l1或者l2。加上以后logistic regression就有了这个功能：

from sklearn import linear_model

clf = linear_model.LogisticRegression(C=1.0, penalty='l1', tol=1e-6)

clf.fit(X, y)

反正就是避免model过于复杂，要么就是引入了太多没必要的变量，要么就是对已有的变量引入了太多太复杂的高阶项（其实都可以删掉）。加上penalty之后，在模型想要引入更多变量或更复杂的高阶项时、也会有一定的惩罚，从而实现“中和”。

我们知道，L1和L2都是规则化的方式，我们将权值参数以L1或者L2的方式放到代价函数里面去。然后模型就会尝试去最小化这些权值参数。而这个最小化就像一个下坡的过程，L1和L2的差别就在于这个“坡”不同，如下图：L1就是按绝对值函数的“坡”下降的，而L2是按二次函数的“坡”下降。所以实际上在0附近，L1的下降速度比L2的下降速度要快。所以会非常快得降到0。所以L1构建模型会更快效率更高，L2则能消除过拟合：

 <img src="l1_norm_lasso_l2_norm_ridge.jpg" width="100%" height="100%" alt="l1_norm_lasso_l2_norm_ridge"/><br />

什么叫过拟合？按照Andrew Ng的讲述，过拟合就是模型引入了太多不必要的四次方、五次方、六次方等特征项，如下：
 
如何防止过拟合？就是在定义loss损失函数（误差）的时候，给四次方、五次方、六次方这些项加上一个惩罚函数（penalty func），使得它们的参数尽可能趋向于0，消减它们对模型的影响，同时也使得我们的模型更加简单直观（没有了什么复杂的四次方、五次方、六次方）

 <img src="overfitting_AndrewNg.jpg" width="100%" height="100%" alt="overfitting_AndrewNg"/><br />