# The ninth week——Andrew-Ng Machine Learning Notes  
This is my note on Andrew-Ng's machining learning about the ninth week contents. Thank you for asking questions.

***
[![](/picture/the_first_week/fig_ML.jpg)][Andrew-Ng-coursera]  
- Author: Guo Guanglu  
- E-mail: 2360889142@qq.com
- QQ: 2360889142  

*** 
[**BACK README**](README.md)  

## Content  
* [Density estimation](#density-estimation)
	* Problem motivation  
	* Gaussian distribution  
  	* Algorithm   
* [Building an anomaly detection system](#building-an-anomaly-detection-system)  
	* Developing and evaluating an anomaly detection system  
	* Anomaly detection vs supervised learning  
	* Choosing what features to use  
* [Multivariate Gaussian distribution](#multivairate-gaussian-distribution)  
	* Multivariate Gaussian distribution  
	* Anomaly detection using the multivariate Gaussian distribution  
* [Predicting movie ratings](#predicting-movie-ratings)
	* Problem formulation  
	* Content based recommendations  
* [Collaborative filtering](#collaborative-filtering)  
	* Collaborative filtering  
	* Collaborative filtering algorithm  
* [Low rank matrix factorization](#low-rank-matrix-factorization)  
	* Vectorization: low rank matrix factorization  
	* Implementational detail: mean normalization  
* [Reference](#reference)  

***  
Density estimation  
----  
### Problem motivation  
![](/picture/the_ninth_week/anomaly_detection1.png)  
**Application**:  
1. Fraud detection  
2. Manufacturing  
3. Monitoring computers in a data center  

When your system has too many anomalous things, you should decrease the flag.  
### Gaussian distribution  
![](/picture/the_ninth_week/anomaly_detection2.png)  
![](/picture/the_ninth_week/anomaly_detection3.png)  
### Algorithm  
![](/picture/the_ninth_week/anomaly_detection4.png)  

***  
Building an anomaly detection system  
----  
### Developing and evaluating an anomaly detection system  
![](/picture/the_ninth_week/anomaly_detection5.png)  
![](/picture/the_ninth_week/anomaly_detection6.png)   
Note:Alternative is less good practice.  
![](/picture/the_ninth_week/anomaly_detection7.png)   

### Anomaly detection vs supervised learning  
**Difference**:
```
Anomaly detection:  
1. very small number of positive examples and larege number of negative examples.  
2. Many different 'types' of anomalies. And future anomalies may look nothing like examples that we have seen.  

Supervised learning:  
1. Large number of positive and negative examples.  
2. Enough positive examples for algorithm to get a sense fo what positive examples are like. And the future positive examples are similar to ones in training set.  
```  
**Application**: 
 ```
 Anomaly detection:  
 1. Fraud detection  
 2. Manufacturing(e.g. aircraft engines)  
 3. Monitoring machines in a data center  
 
 Supervised learning:  
 1. Email spam classification  
 2. Weather predcition(sunny/rainy/etc)  
 3. Cancer classification  
 ```

### Choosing what features to use  
![](/picture/the_ninth_week/anomaly_detection8.png)   
You better make your data look like more Gaussian distribution. You can use log() or power() funciton to transform your data like Gaussian distribution.  
Error analysis: Sometimes you need add new features to make mistake anomalous examples correct.  

***  
Multivairate Gaussian distribution  
---  
### Multivariate Gaussian distribution  
**Multivariate Gaussian distribution model**:  
![](/picture/the_ninth_week/anomaly_detection9.png)   
**The conditions of Multivariate Gaussian distribution model**:  
![](/picture/the_ninth_week/anomaly_detection10.png)   
![](/picture/the_ninth_week/anomaly_detection11.png)   
![](/picture/the_ninth_week/anomaly_detection12.png)   
![](/picture/the_ninth_week/anomaly_detection13.png)   
### Anomaly detection using the multivariate Gaussian distribution  
**Anomaly detection with the multivariate Gaussian**:  
![](/picture/the_ninth_week/anomaly_detection14.png)  

***  
Predicting movie ratings  
---  
### Problem formulation  

### Content based recommendations  

***  
Collaborative filtering  
---  
### Collaborative filtering  

### Collaborative filtering algorithm  

***  
Low rank matrix factorization  
---
### Vectroization: low rank matrix fatorization  

### Implementational detail: mean normalization  



***  
Reference  
----  
https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"
