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
  
 ***
 ### Multivariate linear regression  
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
 #### Gradient descent for multiple  
 The gradient descent equation itself is generally the same form; we just have to repeat it for our 'n' features.
 The equation is :  
 ![](/picture/the_second_week/GD_multvar_formula.png)  
 The following image compares gradient descent with one variable to gradient descent with multiple variables:  
 ![](/picture/the_second_week/GD_fig)  
  

**********
### Reference
https://hacpai.com/article/1490848332861  
https://blog.csdn.net/guodongxiaren/article/details/23690801  
https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"
