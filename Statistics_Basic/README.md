Statistics basic
 ### (0) A/B Testing

     先来了解t test和z test的区别：z-test：大样本；>30;符合z分布；t-test：小样本;<30;符合t分布。

     当总体分布是正态分布时，对任意样本量n，抽样均值分布均为正态分布。如果总体为非正态分布，仅在n值较大的情况下，样本均值分布近似为正态分布。（中心极限定理）

     认为样本均值近似的服从正态分布，当样本数量足够多时，样本方差和均值近似于总体均值和方差；或者，已知总体均值和方差，经过标准变换，认为其服从标准正态分布（z分布）（其实即使经过标准变换的值服从标准正态分布）。这就是z检验。

     仍假设样本均值近似的服从正态分布，总体标准差未知的情况且样本量较小（自由度较小）的情况下（什么叫大：趋向于无穷），用样本方差代替总体方差，认为经过标准正态变换的值不服从z分布，（差异来源：用样本方差代替总体方差）而是服从t分布。（服从分布不一样）这就是t检验。

     BMA-2笔记搜索A/B Testing后续计算过程都有，须知Control Group/Test Group。计算z值(x1 mean-x2 mean)/sqrt(x1 sd^2/n1+x2 sd^2/n2), 假定/alpha=0.01，一般我们用two tailed t test，如果z大于查表的结果则p-value<0.01，于是reject H_0接受H_1（前提先做hypothesis test，H_0是control group == test group, H_1是control group <> test group）。

     下述真实的A/B Testing案例来自https://blog.csdn.net/buracag_mc/article/details/74905483，Bayer医药网站客户转化率（新设计为test group，旧设计为control group）：

 <img src="ABTesting_1.jpg" width="100%" height="100%" alt="ABTesting_1"/><br />
 <img src="ABTesting_2.jpg" width="100%" height="100%" alt="ABTesting_2"/><br />
 <img src="ABTesting_3.jpg" width="100%" height="100%" alt="ABTesting_3"/><br />

     做A/B Testing的一些准则，来自http://baijiahao.baidu.com/s?id=1579982269379294051&wfr=spider&for=pc：

     a. 高Confidence level, 尽可能的让你的置信区间接近99%，最少也要95%，尽量减少得出错误结论的可能性（比如受短期波动影响）。

     b. 耐心、不要过早的下结论。开始进行测试后，首先要做的就是等待样本量到达预期量级，或者达到预定时限（半个月）。

     c. 将测试的时间拉长或进行持续性的测试——如果你并不相信当前测试结束后呈现的结果，并且希望排除掉所有潜在错误的可能性，那么我建议你将测试的时间周期拉长。这样就会有更大的样本容量，进而增加测试数据的统计意义。否则短期观测的结果很可能是来自波动影响。

     d. 要么有足够大的样本量，你可以基于足够大的样本量进行测试，那你获得的测试结果会更具统计意义。不断测试，持续思考和学习。

 ### (1) Hypothesis test, always used to evaluate the coefficients and their p-values, significance test, the relation of X with Y is statistically significant or not

     to evaluate if beta_1 is statistically significantly different from zero,

     H_0: beta_1 == 0

     H_1: beta_1 != 0

     t-test, student test, t distribution

     p-value < 0.05 (significance statistically), reject H_0 accept H_1, or else ...

     计算实例可参考ML courseNotes.pdf P168+169+171+172

     计算实例也可参考ML homework_02.ipynb Question 4 计算t star, t critical，如果t star > t crit那么reject H_0

     公式记忆t star = b1 / s{b1}, t cric = t_distribution(0.025, n-2) n是training data count

     公式记忆b1是model.summary()出来的coefficient，s{b1}是coefficient跟前的std error

     公式记忆也有一种算法是b1是sample mean，s{b1}是std(sample) / sqrt(n) n是training data count

 ### (2) Confidence Interval (CI) Estimation

     针对mean Y，在给定X下，有百分之多少的confidence知道mean Y的范围

     计算实例可参考ML courseNotes.pdf P168+169+171+172, 188

     计算实例也可参考ML homework_02.ipynb Question 4 计算t star, t critical，如果t star > t crit那么reject H_0

 ### (3) Prediction Interval (PI) Estimation

     针对observation Y（即真实的Y value)，在给定X下，有百分之多少的confidence知道actual Y的范围

     计算实例可参考ML courseNotes.pdf P200

 ### (4) Analysis of Variance approach, ANOVA table

     SLR ANOVA table, 1 predictor, P228, remember: for df, SSR = 1, SSE = n-2, SSTO = n-1

     MLR ANOVA table, p-1 predictors, P306, remember: p is count of predictors, for df, SSR = p-1, SSE = n-p, SSTO = n-1

     MLR Type I ANOVA table, P332

     MLR Type II ANOVA table, P334, 两者区别对比看下图一看便知, 两张图在Python里如何生成P335+336

 ### (5) R-squared = SSR/SSTO = 1 - SSE/SSTO, 0到1之间，越接近1越好, P218, P219

     Higher R-squared does not imply that the estimated regression line is a good fit.
     Higher R-squared does not imply that X and Y are not related.

     WHY involves Adjusted R-squared? P309-313, 1-SSE/SSTO变成SSE除以自己的df n-p和SSTO除以自己的df n-1

 ### (6) SSTO, SSR, SSE, MSR, MSE, related with Confidence Bands P204

     Total Sum of Squares, SSTO, Yi - mean Y, dof n-1, ML courseNotes.pdf P207

     Error/Residual Sum of Squares, SSE, Yi - estimated Y, dof n-2, ML courseNotes.pdf P208

     Regression Sum of Squares, SSR, estimated Y - mean Y, dof 1, ML courseNotes.pdf P209

     三者关系P212, Total Deviation = Deviation of fitted regression value around mean + Deviation of unfitted regression value around mean

     For SLR: MSR = SSR / 1, MSE = SSE / (n-2); for MLR: MSR = SSR / (p-1), MSE = SSE / (n-p), p is count of predictors.

     P330: in MLR, SSR(X1, X2, ..., Xp-1) != SSR(X1) + SSR(X2) + ... + SSR(Xp-1), it is...

 ### (7) Diagnostics for Residuals, an evaluation of residuals

     Heteroskedasticity，异方差性，给定解释变量，误差项的方差不为常数。与我们做OLS时的基本假设相悖。
     Homoskedasticity，  同方差性，回归模型中的误差在解释变量条件下具有不变的方差。 

     Residual Plot, plot the residuals against the predictor variable X, hope to see a random distribution rather than following any pattern of residuals for all values of X, P239. If we see constant error variance from Residual Plot then we establish Homoskedasticity.

     What is the principle of BF-test for checking Homoskedasticity? P243

     What is the hypothesis test of BF-test for checking Homoskedasticity? P245

     median or mean? P246, 选择比较两组的median group residual or mean group residual，然后get conclusion

     What is the hypothesis test of Shapiro-Wilk Test for checking Normal Distribution of Residuals? P260 符合的话说明好。

     What is QQ Plots for checking Normal Distribution of Residuals? P261+262 点尽可能全部落在线上说明好。

 ### (8) Remedial measures, 当我们发现线性没法fit的时候，尝试做transformation of X或Y

     P267+270, 如果plot发现X和Y不是linear关系，一般先尝试transform X，取log_10(X), X^2, 1/X, sqrt(X), 或者对Y作类似的尝试然后比效果

     P271, 如果plot发现X和Y的确是linear关系而residual却是Heteroskedasticity的，那么说明X和Y需要同时transform

     Box-Cox Transformation，不断算SSE然后比出来一个most optimized pow for Y, then we use that for Y's pow transformation

 ### (9) Coefficient of Partial Determination, P345, R^2Y1|2 = (SSE(X2) - SSE(X1|X2)) / SSE(X2)

 ### (10) Multicollinearity, say one predictor is correlated with another

     坏处：会potentially causing many of the estimated regression coefficients not to be statistically significant. P358, 此时addiing new predictors into model对SSE的decrease effect会不significant

     用专业点的话说，P363, When adding one explanatory variable that is highly correlated with an explanatory variable already in the model, the marginal contribution of the additional variable in reducing SSE is often comparatively small. 

 ### (11) AIC BIC SBC：

 赤池信息准则AIC

 贝叶斯信息指数BIC

 Link： http://sofasofa.io/forum_main_post.php?postid=1000201, smaller is better

 ### (12) Confusion matrix, Precision/Recall, ROC/AUC

