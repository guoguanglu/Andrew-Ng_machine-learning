# Andrew-Ng Machine Learning Notes  
This is my note on Andrew-Ng's machining learning. Thank you for asking questions.

***
[![](/picture/fig_ML.jpg)][Andrew-Ng-coursera]  
- Author: Guo Guanglu  
- E-mail: 2360889142@qq.com
- QQ: 2360889142  

***
## Content
* [What is the machine learning](#what-is-the-machine-learning)  
	* Supervised learning  
	* Unsupervised learning  
* [Model and cost function](#model-and-cost-function)
	* Model representation
	* Cost function  
* [Parameter Learning](#parameter-learning)
	* Gradient descent
	* Gradient descent intuiton
	* gradient descent for linear regression
***
What is the machine learning
-----------------------------
* definition  
	* `Arthur Samuele(1959) Machine Learning`:  Field of study that gives computers the ability to learning without being explicitly programmed.  
	* `TOME Mitchell(1998):`  Well-posed Learning Problem:A computer program is said to learn form experience E with respect to some task T and some performance measure P,if its performance on T, as measured by P, improves with experience E.  
* example: `playing checkers`  
E= the experience of playing many games of checkers  
T= the task of playing checkers  
P= the probability that the program will win the next game  
* ML algorithms can be classified as follow:  
	* supervixed learning and unsupervised learning   
	* `others`: reinforcement learning , recommender systems  

***
#### Supervised learning
In supervised learning, we are given a data set and already know what our correct 
output should look like, having the idea that there is a relationship between the 
input and the output.  
* supervised learning problems are categorized:
	* regression: try to map input variables to some continuous function  
	* classification: try to map input variables into discrete categories  
* example:
	* Given data abot the size of houses on the real estate market, try to predict their price.(regression:continuous output problem)  
	* Given a patient with a tumor, predict whether the tumor is malignant or benign(classification: discrete output problem)

***
#### Unsupervised learning
Unsupervised learning allows us to approach problems with little or no idea what our results should look like. We can derive structure
form data where we don't necessarily know the effect of the variables.  
We can derive this structure by clustering the data based on relationships among the variables in the data.  
With unsupervised learning there is no feedback based on the prediction results.  
* example:  
	* `clustering`: Take a collection of 1,000,000 different genes, and find a way to automatically group these genes into groups that are somehow similar or related by different variables, such as lifespan, location, roles, and so on.  
	* `non-clustering`: The "Cocktail Party Algorithm", allows you to find structure in a chaotic environment.(i.e. identifying individual voices and music from a mesh of sounds at a cocktail party).  

***  
Model and cost function
-------  
#### Model representation  
(x(i),y(i)) is called a training example,where x(i) represents ith input variables, y(i) represents ith output varibles. A list of m training examples is called a training set. We will also use X to denote the space of input values, and Y to denote the space of output values. In this example, X=Y=R.  
To describe the supervised learning problem slightly more formally, our goal is , given a training set, to learn a function h:X to Y, so that h(x) is a `good` predictor for the corresponding value of y. For historical reasons, this function h is called a hypothesis. Seen pictorially, the process is therefore like this:  
![](/picture/ML-process.png)  
When the target variable that we're trying to predict is continuous, such as in our housing example, we call the learning problem a regression problem. When y can take on only a small number of discrete values(such as if, given the living area, we wanted to predict if a dwelling is a house or an apartmentm, say), we call it a classification problem.  
#### Cost function  
We can measure the accuracy of our hypothesis function by using a cost function. This takes an average difference(actually a fancier version of an average) of all the results of the hypothesis with inputs from x's and the actual output y's.  
![](/picture/costfunction.png)  
To break it apart, it is 1/2 x' where x' is the mean of the squares of h(xi)-yi, or the difference between the predicted value and the actual value.  
This function is otherwise called the "Squared error function", or "Mean squared error". The mean is halved(1/2) as a convenience for the computation of the gradient descent, as the derivative term of the square function will cancel out the 1/2 term. The following image
summarizes what the cost function does:  
![](/picture/costfunction2.png)  
#### Cost function intuition I  
If we try to think of it in visual terms, our training data set is scattered on the x-y  plane. We are trying to make a straight line(defined by h_theta(x)) which passes through these scattered data points.  
Our objective is to get the best possible line. The best possible line will be such so that the average squared vertical distances of the scattered points from the line will be the least. Ideally, the line should pass through all the points of our training data set. In such a case, the value of J(theta_0,theta_1) will be 0. The following example shows the ideal situation where we have a cost function of 0.  
![](/picture/costfunction_intuition1.png)  
When theta_1=1, we get a slope of 1 which goes through every single data point in our model. Conversely, when theta_1=0.5, we see the vertical distance from ourt fit to the data points increase.  
![](/picture/costfunction_intuition2.png)  
This increases our cost function to 0.58. Plotting several other points yields to the following graph:  
![](/picture/costfunction_intuition3.png)  
Thus as a goal, we should try to minimize the cost function. In this case, theata_1=1 is our global minimum.  
#### Cost function intuition II  
A contour plot is a graph that contains many contour lines. A contour line of a two variable function has a constannt value at all points of the same line. An example of such a graph is the one to the right below.  
![](/picture/costfunction_intuition4.png)  
Taking any color and going along the 'circle', one would expect to get the same value of the cost function. For example, the three green points found on the green line above have the same value for J(theat_0,theta_1) and as a result, they are found along the same line. The circled x displays the value of the cost function for the graph on the left when theta_0=800 and theta_1=-0.15. Taking another h(x) and plotting its contour plot, one gets the following graphs:  
![](/picture/costfunction_intuition5.png)  
When theta_0=360 and theta_1=0, the value of J(theta_0,theta_1) in the contour plot  gets closer to the center thus reducing the cost function error. Now giving our hypothesis function a slightly positive slope results in a better fit of the data.  
![](/picture/costfunction_intuition6)  
The graph above minimizes the cost function as much as possible and consequently, the result of theta_1 and theta_0 tend to be around 0.12 and 250 respectively. Plotting those values on our graph to the right seems to put ourt point in the center of the inner most 'circle'.  

***
Parameter learning
-------------------
#### Gradient Descent  
So we have our hyopythesis function and we have a way of measuring how well it fits into the data. Now we need to estimate the parameters in the hypothesis function. That's where gradient descent comes in.  
![](/picture/gradient_3d.png)  
For the above graph, we start at a initial point（any），to reach the bottom of the graph as soon as possible, we look around and choose the direction with the steepest descent to move towards.  
The gradient descent algorithm is :  
![](/picture/gradient_descent1.png)  
#### Gradient Descent intuition  
According to the below formula:  
![](/picture/gradient_descent_formula.png)  
By the above graph,  we look the derivative term as a number, alpha is bigger than zero, theta_11 eventually converges to its minimum value. The following graph shows that when the slope is negative, the value of theta_1 increases and when it is positive, the value of theta_1 decreases.  
![](/picture/gradient_descent2.png)  
On a side note, we should adjust our parameter alpha to ensure that the gradient descent algorithm converages in a reasonable time. Failure to converge or too much time to obtain the mininmum value imply that ourt step size is wrong.  
![](/picture/gradient_descent3.png)  
`How does gradient descent converge with a fixed step size alpha?`  
![](/picture/gradient_descent4.png)  
#### Gradient descent for linear regression  
When specifically applied to the case of linear regression, a new form of the gradient descent equation can be derived. We can substitube our actual cost function and out actual hypothesis function an modify the equation to:  
![](/picture/gradient_descent5.png)  
where i represents ith data  
The process of derivation is as follow:  
![](/picture/gradient_descent6.png)  
where j represents jth variable responding to jth constant parameter.  
So, this is simply gradient descent on the original cost function J. This method looks at every example in the entire training set on every step, and is called **batch gradient descent**. Note that, while gradient descent can be susceptible to local minima in general, the optimization problem we have posed here for linear regression has only one global, and no other local, optima; thus gradient descent always converges(assuming the learning rate alpha is not too large) to the global minimum. Indeed, J is a convex quadratic function. Here is an example of gradient descent as it is run to minimize a quadratic function.

**********
### Reference
https://hacpai.com/article/1490848332861  
https://blog.csdn.net/guodongxiaren/article/details/23690801  
https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"


