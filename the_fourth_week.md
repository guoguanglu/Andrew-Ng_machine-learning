# The fourth week——Andrew-Ng Machine Learning Notes  
This is my note on Andrew-Ng's machining learning about the fourth week contents. Thank you for asking questions.

***
[![](/picture/the_first_week/fig_ML.jpg)][Andrew-Ng-coursera]  
- Author: Guo Guanglu  
- E-mail: 2360889142@qq.com
- QQ: 2360889142  

*** 
[**BACK README**](README.md)  

## Content  
* [Neural Networks](#neural-networks)
	* Model representation I  
	* Model representation II  
* [Applications](#applications)  
	* Examples and intuitions I  
	* Examples and intuitins II  
	* Multiclass classification  
* [Reference](#reference)
	
***  
Neural Networks  
-----  
### Model representation I  
![](/picture/the_fourth_week/neural_networks1.png)    

### Model representation II  
![](/picture/the_fourth_week/neural_networks2.png)    

***  
Applications  
------  
### Examples and intuitions I  
Neural neetworks can be used to simulate logical gates. The following is an example of the logical operator 'OR', meaning either x_1 is true or x_2 is true, or both:  
![](/picture/the_fourth_week/neural_networks3.png)  
Where g(z) is the following:  
![](/picture/the_fourth_week/neural_networks4.png)  
### Examples and intuitions II  
There we have the XNOR operator using a hidden layer with two nodes! The following summarizes the above algorithm:  
![](/picture/the_fourth_week/neural_networks5.png)  
### Multiclass classification  
To classify data into multiple classes, we let our hypothesis function return a vector of values. Say we wanted to classify our data into one of four categories. We will use the following example to see how this classification is done. This algorithm takes as input an image and classifies it accordingly:  
![](/picture/the_fourth_week/neural_networks6.png)  

***
Reference  
----  
https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"

