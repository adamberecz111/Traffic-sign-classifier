#### 1. Provide a basic summary of the data set. In the code, the analysis should be done using python, numpy and/or pandas methods rather than hardcoding results manually.

calculated:
Number of training examples = 34799
Number of testing examples = 12630
Image data shape = (32, 32, 3)
Number of classes = 43

#### 2. Include an exploratory visualization of the dataset.

made a graph containing the cunt of the different types of traffic signs in the training set, validation set, test set

#### 1. Describe how you preprocessed the image data. What techniques were chosen and why did you choose these techniques? Consider including images showing the output of each preprocessing technique. Pre-processing refers to techniques such as converting to grayscale, normalization, etc. 

Preprocessing wasn't necessary because the model gave prett high result scores anyway.
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

I just picked random values...
rate = 0.001
EPOCHS = 100
BATCH_SIZE=128
mu = 0
sigma = 0.1

### Test a Model on New Images

Here are the results of the prediction:

| Image			        |     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 50 km/h      		    | Speed limit (80km/h)   									| 
| keep left     		| Keep left 										|
| stop					| No entry											|
| yield	      		    | Yield					 				|
| No passing			| No passing      							|


in the 2nd and 4th picture the model was 100% sure = [1.00000000e+00,0.00000000e+00,0.00000000e+00,0.00000000e+00,0.00000000e+00],

image 1
| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 1.00000000e+00         			| Speed limit (80km/h)   									| 
| 1.62016706e-10     				| Speed limit (30km/h) 										|
| 6.37421919e-13					| Speed limit (50km/h)											|
| 4.38868302e-14	      			| Speed limit (60km/h)					 				|
| 1.07110196e-14				    | Speed limit (100km/h)      							|
image 3
| Probability         	|     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 1.00000000e+00         			| No entry   									| 
| 4.09353454e-22     				| Stop 										|
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