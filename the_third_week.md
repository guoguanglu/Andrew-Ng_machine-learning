# The third week——Andrew-Ng Machine Learning Notes  
This is my note on Andrew-Ng's machining learning about the third week contents. Thank you for asking questions.

***
[![](/picture/the_first_week/fig_ML.jpg)][Andrew-Ng-coursera]  
- Author: Guo Guanglu  
- E-mail: 2360889142@qq.com
- QQ: 2360889142  

*** 
[**BACK README**](README.md)  

## Content  
* [Classification and representation](#classification-and-representation)  
	* Classification  
	* Hypothesis representation  
	* Decision boundary    
* [Logistic regression model](#logistic-regression-model)  
	* Cost function    
	* Simplified cost function and gradient descent  
  	* Advanced optimization  
* [Multiclass classification](#multiclass-classification)  
  * Multiclass classification:One-vs-all  
* [Solving the problem of overfitting](#solving-the-problem-of-overfitting)  
  * The problem of overfitting  
  * Cost function  
  * Regularized linear regression  
  * Regularized logistic regression  

***  
Classification and representation  
-------  
### Classification  
To attempt classification, one method is to use linear regression and map all predictions greater than 0.5 as a 1 and less than 0.5 as a 0. However, this method doesn't work well because classification is not actually a linear function.  
The clasification problem is just like the regression problem, except that the values we now want to predict take on only a small number of discrete values. For now, we will focus on the **binary classification problem** in which y can take on only two values, 0 and 1. (Most of what we say here will also generalize to the multiple-class case.) For instance, if we are trying to build a spam mail, and 0 otherwise. Hence, y in {0, 1} . 0 is also called the negative class, and 1 the positive class, and they are sometimes also denoted by the symbols "-" and "+". Given x^(i), the corresponding y^(i) is also called the label for the training example.  

### Hypothesis representation  
We need to change the form for our hypotheses h_theta(x) to satisfy 0<= h_theta(x) <=1.  
Our new form uses the "Sigmoid Function", also called the  "Logistic Function":
```
h_theta(x) = g(theta^T*x)  
z = theta^T*x  
g(z) = 1/(1+e^(-z))  
```  

The image shows us what the sigmoid function looks like:  
![](/picture/the_third_week/logistic1.png)  
h_theta(x) will give us the **probability** that our output is 1.  

### Decision boundary  
The **decision boundary** is the line that separates the area where y=0 and where y=1(for two classification). It is created by our hypothesis function.  
For example, g(z)>=0.5,y=1, then, z>0. For the z = 0 is the decision boundary.  
The decision boundary doesn't need to be linear, and could be a function that describes a circle or any shape to fit ourt data.  

***  
Logistic regression model  
------  
### Cost function  

### Simplified cost function and gradient descent  

### Advanced optimization  


***  
Multiclass classification  
----  
### Multiclass classification:One-vs-all  


***  
Solving the problem of overfitting  
-----  
### The problem of overfitting  

### Cost function  

### Regularized linear regression  

### Regularized logistic regression  



***
## Reference  
https://www.coursera.org/learn/machine-learning/supplement/fDCQp/classification  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"
