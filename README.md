# Andrew-Ng Machine Learning Notes
This is my note on Andrew-Ng's machining learning. Thank you for asking questions.

***
[![]()][Andrew-Ng-coursera]  
- Author: Guo Guanglu  
- E-mail: 2360889142@qq.com
- QQ: 2360889142  

***
## Content
* [What is the machine learning](#'What+is+the+machine+learning')  
	* Supervised learning  
	* Unsupervised learning    
***

### What is the machine learning
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


**********

### Reference
https://hacpai.com/article/1490848332861  
https://blog.csdn.net/guodongxiaren/article/details/23690801  
https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"


