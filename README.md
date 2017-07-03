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
* Image data shape = (32, 32, 3);
* Number of classes = 43;

## 2. Include an exploratory visualization of the dataset.

Here is an exploratory visualization of the data set. It is a bar chart showing how the data distribute.

![stack Overflow](https://github.com/evaliu1/CarND-Term1-P2/blob/master/distribution.PNG)

From this histogram, we can see different classes have different data distribution. So when we training the data, so of the signs will get a better result.


# Design and Test a Model Architecture

## 1. Preprocessed the image data

As a first step, I decided to convert the images to grayscale because this will change the image from 3 RGB layers to 1 layer.
Here is an example of a traffic sign image before and after grayscaling.

![alt text](https://github.com/evaliu1/CarND-Term1-P2/blob/master/colored_img.PNG)
![alt text](https://github.com/evaliu1/CarND-Term1-P2/blob/master/gray_img.PNG)

As a last step, I normalized the image data so it will give me the mean value 0 for distribution.



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
|	Flatten					|					output:400							|
| Fully connected		| outputs:120       									|
|	RELU					|												|
|	Dropout					|												|
| Fully connected		| outputs:84       									|
|	RELU					|												|
|	Dropout					|												|
| Fully connected		| outputs:43      									|


## 3. Describe how you trained your model

To train the model, I used an ....
* AdamOptimizer for managing learning rate
* Batch Size: 128
* Epochs: 30
* Learning rate: 0.001
* Variables initialized with normal distribution (mean=0, std dev=0.1)
* Biases initialized with zeros

## 4. Describe the approach taken for finding a solution 
 
My final model results were: 
* Train Set Accuracy = 0.996
* Validation Accuracy = 0.949
* Test Set Accuracy = 0.931

1. I used softmax to calculate the cross entropy

2. Then I averaged the values of cross entropy

3. After that, I minimized the loss function using "AdamOptimizer", we can also use "Gradien Decent" here

4. I implemented back propergation to minimize the error

5. Then I loop the whole process for Epochs times to maximize my validation accuracy

I got 0.949 accuracy for the validation set, so the model works pretty well.
 

# Test a Model on New Images

## 1. Choose five German traffic signs found on the web and provide them in the report. 

Here are five German traffic signs that I found on the web:

![alt text](https://github.com/evaliu1/CarND-Term1-P2/blob/master/test_Image/test.JPG)

Firstly, I resized all the images to (32*32*3), which is the same size for the training set. Second, I created an 4D array to store my images. Third I changed the colored image to gray, and also normalized the images to fit the training set.

For the "Speed Limit(30)" sign, the Network might recognize it for a different speed limit. And for the "No Passing" sign, it looks pretty similiar to "End of No Passing" sign. 

## 2. Discuss the model's predictions on these new traffic signs
Here are the results of the prediction:
Test Set Accuracy = 1.000

| Image			        |     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| Turn Right ahead     		| Turn Right ahead 									| 
| No Pass    			| No Pass										|
| No Vehicles   | No Vehicles							|
| Keep Left    		| Keep Left			 				|
| Speed Limit(30)		| Speed Limit(30)     				|


The model was able to correctly guess 5 of the 5 traffic signs, which gives an accuracy of 100%. It looks a pretty good result.

## 3. Describe how certain the model is when predicting on each of the five new images 

For the first image, the model is pretty sure that this is a "Turn Right Ahead" which is number 33 (probability of 0.999986), and the image does contain the sign of turn right ahead. The top five soft max probabilities were


* The first guess is sign number: 33 , with a probability of: 0.999986
* The second guess is sign number: 11 , with a probability of: 7.2003e-06
* The third guess is sign number: 25 , with a probability of: 3.18806e-06
* The fourth guess is sign number: 21 , with a probability of: 2.60653e-06
* The fifth guess is sign number: 12 , with a probability of: 9.4626e-07

For the second image, the model is pretty sure that this is a "No Passing" which is number 9 (probability of 0.999958). The top five soft max probabilities were

* The first guess is sign number: 9 , with a probability of: 0.999958
* The second guess is sign number: 41 , with a probability of: 3.95769e-05
* The third guess is sign number: 12 , with a probability of: 1.36729e-06
* The fourth guess is sign number: 10 , with a probability of: 8.49452e-07
* The fifth guess is sign number: 13 , with a probability of: 1.45176e-07
-----------------------------------------------

For the third image, the model is pretty sure that this is a "No Vehicles" which is number 15 (probability of 0.998548). The top five soft max probabilities were

* The first guess is sign number: 15 , with a probability of: 0.998548
* The second guess is sign number: 12 , with a probability of: 0.00127293
* The third guess is sign number: 8 , with a probability of: 0.000139539
* The fourth guess is sign number: 9 , with a probability of: 3.26851e-05
* The fifth guess is sign number: 13 , with a probability of: 5.85101e-06
-----------------------------------------------

For the fourth image, the model is pretty sure that this is a "Keep Left" sign which is number 39 (probability of 0.99997). The top five soft max probabilities were

* The first guess is sign number: 39 , with a probability of: 0.99997
* The second guess is sign number: 31 , with a probability of: 2.87708e-05
* The third guess is sign number: 19 , with a probability of: 8.52219e-07
* The fourth guess is sign number: 21 , with a probability of: 2.85445e-07
* The fifth guess is sign number: 4 , with a probability of: 2.19135e-08
-----------------------------------------------

For the fifth image, the model is pretty sure that this is a "Speed Limit(30)" sign which is number 1 (probability of 0.999977). The top five soft max probabilities were

* The first guess is sign number: 1 , with a probability of: 0.999977
* The second guess is sign number: 0 , with a probability of: 2.35195e-05
* The third guess is sign number: 2 , with a probability of: 4.00764e-08
* The fourth guess is sign number: 38 , with a probability of: 1.40795e-12
* The fifth guess is sign number: 14 , with a probability of: 1.31987e-13
-----------------------------------------------

