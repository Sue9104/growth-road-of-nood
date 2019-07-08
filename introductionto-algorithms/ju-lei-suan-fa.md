# 聚类算法
无监督的学习 
知乎：https://www.zhihu.com/question/34554321

![](/assets/v2-e6253fb2f5823c564426af0aa970a8b4_r.jpg)


英文： https://towardsdatascience.com/the-5-clustering-algorithms-data-scientists-need-to-know-a36d136ef68
中文：https://www.jiqizhixin.com/articles/the-6-clustering-algorithms-data-scientists-need-to-know

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

## 基于密度的聚类方法（DBSCAN）
![](/assets/640.jpeg)
### 步骤
1. DBSCAN 从一个没有被访问过的任意起始数据点开始。这个点的邻域是用距离 ε（ε 距离内的所有点都是邻域点）提取的。

2. 如果在这个邻域内有足够数量的点（根据 minPoints），则聚类过程开始，并且当前数据点成为新簇的第一个点。否则，该点将会被标记为噪声（稍后这个噪声点可能仍会成为聚类的一部分）。在这两种情况下，该点都被标记为「已访问」。

3. 对于新簇中的第一个点，其 ε 距离邻域内的点也成为该簇的一部分。这个使所有 ε 邻域内的点都属于同一个簇的过程将对所有刚刚添加到簇中的新点进行重复。

4. 重复步骤 2 和 3，直到簇中所有的点都被确定，即簇的 ε 邻域内的所有点都被访问和标记过。

5. 一旦我们完成了当前的簇，一个新的未访问点将被检索和处理，导致发现另一个簇或噪声。重复这个过程直到所有的点被标记为已访问。由于所有点都已经被访问，所以每个点都属于某个簇或噪声。

### 优点
1. 不需要固定数量的簇
2. 将异常值识别为噪声，能找到任意大小和任意形状的簇
### 缺点
1. 簇的密度不同，表现很差，特别是在高维度数据中