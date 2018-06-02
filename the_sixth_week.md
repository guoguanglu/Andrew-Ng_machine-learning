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
![](/picture/the_sixth_week/reg_bias_variance.png)  
In the figure above, we see that as lambda increases, ourt fit becomes more rigid. On the other hand, as lambda approaches 0, we tend to over overfit the data. So how do we choose our parameter lambda to get it "just right"? In order to choose the model and the regularization term lambda, we need to :  
1. Create a list of lambdas {i.e. lambda in {0,0.01,0.02,0.04,0.08,0.16,0.32,0.64,1.28,2.56,5.12,10.24}};  
2. Create a set of models with different degrees or any other variants.  
3. Iterate through the lambdas and for each lambda go through all the models to learn some theta.  
4. Compute the cross validation error using the learned theta(computed with lambda) on the J_cv(theta) without regularization or lambda=0  
5. Select the best combo that produces the lowest error on the cross validation set.  
6. Using the best combo theta and lambda, apply it on J_test(theta) to see if it has a good generalization of the probelm.  

### Learning curves  
Training an algorithm on a very few number of data points(such as 1, 2 or 3) will easily have 0 errors because we can  always find a quadratic curve that touches exactly those number of points. Hence:  
* As the training set gets larger, the error for a quadratic function increases.  
* The error value will plateau out after a certain m, or training set size.  

**Experiencing high bias:**  
**Low training set size**: causes J_train(theta) to be low and J_CV(theta) to be high.  
**Large training set size**: causes both J_train(theta) and J_CV(theta) to be high with J_train(theta) is similar to J_CV(theta).  
If a learning algorithm is suffering from **high bias**, getting more training data will not(by itself) help much.  
![](/picture/the_sixth_week/learning_curves.png)  
**Experiencing high variance**: 
 **Low training set size**: J_train(theta) will be low and J_CV(theta) will be high.  
 **Large training set size**: J_train(theta) increases with training set size and J_CV(theta) continues to decrease without leveling off. Also, J_train(theta) < J_CV(theta) but the difference between them remains significant.  
 If a learning algorithm is suffering from **high variance**, getting more training data is likely to help.  
 ![](/picture/the_sixth_week/learning_curves2.png)  
### Deciding what to do next revisited  
Our decision process can be broken down as follows:  
* Getting more training examples: Fixes high variance  
* Trying smaller sets features: Fixes high variance  
* Adding features: Fixes high bias  
* Adding polynomial features: Fixes high bias  
* Decreasing lambda: Fixes high bias  
* Increasing lambda: Fixes high variance  

**Diagnosing neural networks**  
* A neural network with fewer parameters is prone to underfitting. It is also computationally cheaper.  
* A large neural network with more parameters is prone to overfittingg. It is also computationally expensive. In this case you can use regularization(increase lambda) to address the overfitting.  

**Model complexity effects:**  
* Lower-order polynomials(low model complexity) have high bias and low variance. In this case, the model fits poorly consistently.   
* Higher-order polynomials(high model complexity) fit the training data extremely well and the test data extremly poorly. These have low bias on the training data, but very high variance.  
* In reality, we would want to choose a model somewhere in between, that can generalize well but also fits the data reasonably well.
***  
Building a spam classifier  
----  
### Prioritizing what to work on  
Given a data set of emails, we could construct a vector for each email. Each entry in this vector represents a word. The vector normally contains 10,000 to 50,000 entries gathered by finding the most frequently used words in our data set. If a word is to be found in the email, we would assign its respective entry a 1, else if it is not found, that entry would be a 0. Once we have all our x vectors ready, we train our algorithm and finally, we could use it to classify if an email is a spam or not.  
![](/picture/the_sixth_week/spam_classification1.png)  
So how could you spend your time to improve the accuracy of this classifier?  
* Collect lots of data (for example "honeypot" project but doesn't always work)  
* Develop sophisticated features(for example: using email header data in spam emails)  
* Develop algorithms to process your input in different ways(for example: recognizing misspelling in spam)  

It is difficult to tell which of the option will be most helpful.  
### Error analysis  
The recommended approach to solving machine learning problems is to:  
* Start with a simple algorithm, implement it quickly, and test it early on your cross validation data.  
* Plot learning curves to decided if more data, more features, etc. are likely to help.  
* Mannually examine the errors on examples in the cross validation set and try to spot a trend where most of the errors were made.  

For example, assume that we have 500 emails and our algorithm misclassifies a 100 of them. We could manually analyze the 100 emails and categorize them based on what type of emails they are. We could then try to come up with new cues and features that would help us classify these 100 emails correctly. Hence, if most of out misclassified emails are those which try to steal passswords, then we could find some features that are particular to those emails and add them to our model. We could also see how classifying each word accordingg to its root changes our error rate:  
![](/picture/the_sixth_week/spam_classification2.png)  
It is very important to get error results as a single, numerical value. Otherwise it is difficult to assess your algorithms's performance. For example if we use stemming, which is the process of treating the same word with different forms(fail/failing/failed)as one word(fail)
, and get a 3% error rate instead of 5%, then we should definitely add it to our model. However, if we try to distinguish between upper case and lower case letters and end up gettingg a 3.2% error rate instead of 3%, then we should avoid using this new feature. Hence, we should try new things, get a numerical value for our error rate, and based on our result decide whether we want to keep the new feature or not.  



***  
Reference  
----  
https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"
