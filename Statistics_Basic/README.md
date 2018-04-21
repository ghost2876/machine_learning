Statistics basic

 ### (1) Hypothesis test

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

 ### (2) Confidence Interval (CI)

     有针对mean的也有针对observation的

     计算实例可参考ML courseNotes.pdf P168+169+171+172

     计算实例也可参考ML homework_02.ipynb Question 4 计算t star, t critical，如果t star > t crit那么reject H_0
