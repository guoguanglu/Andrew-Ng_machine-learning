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
* L = total number of layers in the network  
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
Recall that the cost function for a neural network is:  
![](/picture/the_fifth_week/backpropagation5.png)  
If we consider simple non-multiclass classification(k=1) and disregard regularization, the cost is computed with:  
![](/picture/the_fifth_week/backpropagation6.png)  
Intuitively, delta_j^(l) is the "error" for a_j^(l)(unit j in layer l). More formally, the delta values are actually the derivative of the cost function:  
![](/picture/the_fifth_week/backpropagation7.png)  
Recall that our derivative is the slope of a line tangent to the cost function, so the steeper the slope the more incorrect we are. Let us consider the following neural network below and see how we could calculate some delta_j^(l):  
![](/picture/the_fifth_week/backpropagation8.png)  
In the image above, to calculate delta_2^(2), we multiply the weights theta_12^(2) and theta_22(2) by their respective delta values found to the right of each edge. So we get delt_2^(2) = theta_12^(2)\*delta_1^(3) + theta_22(2)\*delta_2^(3). To calculate every single possible theta_j^(l), we could start from the right of our diagram. We can think of our edges as our theta_ij. Going from right to left, to calculate the value of theta_j^(l), you can just take the over all sum of each weight times the delta it is coming from. Hence, another example would be delta_2^(3) = theta_12^(3)\*delta_1^(4).  

***  
Backpropagation in practice  
----  
### Implementation note: unrolling parameters  
In order to use optimizing functions such as "fminunc()", we will want to "unroll" all the elements and put them into one long vector.   
![](/picture/the_fifth_week/backpropagation9.png)  
### Gradient checking  
Gradient checking will assure that our backpropagation works as intended. We can approximate the derivative of our cost function with:  
![](/picture/the_fifth_week/backpropagation10.png)  
With multiple theta matrices, we can approximate the derivative with respect to theta_j as follows:  
![](/picture/the_fifth_week/backpropagation11.png)  
A small value for epsilon such as epsilon = 10^-4, guarantees that the math works out properly. If the value for epsilon is too small, we can end up with numerical problems.  
Hence, we are only adding or subtracting epsilon to the theta_j matrix. In octave we can do it as follows:  
![](/picture/the_fifth_week/backpropagation12.png)  
We previously saw how to calculate the deltaVector. So once we compute our gradApprox vector, we can check that gradApprox is similar to deltaVector.  
Once you have verified **once** that your backpropagation algorithm is correct, you don't need to compute gradApprox again. **The code to compute gradApprox can be very slow.**  
### Random initialization  
Initializing all theta weights to zero does not work with neural networks. When we backpropagate, all nodes will update to the same value repeatedly. Instead we can randomly initialize our weights for our theta matrices using the following method:  
![](/picture/the_fifth_week/backpropagation13.png)  
Hence, we initialize each theta_ij^(l) to a random value between [-epsilon,epsilon]. Using the above formula guarantees that we get the desired bound. The same procedure applies to all the theta's. Below is some working code you could use to experiment.  
![](/picture/the_fifth_week/backpropagation14.png)  
Where rand(x,y) is just a function in octave that will initialize a matrix of random real numbers between 0 and 1.  
### Putting it together  
First, pick a network architecture; choose the layout of your neural network, including how many hidden units in each layer and how many layers in total you want to have.  
* Number of input units = dimension of features x^(i)  
* Number of output units = number of classes  
* Number of hidden units per layer = usually more the better(must balance with cost of computation as it increases with more hidden units.)  
* Defaults: 1 hidden layer.If you have more than 1 hidden layer, then it is recommended that you have the same number of units in every hidden layer.  

**Training a neural network**  
1. Randomly initialize the weights  
2. Implement forward propagation to get h_theta(x^(i)) for any x^(i)  
3. Implement the cost function  
4. Implement backpropagation to compute parital derivatives  
5. Use gradient checking to confirm that your backpropagation works. Then disable gradient checking.  
6. Use gradient descent or a built-in optimization function to minimize the cost function with the weights in theta.  

When we perform forward and back propagation, we loop on every training example:  
![](/picture/the_fifth_week/backpropagation15.png)  
The following image gives us an intuition of what is happening as we are implementingg our neural network:  
![](/picture/the_fifth_week/backpropagation16.png)  
Ideally, you want h_theta(x^(i)) is similar to y^(i). This will minimize our cost function. However, keep in mind that J(theta) is not convex and thus we can end up in a local minimum instead.  

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
