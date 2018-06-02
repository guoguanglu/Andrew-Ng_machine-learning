# The seventh week——Andrew-Ng Machine Learning Notes  
This is my note on Andrew-Ng's machining learning about the seventh week contents. Thank you for asking questions.

***
[![](/picture/the_first_week/fig_ML.jpg)][Andrew-Ng-coursera]  
- Author: Guo Guanglu  
- E-mail: 2360889142@qq.com
- QQ: 2360889142  

*** 
[**BACK README**](README.md)  

***
## Content  
* [Large margin classification](#large-margin-classification)  
	* Optimization objective  
  	* Large margin intuition  
 	* Mathematics behind large margin classification  
* [Kernels](#kernels)  
	* Kernels I  
	* Kernels II  
* [SVMs in practice](#svms-in-practice)  
 	* Using an SVM  
* [Reference](#reference)  

***
Large margin classification  
-----
### Optimization objective  
![](/picture/the_seventh_week/svm1.png)  

### Large margin intuition  
![](/picture/the_seventh_week/svm2.png)  
![](/picture/the_seventh_week/svm3.png)  
From the above picture, the back line is SVM decision boundary (intuition). Large margin classifier is the distance between the black line and blue line.  
![](/picture/the_seventh_week/svm4.png)  
When the C is very large, the clasifier will make training dataset correct, the decision boundary will be pink line. When C is small, the decision boundary will be black line.   
### Mathematics behind large margin classification  
**Vector inner product**:  
`u^T\*v = p * ||u||`  
The geometric meaning of Vector u and v inner product is that length of projection of v onto u products norm of u. It is shown as follows:  
![](/picture/the_seventh_week/svm5.png)  
![](/picture/the_seventh_week/svm6.png)  
![](/picture/the_seventh_week/svm7.png)  

***  
Kernels  
----  
### Kernels I  
We can get:  
When x is close to l^(1), then new feature f1 is similar to one.  
When x is far away from l^(1), then new featuref1 is similar to zero.
![](/picture/the_seventh_week/kernel1.png)  
The larger sigma is , the fatter the plot is. However the new feature maximum is one.  
![](/picture/the_seventh_week/kernel2.png)  
When introducing three landmarks l(1),l(2),l(3), we can get intuitively red decision boundary.  
![](/picture/the_seventh_week/kernel3.png)  

### Kernels II  
**SVM with kernels**:  
1. Given training data set (x^(1), y^(1)), (x^(2), y^(2)),...,(x^(m), y^(m))  
2. Choose l^(1) = x^(1), l^(2) = x^(2),..., l^(m) = x^(m)  
3. By similarity function, we can get the new features:  
```
f_1 = similarity(x, l^(1))  
f_2 = similarity(x, l^(2))  
f_m = similarity(x, l^(m))  
f = [f_0, f_1, f_2,..., f_m],  where f_0 = 1  
```  
the number of feature f is m+1. We can get the cost function of SVM with kernel as follows:  
![](/picture/the_seventh_week/kernel4.png)  

***  
SVMs in practice  
-----  
### Using an SVM  
try to use SVM software package(e.g. liblinear, libsvm) , don't write svm by yourself  
Need to specify:  
1. Choice of parameter C.  
2. Choice of kernel ( no-kernel called linear kernel)  

For Gaussian kernel:  
Need to choose sigma: 
* Higher variance, larger sigma  
* Higher bias, lower sigma  

**when do we choose Gaaussian kernel?**  
when the number of features n is small, and the size of training dataset is large.  
Note:  
* Do perform feature scaling before using the Gaussian kernel.  
* Not all similarity functions make valid kernels, which needs to satify technical condition called "mercer's Theroem" to make sure SVM packages's optimization run correctly, don't diverge.  

Some kernel can be used:  
1) Polynomial kernel  
2) More esoteric: string kernel, chi-square kernel, histogram inersection kernel  

**Use logistic or SVM 
1) n >> m(n=10000,m=1-1000) use logistic regression or SVM without kernel  
2) n is small, m is intermediate(n=1-1000,m=10-10000) use SVM with Gaussian kernel  
3) n is small, m is large(n=1-1000, m=50000+) create/add more features, then use logistic regression or SVM without kernel  

Note:  
Neural network likely to work well for most of these settings, but may be slower to train.  

***  
Reference  
----  
Reference  
-----  
https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"

