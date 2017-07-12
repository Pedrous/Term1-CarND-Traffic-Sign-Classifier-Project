# **Traffic Sign Recognition** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file, but feel free to use some other method and submit a pdf if you prefer.

---

**Build a Traffic Sign Recognition Project**

The goals / steps of this project are the following:
* Load the data set (see below for links to the project data set)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report


[//]: # (Image References)

[image1]: ./examples/visualization.jpg "Visualization"
[image2]: ./examples/grayscale.jpg "Grayscaling"
[image3]: ./examples/random_noise.jpg "Random Noise"
[image4]: ./1.jpg "Traffic Sign 1"
[image5]: ./2.jpg "Traffic Sign 2"
[image6]: ./3.jpg "Traffic Sign 3"
[image7]: ./4.jpg "Traffic Sign 4"
[image8]: ./5.jpg "Traffic Sign 5"
[image9]: ./6.jpg "Traffic Sign 6"

# Rubric Points

Here is link to my project code: https://github.com/Pedrous/Term1-CarND-Traffic-Sign-Project/blob/master/Traffic_Sign_Classifier.ipynb

## Files submitted
The additional photos, project report and the project code is provided as .ipynb and .html files.

## Dataset exploration
A summary of the dataset is provided as suggested in the beginning of the .ipynb model and also a few traffic signs from the dataset are visualized. These are both shown in the .ipynb file.

## Design and Test a Model Architecture
* I preprocessed the data by changing it to grayscale and then normalizing the data between 0.1 and 0.9. I also tried to reduce the mean from the data but it seemed liked that there was no huge difference so I didn't apply that ultimately.
* The starting point of my model was the LeNet classifier but I increased the amount of filters in the first layer to 16 and in the second layer to 40 so that the input of the first fully connected layer was 1000. Then I added one fully-connected layer there, which takes in 1000 inputs puts out 400. The change of the layers was done because it seemed to improve the result a little bit. I believed that LeNet would be good in traffic signs as it worked for the handwritten numbers as well.
* For the training I used the same batch size of 128 than in LeNet but increased th epochs to 40 so that my netwrok converges. I tried changing the learning rate, but there was no huge difference so I gave that up. The opitimizer was the same AdamOptimizer that it was in the LeNet.
* The training accuracy with these improves was 1 and the validation accuracy was almost 0.95 so I was satisfied with the result. Test set accuracy was also more than 0.93 so that was pretty good. The training accuracy of 1 and the validation and test set accuracy maybe suggests that the model is a bit overfitted so that could still be addressed to improve the classifier.

## Test a Model on New Images

Here are six German traffic signs that I found on the web:

![alt text][image4] ![alt text][image5] ![alt text][image6] 
![alt text][image7] ![alt text][image8] ![alt text][image9]

The fourth image might be bit difficult to classify because it is quite rotated but the other ones shouldn't be a problem. The accuracy of the prediction for the new images was 66.67 %. As I was guessing before-hand, the rotated image wasn't easy to predict and the network had actually confused it to another triangle-shaped traffic sign with a construction guy. That is quite understandable error since they have obvious similarity with human figures. What was surprising, was that the image number 3 was misclassified as "Wild animals crossing" and I cannot find any similarity between these to signs, even the shape of the signs differ. But then overall the second most probable class for the image 3 was the correct one.

Here are the results of the prediction:

| Image			                              |     Prediction	        				           | 
|:-------------------------------------:|:-------------------------------------:| 
| Speed limit (50km/h)                  | Speed limit (50km/h)                  |
| Speed limit (80km/h)                  |	Speed limit (80km/h)								          | 
| Speed limit (50km/h)                  | Wild animals crossing                 |
| Children crossing 				                | Road work                             |
| Go straight or left			                | Go straight or left										         |
| Right-of-way at the next intersection | Right-of-way at the next intersection | 


####3. Describe how certain the model is when predicting on each of the five new images by looking at the softmax probabilities for each prediction. Provide the top 5 softmax probabilities for each image along with the sign type of each probability. (OPTIONAL: as described in the "Stand Out Suggestions" part of the rubric, visualizations can also be provided such as bar charts)

The code for making predictions on my final model is located in the end of the Ipython notebook.

For the first image, the model is sure about the result. The top five soft max probabilities were:
| Probability      |     Prediction	        			 		                    | 
|:----------------:|:------------------------------------------------:| 
| 1.00         	   | Speed limit (50km/h)   						                    | 
| .00...     				  | No passing for vehicles over 3.5 metric tons 				|
| .00...				       | Speed limit (60km/h)		                           |
| .00...	      			 | Speed limit (80km/h)				 				                    |
| .00...				       | Speed limit (100km/h)      			                   |


For the second image: 

| Probability      |     Prediction	        			 		| 
|:----------------:|:----------------------------:| 
| 1.00         	   | Speed limit (80km/h)   						| 
| .00...     				  | Speed limit (30km/h) 						 	|
| .00...				       | End of speed limit (80km/h)		|
| .00...	      			 | Speed limit (60km/h)				 				|
| .00...				       | Speed limit (50km/h)      			|


For the third image: 

| Probability      |     Prediction	        			 		| 
|:----------------:|:----------------------------:| 
| 1.00         	   | Wild animals crossing   					| 
| .00...     				  | Speed limit (50km/h) 						 	|
| .00...				       | Double curve		               |
| .00...	      			 | Speed limit (30km/h)				 				|
| .00...				       | General caution      			     |


For the fourth image: 

| Probability      |     Prediction	        			 		| 
|:----------------:|:----------------------------:| 
| 1.00         	   | Road work   					            | 
| .00...     				  | General caution						 	      |
| .00...				       | Stop		                       |
| .00...	      			 | Keep right				 				          |
| .00...				       | Wild animals crossing      		|


For the fifth image: 

| Probability      |     Prediction	        			 		| 
|:----------------:|:----------------------------:| 
| 1.00         	   | Go straight or left  					   | 
| .00...     				  | Traffic signals						 	      |
| .00...				       | Keep left		                  |
| .00...	      			 | Roundabout mandatory				 				|
| .00...				       | Ahead only     		            |


For the sixth image: 

| Probability      |     Prediction	        			 		            | 
|:----------------:|:----------------------------------------:| 
| 1.00         	   | Right-of-way at the next intersection 			| 
| .00...     				  | General caution						 	                  |
| .00...				       | Double curve		                           |
| .00...	      			 | Beware of ice/snow				 		              		|
| .00...				       | Traffic signals     		                   |
