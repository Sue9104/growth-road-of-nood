#分类算法
## 指标
- 准确率Accuracy （分类器正确分类的样本数与总样本数之比）
- 精确率 （在被识别为正类别的样本中，确实为正类别的比例）

 $$Precision = TP / (TP + FP)$$
 
- 召回率  （在所有正类别样本中，被正确识别为正类别的比例）

 $$ ReCall = TP / (TP+FN) $$

- 灵敏度（sensitive） 所有正例中被分对的比例
 $$ sensitive = TP/P $$

- 特效度（sensitive） 所有负例中被分对的比例
 $$ specificity = TN/N $$

- ROC曲线 （以伪阳率FPR为X,真阳率TPR为Y）
 - 真实为阳性的样本中，被**正确的**判定为阳性的比例
 $$FPR = TP / (TP + FN)$$
 - 真实为阴性的样本中，被**错误的**判定为阳性的比例
 $$FPR = TP / (TP + FN)$$

![](/assets/1024px-ROC_space-2.png)
