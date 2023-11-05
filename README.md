# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## Aim:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm:
1.Choose the number of clusters (K): Decide how many clusters you want to identify in your data. This is a hyperparameter that you need to set in advance.

2.Initialize cluster centroids: Randomly select K data points from your dataset as the initial centroids of the clusters.

3.Assign data points to clusters: Calculate the distance between each data point and each centroid. Assign each data point to the cluster with the closest centroid. This step is typically done using Euclidean distance, but other distance metrics can also be used.

4.Update cluster centroids: Recalculate the centroid of each cluster by taking the mean of all the data points assigned to that cluster.

5.Repeat steps 3 and 4: Iterate steps 3 and 4 until convergence. Convergence occurs when the assignments of data points to clusters no longer change or change very minimally.

6.Evaluate the clustering results: Once convergence is reached, evaluate the quality of the clustering results. This can be done using various metrics such as the within-cluster sum of squares (WCSS), silhouette coefficient, or domain-specific evaluation criteria.

7.Select the best clustering solution: If the evaluation metrics allow for it, you can compare the results of multiple clustering runs with different K values and select the one that best suits your requirements

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Roghith k
RegisterNumber: 212222040135
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv('/content/Mall_Customers (1).csv')

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss=[]

for i in range (1,11):
  kmeans=KMeans(n_clusters=i,init="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km=KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

y_pred=km.predict(data.iloc[:,3:])
y_pred

data["cluster"]=y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:
### data.head():
![image](https://github.com/RoghithKrishnamoorthy/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119475474/5f0ba04a-ddb1-4de7-befa-9b42de53b8b1)

### data.info():
![image](https://github.com/RoghithKrishnamoorthy/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119475474/dcaa626d-2ad6-4007-9b82-0da1f8419221)

### Null Values:
![image](https://github.com/RoghithKrishnamoorthy/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119475474/ff836d91-adb8-460d-9829-5a1b1f800616)

### Elbow Graph:
![image](https://github.com/RoghithKrishnamoorthy/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119475474/2879aceb-86e8-460f-be75-7698b226ee12)

### K-Means Cluster Formation:
![image](https://github.com/RoghithKrishnamoorthy/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119475474/c4340d4d-fc0e-47e3-92c6-8765a81c53a4)

### Predicted Value:
![image](https://github.com/RoghithKrishnamoorthy/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119475474/cf496f0e-8cd7-483e-8076-32e9f4fc36fe)

### Final Graph:
![279570034-2198ffde-a8d9-4387-b1bb-ce48563fc9d4](https://github.com/RoghithKrishnamoorthy/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119475474/3b772d04-7eb7-4649-891c-bc3bf7349cf1)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
