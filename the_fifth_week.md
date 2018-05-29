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
"Backpropagation" is neural-network terminology for minimizing our cost function, just like what we were doing with gradient descent in logistic and linear regression. Our goal is to compute:  
`min_theta J(theta)`  
That is, we want to minimize our cost function J using an optimal set of parameters in theta. In this section we'll look at the equations we use to compute the partial derivative of J(theta).  
To do so, we use the following algorithm:  
![](/picture/the_fifth_week/backpropagation1.png)  
**Back propagation algorithm**  
Given training set {(x^(1),y^(1)),...,(x^(m),y^(m))}  
* Set delta_i,j^(l):=0 for all(l,i,j)(hence you end up having a matrix full of zeros)  

For training example t=1 to m:  
1. Set a^(1): = x^(t)  
2. Pefrom forward propagation to compute a^(l) for l = 2,3,...,L  

![](/picture/the_fifth_week/backpropagation2.png)  
3. Using y^(t), compute delta^(L) = a^(L) - y^(t)  
Where L is our total number of layers and a^(L) is the vector of outputs of the activation units for the last layer. So our "error values" for the last layer are simply the differences of our actual results in the last layer and the correct outputs in y. To get the delta values of the layers before the last layer, we can use an equation that steps us back from right to left:  
4. Compute delta^(L-1), delta^(L-2),...,delta^(2)  
![](/picture/the_fifth_week/backpropagation3.png)  
The delta values of layer l are calculated by multiplying the delta values in the next layer with the theta matrix of layer l. We then element-wise multiply that with a function called g', or g-prime, which is the derivative of the activation function g evaluated with the input values given by z^(l).  
The g-prime derivative terms can also be written out as :
![](/picture/the_fifth_week/backpropagation4.png)  

The capital-delta matrix D is used as an "accumulator" to add up our values as we go along and eventually compute our partial derivative. Thus we get d(J(theta))/d(theta_ij^(l)) = D_ij^(l)  


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
