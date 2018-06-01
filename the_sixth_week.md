# The sixth week——Andrew-Ng Machine Learning Notes  
This is my note on Andrew-Ng's machining learning about the sixth week contents. Thank you for asking questions.

***
[![](/picture/the_first_week/fig_ML.jpg)][Andrew-Ng-coursera]  
- Author: Guo Guanglu  
- E-mail: 2360889142@qq.com
- QQ: 2360889142  

*** 
[**BACK README**](README.md)  

## Content  
* [Evaluating a learning algorithm](#evaluating-a-learning-algorithm)  
	* Evaluating a hypothesis    
	* Model selection and train/validation/test sets      
* [Bias vs variance](#bias-vs-variance)  
	* Diagnosing bias vs variance        
	* Regularization and bias/variance     
	* Learning curves
	* Deciding what to do next revisited  
* [Building a spam classifier](#building-a-spam-classifier)  
	* Prioritizing what to work on  
	* Error analysis  
* [Reference](#reference)  

***  
Evaluating a learning algorithm  
-----  
### Evaluating a hypothesis  
Once we have done some trouble shooting for errors in our predictions by:  
* Getting more training examples  
* Trying smaller sets of features  
* Trying additional features  
* Trying polynomial features  
* Increasing or decreasing lambda  

We can move on to evaluate our new hypothesis.  
We can split up the data int two sets: **training set** and **test set**. Typically, the proportion of the training set and test set is 
**7:3**.  
The new procedure using these two sets is then:  
1. Learning theta and minimize J_train(theta) using the training set  
2. Compute the test set error J_test(theta)  

**The test set error**:  
1. For linear regression:  
![](/picture/the_sixth_week/LR_test_error.png)  
2. For classification: Misclassification error (aka 0/1 miscalssification error):  
![](/picture/the_sixth_week/classification_test_error.png)  

This gives us a binary 0 or 1 error result based on a misclassification. The average test error for the test set is:  
![](/picture/the_sixth_week/classification_test_error2.png)  
This gives us the proportion of the test data that was misclassified.  

### Model selection and train/validation/test sets  
Just beacause a learning algorithm fits a training set well, that does not mean it is a good hypothesis. It could over fit and as a result your predictions on the test set would be poor. The error of your hypothesis as measured on the data set with which you trained the parameters will be lower than the error on any other data set.  
Given many models with different polynomial degrees, we can use a systematic approach to identify the 'best' function. In order to choose the model of your hypothesis, you can test each degree of polynomial an look at the error result.  
One way to break down our dataset into the three sets is :  
* Training set : 60%  
* Cross validation set : 20%  
* Test set : 20%  

We can now calculate three separate error values for the three different sets using the following method:  
1. Optimize the parameters in theta using the training set for each polynomial degree.  
2. Find the polynomial degree d with the least error using the cross validation set.  
3. Estimate the generalization error using the test set with J_test(theta^(d)), (d = theta from polynomial with lower error)

This way, the degree of the polynomial d has not been trained using the test set.  

***  
Bias vs variance  
-----  
### Diagnosing bias vs variance  
* We need to distinguish whether **bias** or **variance** is the problem contributing to bad predictions.  
* High bias is underfitting and high variance is overfitting. Ideally, we need to find a golden mean between these two.  

![](/picture/the_sixth_week/bias_variance1.png)  
The training error will tend to decrease as we increase the degree d of the polynomial.  
At the same time, the cross validation error will tend to decrease as we increase d up to a point, and then it will increase as d is increased, forming a convex curve.  
![](/picture/the_sixth_week/bias_variance2.png)  
### Regularization and bias/variance  

### Learning curves  

### Deciding what to do next revisited  

***  
Building a spam classifier  
----  
### Prioritizing what to work on  

### Error analysis  




***  
Reference  
----  
https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"
