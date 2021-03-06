# The eighth week——Andrew-Ng Machine Learning Notes  
This is my note on Andrew-Ng's machining learning about the eighth week contents. Thank you for asking questions.

***
[![](/picture/the_first_week/fig_ML.jpg)][Andrew-Ng-coursera]  
- Author: Guo Guanglu  
- E-mail: 2360889142@qq.com
- QQ: 2360889142  

*** 
[**BACK README**](README.md)  

## Content  
* [Clustering](#clustering)
	* K-means algorithm  
	* Optimization objective  
  	* Random initialization  
  	* Choosing the number of clusters  
* [Motivation](#motivation)  
	* Motivation I: data compression  
	* Motivation II: visualization    
* [Principal component analysis](#principal-component-analysis)  
	* principal component analysis problem formulation  
	* principal component analysis algorithm  
* [Applying PCA](#applying-pca)
	* Reconstruction from compressed  
	* Choosing the number of principal components  
	* Advice for applying PCA  
* [Reference](#reference)  

***  
Clustering  
----  
### K-means algorithm  
**K-means algorithm**  
Input:  
* K(number of clusters)  
* Training set {x^(1), x^(2),..., x^(m)}(unlabel dataset)  
Note: x^(i) in R^(n)(drop x_0 = 1 convention)  

Algorithm:
```
1. Randomly initialize K cluster centroids mu_1,mu_2,...,mu_K in R^(n)  
2. Repeat{  
(1)	for i =1 to m  
		c^(i):= index(from 1 to K) of cluster centroid closest to x^(i)  
(2)	for k =1 to K   
		mu_k:= average(mean) of points assigned to cluster k  
```  
Note:  
(1) The step is called cluster assignment step. The dataset is divided and assigned to corresponding cluster set.  
c^(i) := min_k||x^(i) - mu_k||^2  
(2) The step is called moving cluster step. According to the new cluster datasets, we can get new cluster centroids.  

### Optimization objective  
![](/picture/the_eighth_week/k_mean1.png)  
We can find the distance is just that the distance between examples and cluster centroids of cluster to which examples has been assigned.  
![](/picture/the_eighth_week/k_mean2.png)  
### Random initialization  
K-means random initializationn  
1. Should have k<m  
2. Randomly pick k training examples  
3. Set mu_1, mu_2,...mu_k equal to these k examples.  

To avoid stucking in a local minimize, we can randomly initialize and run many times(50-1000times)  
```
For i=1 to 100{
	Randomly initialize k-means  
	Run k-means. Get c^(1), c^(2),..., c^(m), mu_1,...,mu_k  
	compute the cost function (distortion)  J(c^(1),...,c^(m),mu_1,...,mu_k)  
Pick clustering that give lowest cost J
```
Note : when k = 2-10, The method of  runnning many times can make a huge difference.   
### Choosing the number of clusters  
![](/picture/the_eighth_week/k_mean3.png)  
Sometimes, you're running K-means to get clusters to use for some later/downstream purpose.  

***  
Motivation  
---  
### Motivation I: data compression  
![](/picture/the_eighth_week/data_compression.png)  

### Motivation II: visualization  
We need to visulaize our dataset. However there are many features, then we can choose two or three main feature to visualize them.  

***  
Principal component analysis  
---  
### principal component analysis problem formulation  
PCA problem formulation  
Reduce from n-dimension to k-dimension: Find k vectors u^(1), u^(2),...,u^(k) onto which to project the data, so as to **minimize the projection error**.  
PCA is not linear regression. PCA computes the minimize projection error(that is distance between point to line). However linear regression computes the vertical distance between point and line. They are different.  
![](/picture/the_eighth_week/pca1.png)  

### principal component analysis algorithm  
![](/picture/the_eighth_week/pca2.png)  
***  
Applying PCA  
---  
### Reconstruction from compressed representation  
We can map low-dimension  back to high-dimension.  
```
Z = U_reduce^T \* x  
x_approx = U_reduce * Z
```  
### Choosing the number of principal components  
choosing k(called number of principal components)  
**one method**:  
Average squared projection error:   
![](/picture/the_eighth_week/pca3.png)  
Total variation in the data:   
![](/picture/the_eighth_week/pca4.png)   
Typically, choose k to be smallest value so that   
![](/picture/the_eighth_week/pca5.png)   
'99%' of variance is retained.   
'95%' and '99%' are  common range of values that people use.  
**two method**:  
[U, S, V] = svd(Sigma)  
Pick smallest value of k for which  
![](/picture/the_eighth_week/pca6.png)  

### Advice for applying PCA  
Sometimes PCA can speed up a learning algorithm.  
**supervised learning speedup**:  
```
train set : {(x^(1), y^(1)), ..., (x^(m), y^(m))}  
extract input: x^(i) map to z^(i) by PCA  ,where x in 10000-dimension, z in 1000-dimension  
we can get new train set : {(z^(1), y^(1)), ..., (z^(m), y^(m))}  
```
Note:  
Running PCA only on the training set. Then the mapping can be applied as well to the cv set or test set.  
**Application of PCA**:  
1. Compression  
	* Reduce memory/disk needed to store data  
	* Speed up learning algorithm  
2. Visulization  

**Bad application of PCA**: To prevent overfitting problem. you can use regularization.

***  
Reference  
----  
https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"
