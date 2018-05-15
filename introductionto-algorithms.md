# 聚类算法
无监督的学习 
知乎：https://www.zhihu.com/question/34554321

![](/assets/v2-e6253fb2f5823c564426af0aa970a8b4_r.jpg)


参考： https://towardsdatascience.com/the-5-clustering-algorithms-data-scientists-need-to-know-a36d136ef68

## K-Means Clustering
### 步骤
1. Select a number of classes/groups to use and randomly initialize their respective center points
2. Classified by computing the distance between that point and each group center, and then classifying the point to be in the group whose center is closest to it
3. Recompute the group center by taking the mean of all the vectors in the group
4. Repeat these steps for a set number of iterations or until the group centers don’t change much between iterations

![](/assets/1_KrcZK0xYgTa4qFrVr0fO2w.gif)

### 优势
 Pretty fast, linear complexity O(n)
 
### 缺点
1. Have to select how many groups/classes there are
2. May not be repeatable and lack consistency(starts with random select)
