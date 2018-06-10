# The eleventh week——Andrew-Ng Machine Learning Notes  
This is my note on Andrew-Ng's machining learning about the eleventh week contents. Thank you for asking questions.

***
[![](/picture/the_first_week/fig_ML.jpg)][Andrew-Ng-coursera]  
- Author: Guo Guanglu  
- E-mail: 2360889142@qq.com
- QQ: 2360889142  

*** 
[**BACK README**](README.md)  

## Content  
* [Photo OCR](#photo-ocr)
	* Problem description and pipeline    
	* Sliding windows    
  	* Getting lots of data and artificial    
  	* Ceiling analysis: what part of the pipeline to work on next    
* [Conclusion](#conclusion)  
* [Reference](#reference)  

*** Photo OCR  
### Problem description and pipeline  
for example:  
Photo OCR pipleine:  
1. Text detection  
2. Character segmentation  
3. Character classification  

![](/picture/the_eleventh_week/OCR_pipeline.png)  
### Sliding windows  
![](/picture/the_eleventh_week/sliding_window.png)  
### Getting lots of data and artificial  
![](/picture/the_eleventh_week/get_data.png)  
Discussion on getting more data:  
1. Make sure you have a low bias classifier before expending the effort.  
2. How much work would it be to get 10x as much data as we currently have?  
	* Artificial data synthesis  
	* Collect/label it yourself  
	* Crowd source (E.g. Amazon Mechanical Turk)  

### Ceiling analysis: what part of the pipeline to work on next
![](/picture/the_eleventh_week/ceiling_analysis.png)  
Ceiling analysis can tell us on which part of pipeline we should spend a lot of effort.  

***  
Conclusion  
---  
![](/picture/the_eleventh_week/conclusion.png)  

***  
Reference  
----  
https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation  

---------------------------------------------------------
[Andrew-Ng-coursera]:https://www.coursera.org/learn/machine-learning/lecture/db3jS/model-representation "Andrew Ng coursera"
