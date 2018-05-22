# The second week——Andrew-Ng Machine Learning Notes  
This is my note on Andrew-Ng's machining learning about the second week contents. Thank you for asking questions.

***
[![](/picture/the_first_week/fig_ML.jpg)][Andrew-Ng-coursera]  
- Author: Guo Guanglu  
- E-mail: 2360889142@qq.com
- QQ: 2360889142  

*** 
[**BACK README**](README.md)  

## Content  
* [Multivariate linear regression](#multivariate-linear-regression)
	* Multiple features
	* Gradient descent for multiple variables
	* Gradient descent in practice I - feature scaling  
	* Gradient descent in practice II - learning rate  
	* Features and polynomial regression  
* [Computing parameters analytically](#computing-parameters-analytically)
	* Normal equation  
	* Normal equation noninvertibility  
* [Programming tips from mentors](programming-tips-from-mentors)  

  
 ***
 Multivariate linear regression  
------------
 #### Multiple features  
 Linear regression with multiple variables is also known as `multivariate linear regression`.  
 We now introduce notation for equations where we can have any number of input variables.  
 ```
 x^i_j=value of feature j in the i^th training example.  
 x^i = the input(features) of the i^the training example.  
 m = the number of training examples  
 n = teh number of features  
 ```  
 The multivariable form of the hypothesis function accommodating these multiple features is as follows:  
 `h_theta(x)=theta_0 + theta_1 * x1 + theta_2 * x2 + theta_3 * x3 + ... + theta_n * n`  
 Using the definition of matrix multiplication, our multivariable hypothesis function can be concisely represented as:  
 ![](/picture/the_second_week/multiple_feature_formula.png)  
 `note: where x_0 = 1`  
 #### Gradient descent for multiple variables  
 The gradient descent equation itself is generally the same form; we just have to repeat it for our 'n' features.
 The equation is :  
 ![](/picture/the_second_week/GD_multvar_formula.png)  
 The following image compares gradient descent with one variable to gradient descent with multiple variables:  
 ![](/picture/the_second_week/GD_fig.png)  
 #### Gradient descent in practice I - feature scaling  
 We can speed up gradient descent by having each of our input values in roughly the same range. This is besause theta will descend        quickly on small ranges and slowly on large ranges, and so will oscillate inefficiently down to the optimum when the variables are  very uneven.  
 The vay to prevent this is to modify the ranges of our input variables so that they are all roughly the same. Ideally:  
 -1<=x(i)<=1  
 or  
 -0.5<=x(i)<=0.5  
 These aren't exact requirements; we are only trying to speed things up. The goal is to get all input variables into roughly one of these ranges, give or take a few.  
 Two technidques to help with this are:  
 * **feature scaling**: involve dividing the input values by the range(i.e. the maximum value minus the minimum value) of the input variablem resulting in a new range of just 1.  
 * **mean normalization**: involves subtracting the average value for an input variable from the values for that input variable resulting in a new average value for the input variable of just zero. To implement both of thes techniques, adjust your input values as shown in this formula:  
 x_i = (x_i - miu_i)/s_i  
 where miu_i is the `average` of all the values for feature(i) and s_i is the range of values (that is, max-min)or s_i is the standard deviation.  
  For example, if x_i represents housing prices with a range of 100 to 2000 and a mean value of 1000, then,  
  x_i = (price - 1000)/1900  
  #### Gradient descent in practice II - learning rate  
  * Debugging gradient descent. Make a plot with number of iterations on the x-axis. Now plot the cost function, J(theta) over the number of iterations of gradient descent. If J(theta) ever increases, then you probably need to decrease `alpha`.  
  * Automatic convergence test. Declare convergence if J(theta) decreases by less than E in one iteration, where E is some small value such as 10^-3. Hower in practice it's difficult to choose this threshold value.  
  ![](/picture/the_second_week/GD_learningrate1.png)  
  It has been proven that if learning rate `alpha` is sufficiently small, then J(theta) will decrease on every iteration.  
  ![](/picture/the_second_week/GD_learningrate2.png)  
  Notes:  
  * If alpha is too small: slow convergence.  
  * If alpha is too large: may not decrease on every iteration and thus may not converge.  
  #### Features and polynomial regression  
  We can combine multiple features into one. For example, we can combine x_1 and x_2 into a new feature x_3 by taking x_1*x_2.  
  * Polynomial regression   
  Our hypothesis funciton need not be linnear(a straight line)if that does not fit the data well. We can change the behavior or curve of our hypothesis function by making it a quadratic, cubic or square root.
  For the cubic version,  
  h_theta(x)=theta_0 + theta_1*x_1 + theta_2*x_1^2 + theta_3*x_1^3   
  we can create new features x2=x_1^2, x_3=x_1^3 , which converts cubic into linear. One important thing to keep in mind, if you choose this way ,then feature scaling becomes very important.  
  
***
Computing parameters analytically   
---------  
  #### Normal equation  
  Gradient descent gives one way of mininminzing J. Another method can also do this, called `Normal Equation`. This method can find the optimum theta without iteration. The equation is given below:  
  ![](/picture/the_second_week/normal_equation1.png)  
  **Note**: there is no need to do feature scaling with the normal equation.  
  ![](/picture/the_second_week/normal_equation2.png)  
  With the normal equation, computing the inversion has complexity O(n^3). So if we have a very large number of features, the normal equation will be slow. In practice, when n exceeds 10,000 it might be a good time to go from a normal solution to an iterative process.  
  
  #### Normal equation noninvertibility  
  When implementing the normal equation in octave we want to use the `pinv` function rather than `inv`. The `pinv` function will give you a value of theta even if X^TX is not invertible.  
  If X^TX is **noninvertible**, the common cases might be having:  
  * Redundant features, where two features are very closely related(i.e. they are linearly dependent).  
  * Too many features(e.g. m<=n). In this case, delete some features or use `regularization`.  
  
  Solution to be the above problems include deleting a feature that is linearly dependent with another or deleting one or more features when there are too many features.  
  
***
Programming tips from mentors  
-----  
**Getting help**:  
1. The submit grader uses a different test case than what is in the PDF file. These test cases use a different size of data set and are more sensitive to small errors than the ex test cases. Your code must work correctly with any size of data set.  
2. Each programming assignment has a "Discussions" area in the Forum. In this section you can often find "unit tests". These are additional test cases, which give you a command to type, and provides the expected results. It is always a good idea to test your functions using the unit tests before submitting to the grader.  

  
  

**********
### Reference
https://hacpai.com/article/1490848332861  
https://blog.csdn.net/guodongxiaren/article/details/23690801  
https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"
