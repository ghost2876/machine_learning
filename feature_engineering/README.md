feature engineering常见的手法包括：

One-hot encoding

数据中心化standardization、标准化data scaling, like for kNN this is really important cuz kNN is sensitive to distance scaler.

missing values缺失值处理(scikit-learn的mean或者kNN填补)

sample inbalance处理

【解决样本不均衡的办法】
方案一：设定不同的正负样本权重（惩罚函数loss）
方案二：重复正样本若干次（上采样）
方案三：把所有的负样本分成n份、将正样本分别和n份负样本构建n个模型、n个模型去投票

可以在scikit-learn里用Random Forest或者XGBoost来衡量importance of each feature，从而知道其scores选取最重要的那些个features