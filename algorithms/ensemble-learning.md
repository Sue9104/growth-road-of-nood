# Ensemble Learning

视频学习参考：https://www.youtube.com/watch?v=tH9FH1DH5n0

|  | Bagging | Boost |
| :--- | :--- | :--- |
| 训练样本 | 有放回的抽样（bootstrap） | 上一次分类错误样本提高权重 |
| 模型权重 | 相等 | 分类误差小的分类器有更大的权重 |
| 并行 | 每个分类器是独立的，可并行 | 每个弱分类器严格依赖上一步的分类器，不可并行 |

## 常见的分类算法

| RandomForest | Bagging + DecisionTree |
| :--- | :--- |
| BoostingTree | AdaBoost + DecisionTree |
| GBDT | GradientBoost + DecisionTree |



