### 思路

对test data points，each of them找他们身边distance最近的k个点，看这些点的label，label多数的，算作这个test data points的label

k不能是偶数，一般从sqrt(n)开始，n是样本个数

### Advantage

Insensitive to outliers.

Easy to interpret with business.

### Disadvantage

Lazy algorithm, requires all training data to make predictions for each point of test data, i.e. requires a lot of memory

Computationally expensive and has large memory footprint

### 需要focus和pay attention的地方

Distance calculation is important, sometimes differences on a small scale appear to be closer even when they're not, 就是说distance的量纲scale非常重要、要统一所有features的量纲、features and distance Standardization and centralism.