# Traffic Sign Classification

## Eva Liu

Traffic Sign Classification

The goals / steps of this project are the following:


**Build a Traffic Sign Recognition Project**

The goals / steps of this project are the following:
* Load the data set (see below for links to the project data set)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report


## Rubric Points
###Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/481/view) individually and describe how I addressed each point in my implementation.  

---


## 1. Provide a basic summary of the data set. 

I used the pandas library to calculate summary statistics of the traffic
signs data set:

* Number of training examples = 34799;
* Number of validation examples = 4410;
* Number of testing examples = 12630;
* Number of label set examples = 34799;
* Image data shape = (32, 32, 3);
* Number of classes = 43;

## 2. Include an exploratory visualization of the dataset.

Here is an exploratory visualization of the data set. It is a bar chart showing how the data distribute.

![stack Overflow](https://github.com/evaliu1/CarND-Term1-P2/blob/master/distribution.PNG)



# Design and Test a Model Architecture

## 1. Preprocessed the image data. What techniques were chosen and why did you choose these techniques?

As a first step, I decided to convert the images to grayscale because this will change the image from 3 RGB layers to 1 layer.
Here is an example of a traffic sign image before and after grayscaling.

![alt text](https://github.com/evaliu1/CarND-Term1-P2/blob/master/colored_img.PNG)
![alt text](https://github.com/evaliu1/CarND-Term1-P2/blob/master/gray_img.PNG)

As a last step, I normalized the image data so it will give me the mean value 0 for distribution.

I decided to generate additional data because ... 

To add more data to the the data set, I used the following techniques because ... 

Here is an example of an original image and an augmented image:

![alt text][image3]

The difference between the original data set and the augmented data set is the following ... 


## 2. Final model architecture looks like including model type, layers, layer sizes, connectivity, etc.) 

My final model consisted of the following layers:

| Layer         		|     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
| Input         		| 32x32x1 RGB image   							| 
| Convolution 3x3     	| 5x5 stride, same padding, outputs 28x28x6 	|
| RELU					|												|
| Max pooling	      	| 2x2 stride,  outputs 14x14x6 				|
| Convolution 3x3	    | 5x5 stride, same padding, outputs 10x10x16			|
| RELU					|												|
| Max pooling	      	| 2x2 stride,  outputs 5x5x16 				|
| Fully connected		| outputs:120       									|
| Fully connected		| outputs:84       									|
| Fully connected		| outputs:10       									|
| Softmax				| etc.        									|
|						|												|
|						|												|
 


## 3. Describe how you trained your model. The discussion can include the type of optimizer, the batch size, number of epochs and any hyperparameters such as learning rate.

To train the model, I used an ....
* AdamOptimizer for managing learning rate
* Batch Size: 128
* Epochs: 30
* Learning rate: 0.001
* Variables initialized with normal distribution (mean=0, std dev=0.1)
* Biases initialized with zeros

## 4. Describe the approach taken for finding a solution and getting the validation set accuracy to be at least 0.93. Include in the discussion the results on the training, validation and test sets and where in the code these were calculated. Your approach may have been an iterative process, in which case, outline the steps you took to get to the final solution and why you chose those steps. Perhaps your solution involved an already well known implementation or architecture. In this case, discuss why you think the architecture is suitable for the current problem.

My final model results were:
* training set accuracy of ?
* validation set accuracy of ? 
* test set accuracy of ?

If an iterative approach was chosen:
* What was the first architecture that was tried and why was it chosen?
* What were some problems with the initial architecture?
* How was the architecture adjusted and why was it adjusted? Typical adjustments could include choosing a different model architecture, adding or taking away layers (pooling, dropout, convolution, etc), using an activation function or changing the activation function. One common justification for adjusting an architecture would be due to overfitting or underfitting. A high accuracy on the training set but low accuracy on the validation set indicates over fitting; a low accuracy on both sets indicates under fitting.
* Which parameters were tuned? How were they adjusted and why?
* What are some of the important design choices and why were they chosen? For example, why might a convolution layer work well with this problem? How might a dropout layer help with creating a successful model?

If a well known architecture was chosen:
* What architecture was chosen?
 LeNet Architecture.
* Why did you believe it would be relevant to the traffic sign application?

* How does the final model's accuracy on the training, validation and test set provide evidence that the model is working well?
 

# Test a Model on New Images

## 1. Choose five German traffic signs found on the web and provide them in the report. For each image, discuss what quality or qualities might be difficult to classify.

Here are five German traffic signs that I found on the web:

![alt text](https://github.com/evaliu1/CarND-Term1-P2/blob/master/p0.jpg)
![alt text](https://github.com/evaliu1/CarND-Term1-P2/blob/master/p1.jpg) 
![alt text](https://github.com/evaliu1/CarND-Term1-P2/blob/master/p3.jpg)
![alt text](https://github.com/evaliu1/CarND-Term1-P2/blob/master/p4.jpg)
![alt text](https://github.com/evaliu1/CarND-Term1-P2/blob/master/p5.jpg)

The first image might be difficult to classify because ...

####2. Discuss the model's predictions on these new traffic signs and compare the results to predicting on the test set. At a minimum, discuss what the predictions were, the accuracy on these new predictions, and compare the accuracy to the accuracy on the test set (OPTIONAL: Discuss the results in more detail as described in the "Stand Out Suggestions" part of the rubric).

Here are the results of the prediction:

| Image			        |     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| Stop Sign      		| Stop sign   									| 
| U-turn     			| U-turn 										|
| Yield					| Yield											|
| 100 km/h	      		| Bumpy Road					 				|
| Slippery Road			| Slippery Road      							|


The model was able to correctly guess 4 of the 5 traffic signs, which gives an accuracy of 80%. This compares favorably to the accuracy on the test set of ...

####3. Describe how certain the model is when predicting on each of the five new images by looking at the softmax probabilities for each prediction. Provide the top 5 softmax probabilities for each image along with the sign type of each probability. (OPTIONAL: as described in the "Stand Out Suggestions" part of the rubric, visualizations can also be provided such as bar charts)

The code for making predictions on my final model is located in the 11th cell of the Ipython notebook.

For the first image, the model is relatively sure that this is a stop sign (probability of 0.6), and the image does contain a stop sign. The top five soft max probabilities were

| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| .60         			| Stop sign   									| 
| .20     				| U-turn 										|
| .05					| Yield											|
| .04	      			| Bumpy Road					 				|
| .01				    | Slippery Road      							|


For the second image ... 

