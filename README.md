#Image Classification
Build a Traffic Sign Recognition Project

The goals / steps of this project are the following:

Load the data set (see below for links to the project data set)
Explore, summarize and visualize the data set
Design, train and test a model architecture
Use the model to make predictions on new images
Analyze the softmax probabilities of the new images
Summarize the results with a written report

###Writeup / README

####1. Provide a Writeup / README that includes all the rubric points and how you addressed each one. You can submit your writeup as markdown or pdf. You can use this template as a guide for writing the report. The submission includes the project code.

You're reading it! and here is a link to my project code

###Data Set Summary & Exploration

####1. Provide a basic summary of the data set. In the code, the analysis should be done using python, numpy and/or pandas methods rather than hardcoding results manually.

I used the numpy library to calculate summary statistics of the traffic signs data set:

The size of training set is 34799
The size of the validation set is 4410
The size of test set is 12630
The shape of a traffic sign image is 32 X 32 X 3
The number of unique classes/labels in the data set is 43

###Design and Test a Model Architecture

####1. Describe how you preprocessed the image data. What techniques were chosen and why did you choose these techniques? Consider including images showing the output of each preprocessing technique. Pre-processing refers to techniques such as converting to grayscale, normalization, etc. (OPTIONAL: As described in the "Stand Out Suggestions" part of the rubric, if you generated additional data for training, describe why you decided to generate additional data, how you generated the data, and provide example images of the additional data. Then describe the characteristics of the augmented training set like number of images in the set, number of images for each class, etc.)

As a first step, I decided to convert the images to grayscale because it reduces the impact of Noise. The python note book has images
related to color and gray images

I normalized the images by diving each pixel value by 127 so that each pixel value is between 0 and 2

####2. Describe what your final model architecture looks like including model type, layers, layer sizes, connectivity, etc.) Consider including a diagram and/or table describing the final model.

My final model consisted of the following layers:

Layer	Description
Input	32x32x1 Gray image
Convolution 5x5	1x1 stride, valid padding, outputs 28x28x6
RELU	
Max pooling	2x2 stride, outputs 14x14x6
Convolution 5x5	1x1 stride , valid padding, outputs 10x10x16
RELU
Max Pooling 2x2 stride outputs 5x5x16
FLATTEN to 400 units
FLATTEN to 120 units
RELU
Flatten to 84 units
RELU
Flatten to 43 units

####3. Describe how you trained your model. The discussion can include the type of optimizer, the batch size, number of epochs and any hyperparameters such as learning rate.

To train the model, I used an adam's optimizer. I finally concluded to a batch size of 32 and epochs as 25 with a learning rate of 0.01. 

After trying the above changes,  validation accuracy of 93 % being acheived. 


####4. Describe the approach taken for finding a solution and getting the validation set accuracy to be at least 0.93. Include in the discussion the results on the training, validation and test sets and where in the code these were calculated. Your approach may have been an iterative process, in which case, outline the steps you took to get to the final solution and why you chose those steps. Perhaps your solution involved an already well known implementation or architecture. In this case, discuss why you think the architecture is suitable for the current problem.

I started my model by taking the La-Net architecture. Below are the things which were tried by me

a) Addition of extra conv layer
b) Deletion of extra conv layer
c) Increasing the filter size and decreasing the filter size
d) Increasing and decreasing the max pool stride size
e) Increasing/decreasing the number of flat layers
f) Adding drop outs to reduce over fitting
h) Manipulating the images by skimage exposure gamma transform, log transform and sigmoid transforms
i) Reducing Batch sizes
j) Increasing/Decreasing Epoch.

After tuning of the above points, I finally found the validation accuracy of 93%

training set accuracy of 99.3%
validation set accuracy of 93.5%



###Test a Model on New Images

####1. Choose five German traffic signs found on the web and provide them in the report. For each image, discuss what quality or qualities might be difficult to classify.

I imported 5 new images from web. The accuracy was 100%. The new images have been printed 
in python notebook. The one common difficulty in classifying new images was when the image was resized to 32x32, the resize was causing a lot of distortion. To overcome this, I manually had to crop the images into square so that the distortions could be reduced. After this was done, the accuracy was increased to 1.000. Before this was done, the accuracy was at 0.2.

####2. Discuss the model's predictions on these new traffic signs and compare the results to predicting on the test set. At a minimum, discuss what the predictions were, the accuracy on these new predictions, and compare the accuracy to the accuracy on the test set (OPTIONAL: Discuss the results in more detail as described in the "Stand Out Suggestions" part of the rubric).

Here are the results of the prediction:

Image	                                                                Prediction
Speed limit (30km/h)                                                   Speed limit (30km/h)
Speed limit (50km/h)                                                   Speed limit (50km/h)
Stop                                                                    Stop
Yield                                                                   Yield
Keep right                                                              Keep right
The model was able to correctly guess 5 of the 5 traffic signs, which gives an accuracy of 100%. 

####3. Describe how certain the model is when predicting on each of the five new images by looking at the softmax probabilities for each prediction. Provide the top 5 softmax probabilities for each image along with the sign type of each probability. (OPTIONAL: as described in the "Stand Out Suggestions" part of the rubric, visualizations can also be provided such as bar charts)

The code for making predictions on my final model is located in the IN[186]
