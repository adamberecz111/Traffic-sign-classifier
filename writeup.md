#### 1. Provide a basic summary of the data set. In the code, the analysis should be done using python, numpy and/or pandas methods rather than hardcoding results manually.

calculated:
Number of training examples = 34799
Number of testing examples = 12630
Image data shape = (32, 32, 3)
Number of classes = 43

#### 2. Include an exploratory visualization of the dataset.

made a graph containing the count of the different types of traffic signs in the training set, validation set, test set

#### 1. Describe how you preprocessed the image data. What techniques were chosen and why did you choose these techniques? Consider including images showing the output of each preprocessing technique. Pre-processing refers to techniques such as converting to grayscale, normalization, etc. 

I Normalized the images like: (pixel - 128)/ 128
validation acc = 0.955
test acc = 0.946

#### 2. Describe what your final model architecture looks like including model type, layers, layer sizes, connectivity, etc.) Consider including a diagram and/or table describing the final model.

My final model consisted of the following layers:

| Layer         		|     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
| Input         		| 32x32x3 RGB image   							| 
| Convolution 3x3     	| 1x1 stride, same padding, outputs 32x32x32 	|
| RELU					|												|
| Max pooling	      	| 2x2 stride,  outputs 16x16x32 				|
| Convolution 3x3	    | etc.      									|
| Convolution 3x3     	| 1x1 stride, same padding, outputs 32x32x64 	|
| RELU					|												|
| Max pooling	      	| 2x2 stride,  outputs 16x16x64 				|
| Convolution 3x3	    | etc.      									|
| Convolution 3x3     	| 1x1 stride, same padding, outputs 32x32x128 	|
| RELU					|												|
| Max pooling	      	| 2x2 stride,  outputs 16x16x128 				|
| Fully connected		| size:512        								|
| RELU				    |									            |
| Fully connected		| size:128        								|
| RELU				    |									            |

#### 3. Describe how you trained your model. The discussion can include the type of optimizer, the batch size, number of epochs and any hyperparameters such as learning rate.

I started with LeNet but the accuracy was low so I added a few layers and still it didn't reach the required accuracy so I thought ok I'm just gonna increase the epochs, and that worked. After that I deleted some of the layers to check if a smaller network would be successful with a large epoch value but I didn't want to use completely the same architecture than LeNet so I left one plus convolution layer in. 
rate = 0.001
EPOCHS = 100
BATCH_SIZE=128
mu = 0
sigma = 0.1

### Test a Model on New Images

It's hard for the model to detect the numbers on the speed limit signs which is understandable because it actually looks confusing in the low res test image. Otherwise based on these few test images I can't identify any particular qulaity that would be hard for the model to detect except maybe if there were multiple signs on the image, which is I think souldn't be happening in the first place because if that were the case than the image would need preprocessing first probably to separate the signs.

Based on this few example the model successfully recognized 4 out of 5 custom images which is about 80% so it has worse performance then in the test image set.

In the cases of the custom images the model was always very sure.

Here are the results of the prediction of the custom images:

| Image			        |     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 50 km/h      		    | Speed limit (20km/h)   									| 
| keep left     		| Keep left 										|
| stop					| stop											|
| yield	      		    | Yield					 				|
| No passing			| No passing      							|


in the 2nd and 4th picture the model was 100% sure = [1.00000000e+00,0.00000000e+00,0.00000000e+00,0.00000000e+00,0.00000000e+00],

image 1
| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 1.00000000e+00         			| Speed limit (20km/h)   									| 
| 1.62016706e-10     				| Speed limit (30km/h) 										|
| 6.37421919e-13					| Speed limit (50km/h)											|
| 4.38868302e-14	      			| Speed limit (60km/h)					 				|
| 1.07110196e-14				    | Speed limit (100km/h)      							|
image 3
| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 1.00000000e+00         			| Stop   									| 
| 4.09353454e-22     				| No entry 										|
| 7.51821618e-25					| Yield											|
| 1.48684212e-33	      			| Speed limit (20km/h)					 				|
| 1.85892941e-34				    | Bicycles crossing      							|
image 5
| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 1.00000000e+00         			| No passing   									| 
| 1.04289418e-15     				| End of all speed and passing limits 										|
| 7.66437074e-16					| No entry											|
| 4.18802759e-19	      			| Children crossing					 				|
| 2.09459886e-20				    | Speed limit (60km/h)      							|