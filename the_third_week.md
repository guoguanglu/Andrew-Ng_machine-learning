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
We cannot use the same cost function that we use for linear regression because the logistic function will cause the output to be wavy, causing many local optima. In other words, it will not be a convex function.  
Instead, ourt cost function for logistic regression looks like:  
![](/picture/the_third_week/logistic2.png)  
When y=1, we get the following plot:  
![](/picture/the_third_week/logistic3.png)  
Similarly, when y = 0, we get the following plot:  
![](/picture/the_third_week/logistic4.png)  
For the above plots, we can find following formulations:  
![](/picture/the_third_week/logistic5.png)  

### Simplified cost function and gradient descent  
According to the former Cost function , we can get the entire cost function of the logistic regression as follows:  
![](/picture/the_third_week/logistic6.png)  
A vectorized implementation is:  
![](/picture/the_third_week/logistic7.png)  
the general form of gradient descent of logistic regression is similar to linear regression:  
![](/picture/the_third_week/logistic8.png)  
A vectorized implementation is:  
![](/picture/the_third_week/logistic9.png)  

### Advanced optimization  
"Conjugate gradient", "BFGS" and "L-BFGS" are more sophisticated, faster ways to optimize theta that can be used instead of gradient descent. We suggest that you should not write these more sophisticated glgorithms yourself(unless you are an expert in numerical computing)but use the libraries instead, as they're already tested and highly optimized. Octave provides them.  
We first need to probide a function that evaluates the following two functions for a given input value theta:  
J(theta)  
dJ(theta)  
We can write a single function that returns both of these:  
```#matlab
function [jVal, gradient] = costFunction(theta)  
	jVal = [code to compute J(theta)];  
	gradient = [code to compute derivative of J(theta)];  
end  
```  
Then we can use octave's "fminunc()" optimization algorithm along with the "optimset()"function that creates an object containing the options we want to send to "fminunc".  
```
options = optimset('GradObj', 'on', 'MaxIter', 100);  
initilTheta = zeros(2, 1);  
[optTheta, functionVal, exitFlag] = fminunc(@costFunction, initialTheta, options);  
```  
We give to the function "fminunc()"our cost function, our initial vector of theta values, and the "options"object that we created beforehand.  

***  
Multiclass classification  
----  
### Multiclass classification:One-vs-all  
We are basically choosing one clas and then lumping all the others into a single second class. We do this repeatedly, applying binary logistic regression to each case, and then use the hypothesis that returned the highest value as our prediction.  
The following image shows how one could classify 3 classes:  
![](/picture/the_third_week/one_vs_all.png)  
**Two notes:**  
1. Train a logistic regression classifier h_theta(x) for each class to predict the probability that y=i.  
2. To make a prediction on a new x, pick the class that maximizes h_theta(x)  


***  
Solving the problem of overfitting  
-----  
### The problem of overfitting  
When we fit  training data, three conditions are shown as follows:  
![](overfitting.png)  
The first plot called underfitting or high bias is when the form ourt hypothesis function h maps poorly to the trend of the data.  
The second plot called just right can fit the data very well, which can give us a good prediction.  
The third plot called overfitting or high variance is caused by a hypothesis function that fits the available data but does not generalize well to predict new data.  
There are two main options to address the issue of overfitting:  
1. Reduce the number of features:  
* Manually select which features to keep  
* Use a model selection algorithm  
2. Regularization  
* Keep all the features, but reduce the magnitude of parameters theta_j.  
* Regularization works well when we have a lot of slightly useful features.  

### Cost function  

### Regularized linear regression  

### Regularized logistic regression  



***
## Reference  
https://www.coursera.org/learn/machine-learning/supplement/fDCQp/classification  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"
