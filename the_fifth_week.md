# The fifth week——Andrew-Ng Machine Learning Notes  
This is my note on Andrew-Ng's machining learning about the fifth week contents. Thank you for asking questions.

***
[![](/picture/the_first_week/fig_ML.jpg)][Andrew-Ng-coursera]  
- Author: Guo Guanglu  
- E-mail: 2360889142@qq.com
- QQ: 2360889142  

*** 
[**BACK README**](README.md)  

## Content  
* [Cost function and backpropagation](#cost-function-and-backpropagation)  
	* Cost function    
	* Backpropagation algorithm    
	* Backpropagation intuition      
* [Backpropagation in practice](#backpropagation-in-practice)  
	* Implementation note: unrolling parameters      
	* Gradient checking    
  * Random initialization  
  * Putting it together  
* [Application of neural networks](#application-of-neural-networks)  
  * Autonomous driving    
* [Reference](#reference)  

***  
Cost function and backpropagation  
-----  
### Cost function  
Let's first define a few variables that we will need to use :  
* L = toal number of layers in the network  
* s_l = number of units (not counting bias unit) in layer l  
* K = number of output units/classes  

Recall that in neural networks, we may have many output nodes. We denote h_theta(x)k as being a hypthesis that results in the k^th output. Our cost function for neural networks is going to be a generalization of the one we used for logistic regression. Recall that the cost function for regularized logistic regression was :  
![](/picture/the_fifth_week/nn_cost_function1.png)  
For neural networks, it is going to be slightly more complicated:  
![](/picture/the_fifth_week/nn_cost_function2.png)  
We have added a few nested summations to account for our multiple output nodes. In the first part of the equation, before the square brackets, we have an additional nested summation that loops throught the number of output nodes.  
In the regularization part, after the square brackets, we must account for multiple theta matrices. The number of columns in our current theta matrix is equal to the number of nodes in our current layer(excluding the bias unit). As before with logistic regression, we square every term.  
Note:  
* the double sum simply adds up the logistic regression costs calculated for each cell in the output layer.  
* the triple sum simply adds up the squares of all the individual thetas in the entire network.  
* the i in the triple sum does not refer to training example i.  

### Backpropagation algorithm  

### Backpropagation intuition  

***  
Backpropagation in practice  
----  
### Implementation note: unrolling parameters  

### Gradient checking  

### Random initialization  

### Putting it together  

***  
Application of neural networks    
-----  
### Autonomous driving  

***  
Reference  
----  
https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"