参考链接：http://blog.csdn.net/lichao_ustc/article/details/52702964

应用实例参见kNN下KNN_on_Class_Apr102018.ipynb

 <img src="confusion_matrix.jpg" width="100%" height="100%" alt="Confusion Matrix"/><br />
 <img src="confusion_matrix_2.jpg" width="100%" height="100%" alt="Confusion Matrix"/><br />

precision = tp / (tp + fp)

recall = tp / (tp + fn)

Wikipedia有关recall和precision的解释：https://en.wikipedia.org/wiki/Precision_and_recall

    1. 正确率 = 提取出的正确信息条数 /  提取出的信息条数     

    2. 召回率 = 提取出的正确信息条数 /  样本中的信息条数    

两者取值在0和1之间，数值越接近1，查准率或查全率就越高。

F1 score, how well do I specifically perform on only malignant cancer prediction? 就是我只关注我在恶性肿瘤上的预测准确率有多高，而不是关注我在所有肿瘤类型恶性+良性一共的准确率有多高（因为你想啊，如果本身有90%的患者都是良性肿瘤，只有10%的患者是恶性肿瘤，那就算我的model再傻逼，我预测全部患者都是良性肿瘤，那我的准确率还有90%呢，但其实这没任何意义）

F1 score = (2*precision*recall) / (precision + recall)

参见百度百科对ROC和AUC的解释：https://baike.baidu.com/item/ROC%E6%9B%B2%E7%BA%BF/775606?fr=aladdin

选择最佳的诊断界限值。ROC曲线越靠近左上角,试验的准确性就越高。最靠近左上角的ROC曲线的点是错误最少的最好阈值，其假阳性和假阴性的总数最少。

最靠近左上角的ROC曲线所代表的受试者工作最准确。哪一种试验的 AUC最大，则哪一种试验的诊断价值最佳。