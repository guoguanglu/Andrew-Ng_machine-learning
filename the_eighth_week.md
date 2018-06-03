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
	* Multiclass classification  
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
![](/picture/the_eighth_week/k_mean2.png)  
Sometimes, you're running K-means to get clusters to use for some later/downstream purpose.  

***  
Motivation  
---  
### Motivation I: data compression  

### Motivation II: visualization  

### Multiclass classification  

***  
Principal component analysis  
---  
### principal component analysis problem formulation  

### principal component analysis algorithm  

***  
Applying PCA  
---  
### Reconstruction from compressed representation  

### Choosing the number of principal components  

### Advice for applying PCA  


***  
Reference  
----  
https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"
