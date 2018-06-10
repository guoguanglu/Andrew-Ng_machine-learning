# The tenth week——Andrew-Ng Machine Learning Notes  
This is my note on Andrew-Ng's machining learning about the tenth week contents. Thank you for asking questions.

***
[![](/picture/the_first_week/fig_ML.jpg)][Andrew-Ng-coursera]  
- Author: Guo Guanglu  
- E-mail: 2360889142@qq.com
- QQ: 2360889142  

*** 
[**BACK README**](README.md)  

## Content  
* [Gradient descent with large datasets](#gradient-descent-with-large-datasets)
	* Learning with large datasets
	* Stochastic gradient descent  
  	* Mini Batch gradient descent  
  	* Stochastic gradient descent convergence    
* [Advanced Topics](#advanced-topics)  
	* Online learning    
	* Map reduce and data parallelism      
* [Reference](#reference)  

***  
Gradient descent with large datasets  
---  
### Learning with large datasets  
**How can you tell if using all of the data is likely to perform much better than using a subset of the data(sy m=1000)?**  
Plot a learning curve for a range of values of m and verify that the algorithm has high variance when m is small.  
When your learning curve has high bias, you have a good model using a subset of the data , however you should add new features and so on.  
![](/picture/the_tenth_week/large_data1.png)  
**Computationally efficient ways to deal with very big data sets**.  
1. Stochastic gradient descent  
2. Map reduce  

### Stochastic gradient descent  
![](/picture/the_tenth_week/SGD1.png)  
### Mini batch gradient descent  
BGD: Using all m examples in one iteration  
SGD: Using one examples in one iteration  
Mini-GD: Using b examples in one iteration  
![](/picture/the_tenth_week/mini_GD1.png)  
### Stochastic gradient descent convergence  
It may not decrease on every single iteration.  
Learning rate alpha is typically held constant. Can slowly decrease alpha over time if we want theta to converge.(e.g. alpha = const1/(interation_number + const2))  
note: iteration number: really the number of examples.  
![](/picture/the_tenth_week/SGD2.png)  

***  
Advanced topics  
---  
### Online learning  
can adapt to change user perference  
![](/picture/the_tenth_week/Online_learning1.png)  
### Map reduce and data parallelism  
![](/picture/the_tenth_week/map_reduce1.png)  

***  
Reference  
----  
https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"
