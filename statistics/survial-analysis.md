# survial analysis

## 基本概念

| 生存分析 | survival analysis | 分析时间的结果和出现这一结果经历的时间的一种统计方法 |
| :--- | :--- | :--- |
| 生存时间 | survival time | 起始时间与终止时间之间的时间间隔 |
| 生存率 | survival rate | 观察对象经过t个单位时间段后仍存活的可能性 |
| 生存函数 S\(t\) | survival function | t时刻存活的个数/开始观察个数 |
| 风险函数 | hazard function | 观察对象在t时刻瞬间死亡率/t时刻存活的人数 |
| 生存曲线 | survival curve | 以观察时间、生存率为x y轴 |
| 中位生存期 | median survival time | 半数生存期，50%的个体存活的时间 |

## 方法分类

| 参数法 | 已知分布，用模型预测生存率 |  |
| :--- | :--- | :--- |
| 非参数法 | 无需分布，用样本统计量预测生存率 | Kaplan-Meier法、寿命表法 |
| 半参数法 | 无需分布，用模型评估影响生存的因素 | COX回归模型 |

## 用途

| 估计 | Kaplan-Meier法、寿命表法 |
| :--- | :--- |
| 比较 | log-rank检验、Wilcoxon秩和检验 |
| 影响因素分析 | COX比例风险回归模型 |
| 预测 | COX回归模型预测生存率 |

