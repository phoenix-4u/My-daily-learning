# Day 78 - 05/06/2026
## Statistics tidbits
- Probability mass function (discrete) has to always sum to 1, but probability density function (continuous) can sum to more than one. The reason is that for discrete events, there is always a probability assigned at a point, but the probability of a point for a continuous function is very close to 0.
- For discrete events, variance is finite, but for continuous events, the sum can be infinite.
- There are 3 types of distributions
  1. Data Generating - The real-world events that generate a distribution
  2. Empirical - The data that we measure in the real world
  3. Model - Based on the data collected, predict the data
- Sampling example includes any real-world event, such as hitting a key while typing or clicking a picture to take a snapshot in time.
- Samples are always Biased, while sampling is not. For example, if we repeat the process of a fair coin toss over and over again, the chance of getting exactly 50% for each experiment is 0
- Labelling data is the process of associating a meaning with the data

# Day 77 - 04/06/2026
## Torch vision models
- Many default models are available in PyTorch that are pretrained
- Various architectures like Google Net, ResNet 50, and so on
- Pretrained models need to be put in the eval model, and then input batches should be fed for prediction
- The prediction is in terms of logits, which is converted to probability with softmax
- then top_k is used to choose the top probabilistic classes.
- The output classes can be either fetched from a JSON mapping or from class metadata
- The class metadata can be used to load an empty model and then use the latest weights

# Day 76 - 03/06/2026
## Torch distribution
- We can define various distributions using the `torch.distribution` module
- These can include Bernoulli, normal, and so on.
- It is important to remember that even when we specify 1000s of samples, the value of the mean and variance (in case of normal distribution) will never be equal to the specified value. It will always have slight randomness

# Day 75 - 02/06/2026
## Torch vision dataset
- We can load a prebuilt dataset like CIFAR10, MNIST, and so on
- The Loading mechanism differs from dataset to dataset
- For custom data loading, the images need to be segregated into their own class folder.
- If a validation test set is provided, then it also needs to be segregated.
- <img width="802" height="302" alt="image" src="https://github.com/user-attachments/assets/b7065c0c-eae7-488c-a5e1-4c3c25c94385" />
- The Fake dataset creates a random dataset based on channels and pixel configurations

# Day 75 - 01/06/2026
## Torch vision modules - Transforms pipelines and Augmentation
- The compose method can be used to construct a custom pipeline.
- Image augmentation is necessary for creating additional sample data points.
- Random resized crop can randomly crop the image to a specified size
- Random Horizontal flip can flip the image based on a probability
- Color jitter can randomly increase brightness and contrast
- Custom classes (such as adding salt and pepper noise or adding Gaussian noise) can also be applied to the pipeline

# Day 74 - 31/05/2026
## Torch vision modules - Transforms
- ToTensor transforms a PIL image to a tensor
- <img width="697" height="333" alt="image" src="https://github.com/user-attachments/assets/22dcf932-b897-494a-954b-730742f2f598" />
- ToPILImage transforms an image back to a tensor
- <img width="753" height="189" alt="image" src="https://github.com/user-attachments/assets/f1d6c28d-7159-4884-b46a-c6f37cf877ff" />
- Resize scales down the original image to the resized image (2048*2048) to (50*50)
- <img width="567" height="168" alt="image" src="https://github.com/user-attachments/assets/fb9b3c52-fcf4-473c-87df-95626ac2e5b7" />
- Centercrop crops the center of the image to the desired pixel size.
- <img width="683" height="159" alt="image" src="https://github.com/user-attachments/assets/13a4907c-571a-4272-a856-89fdbe8c8e5a" />
- Transform normalizes an image to a 0 mean and unit standard deviation.
- The values for the mean and standard deviation are derived from values of a much larger dataset.
- <img width="573" height="71" alt="image" src="https://github.com/user-attachments/assets/b3dbf59a-d54e-4d49-bbb2-a1ccfa4bea61" />


# Day 73 - 30/05/2026
## Torch vision modules
- There are 4 main fundamental modules within Torch Vision. These include:
  1. Transforms - This contains predefined libraries for image processing (cropping/flipping/rotating/resizing, etc.)
  2. Utility function - These contain various functions such as decode_images to tensor, save_images, make_grid, etc.
  3. Datasets - These contain all predefined datasets commonly used for machine learning
  4. Models - Predefined architecture or pretrained models such as ResNet50

# Day 72 - 29/05/2026
## Optimizing Model efficiency
- Apart from accuracy (Or F1 scores), other constraints like model size and inference time also determine model applicability based on the situation
- To get the model size, we have to sum up all elements within all parameters and multiply by the parameter size
- <img width="917" height="443" alt="image" src="https://github.com/user-attachments/assets/d5fb9f97-0003-4b65-92c0-279e433abef1" />
- For evaluating inference time, we have to run multiple iterations for time evaluations and then take the average
- <img width="946" height="467" alt="image" src="https://github.com/user-attachments/assets/fc9fb989-d18c-48bc-9a74-253319ed6945" />
- The model can then be selected based on either the constraints or on a weighted-based approach.
- For a weighted-based approach, the metrics first need to be normalized, and then the weights should be calculated
- <img width="1126" height="443" alt="image" src="https://github.com/user-attachments/assets/425fff69-47d3-4db1-b09f-44dbaacedd13" />

# Day 71 - 28/05/2026
## Hyperparameter optimisation with Optuna
- It is very difficult to search for the best combination of hyperparameters iteratively, as that is time-consuming
- Random searches are faster but might not give an optimal solution.
- The best approach is to follow a tree-based search to find the optimal hyperparameter set, which Optuna does
- First, we have to define the search space with a combination of ranges for the hyperparameter search
- <img width="895" height="271" alt="image" src="https://github.com/user-attachments/assets/aa8f0e5b-251c-48bd-be5f-6b605cac3d5f" />
- Then we have to create and run the study
- <img width="909" height="206" alt="image" src="https://github.com/user-attachments/assets/f780dea0-575b-4e37-a07f-2774079dcd4c" />
- Finally, we will have to get the best parameter set
- <img width="563" height="387" alt="image" src="https://github.com/user-attachments/assets/e9ec42b6-0590-4f22-87a6-2090a3f0fed9" />
- Optuna also provides various visualisations which help to understand the best hyperparameter combination.

# Day 70 - 27/05/2026
## Flexible architecture
- A Flexible CNN architecture comprises several components
- <img width="1020" height="481" alt="image" src="https://github.com/user-attachments/assets/5eacb1e2-328d-4a79-a4a5-472b83d8a577" />
1. The number of layers, the number of filters, and the size of the kernel can be dynamically tuned
   <img width="786" height="410" alt="image" src="https://github.com/user-attachments/assets/f0a34ba6-22e2-489f-8494-5d100a9fe693" />
2. Since we do not know the flattened size for the first fully connected layer, we have to determine that in the first pass of the feed-forward method.
   <img width="726" height="350" alt="image" src="https://github.com/user-attachments/assets/cc07b497-0f4d-4e3c-a627-2173927d2cc1" />
3. The dropout rate can be assigned dynamically as a hyperparameter
   <img width="806" height="330" alt="image" src="https://github.com/user-attachments/assets/3a549f47-8942-4e33-8fd8-1d87946b71d7" />
4. The number of nodes in the fully connected layer (denoted by fc_size) is also a hyperparameter

# Day 69 - 26/05/2026
## Hyperparameter tuning
- Architectural
  1. Number of Layers
  2. Number of neurons per layer (including filters, paddings for CNNs)
  3. Activation functions (Relu/Softmax, etc.)
- Training
  1. Learning rate + scheduler (see below)
  2. Optimiser (Gradient Descent/RMS prop/ Adaptive momentum - ADAM, etc.)
  3. Batch Size - A larger batch size means faster learning but requires more memory and runs the risk of overshooting the minima, whereas a smaller batch size is slower but memory efficient and finds the minima
- Regularization
  1. By weight decay (L2 regularisation)
     <img width="1247" height="121" alt="image" src="https://github.com/user-attachments/assets/d4f97671-fc42-4645-8e2b-2cd8bd8c6520" />
  2. By dropouts
     <img width="557" height="58" alt="image" src="https://github.com/user-attachments/assets/a3b2b98c-9397-4852-a5bb-f7b2e67044e1" />
  4. By early stopping
  5. by batch normalisation
     <img width="925" height="65" alt="image" src="https://github.com/user-attachments/assets/0ccc3259-6ea9-43b9-b7e9-4d5a293fbe0c" />

# Day 68 - 25/05/2026
## Learning rate scheduler
- Learning rate schedulers are used to dynamically adjust the learning rate.
- It's done so that the model learns faster during initial epochs and then gradually updates in smaller iterations to improve accuracy and reach global minima
- There are 3 types of LR schedulers available in PyTorch
- Step LR reduces the LR in a fixed epoch interval by a fixed amount
- <img width="1579" height="243" alt="image" src="https://github.com/user-attachments/assets/e37aeca3-c56b-4c5c-bf1a-4d58241e25b8" />
- Reduce LR on Plateau dynamically decides when to reduce the learning rate if the epochs do not improve accuracy
- The monitoring in this case is done on a metric like validation accuracy
- <img width="1520" height="279" alt="image" src="https://github.com/user-attachments/assets/56282046-d02e-4d16-88b6-522ab1c40850" />
- Cosine Annealing LR reduces the learning rate smoothly following a cosine curve, with the number of epochs and the minimum learning rate being the hyperparameters
- <img width="1369" height="269" alt="image" src="https://github.com/user-attachments/assets/c2dbf9da-07f1-424f-bd5c-be90d9f8cc2c" />

# Day 67 - 24/05/2026
## Optimization
- Optimisation in ML means either maximising or minimising hyperparameters
- Maximising hyperparameters includes precision, recall, accuracy, and F1 score
- Minimising hyperparameters includes log loss, mean-squared errors, training time, etc.
- Models can be externally improved by improving the quality of the sample dataset, with more data, and having better feature representation
- Models can be internally improved by tweaking the number of layers, dropouts, and batch sizes

# Day 66 - 23/05/2026
## Evaluation Metrics
- Accuracy is not a good ML metric when there is an imbalanced data set
- Precision measures cases where false positives have more impact (falsely detecting disease and then performing expensive treatment.
- Its formula = `TP/(TP + FP)`
- Recall measures the impact of false negative cases (not being able to detect cancer when he has cancer might mean that the patient might die)
- Its formula is = `TP/(TP+FN)`
- A better metric is the F1 score =`2* ((Precesion*Recall)/(Precision+Recall))`

# Day 65 - 22/05/2026
## Model inspecting and debugging
- Basic model parameters can be just printed using print(model)
- <img width="1008" height="389" alt="image" src="https://github.com/user-attachments/assets/a3f8b84e-6082-40eb-a799-c814baf6fb6a" />
- model.param.shape prints the parameters of each layer
- <img width="388" height="345" alt="image" src="https://github.com/user-attachments/assets/fe8f4d11-181e-4cc5-8434-1c3fef322305" />
- numel provides the total parameter list
- <img width="828" height="270" alt="image" src="https://github.com/user-attachments/assets/a7e49772-75d9-43c3-90b1-fd7717f8bbd4" />
- named parameter provides the name and parameter shape for that layer
- <img width="524" height="382" alt="image" src="https://github.com/user-attachments/assets/dc9b1d1e-0fab-4c9d-97d2-1349b3aad65c" />
- named children provides just the first-level children, whereas module provides the entire hierarchy
- <img width="995" height="215" alt="image" src="https://github.com/user-attachments/assets/e21feb93-6b88-445c-a583-72890fa81886" />

# Day 64 - 21/05/2026
## Modularisation and refactoring
- The ideal scenario, both the approaches (nn.module and nn.sequential) together
- Instead of repeating the same blocks over and over again in the forward method, group them in a sequential module and then just use those blocks in the forward method
- Instead of defining the convolution, relu, and maxpool block, we can define a class encompassing these 3 modules and then define only the class in the init module.
- <img width="922" height="294" alt="image" src="https://github.com/user-attachments/assets/1a49d5e3-0236-4200-8f07-72147760c023" />

# Day 63 - 20/05/2026
## CNN continued
- In the Sequential module, the computation graph is static, thereby not allowing the use of loops, ifs, etc.
- The tradeoff to this is that the sequential neural networks are faster.
- Use nn.module, instead of nn.sequential

# Day 62 - 19/05/2026
## CNN continued
- Generally, classification models have multiple convolutional layers.
- In the fully connected layer, we add a dropout layer so that the model cannot overfit. Randomly, it is set to 20% - 50% (percentage might vary) deactivation
- Weight decay is added to the optimiser to avoid overfitting. They do it by adding a penalty to Large weights for any neuron-to-neuron connection, thereby smoothening the curve
- <img width="1189" height="575" alt="Screenshot 2026-05-21 at 12 09 18 AM" src="https://github.com/user-attachments/assets/05c1e7fc-d902-4604-94d0-42a8d1c1350d" />

# Day 61 - 18/05/2026
## CNN continued
- The init method for a CNN comprises a conv2d layer, followed by RELU, and then by a maxPool2D layer
- The MaxPool2D layer extracts the most important pixel information by applying a filter
- The dimension of the fully connected layer at the end is the number of channels, followed by the reduced dimension of the original pixels because of max pooling
- <img width="944" height="415" alt="image" src="https://github.com/user-attachments/assets/1404ac08-6215-4799-88b6-075e32ba23b9" />

# Day 60 - 17/05/2026
## CNN continued
- In Pytorch, Conv NN is defined by the nn.conv2d module.
- It takes a few inputs
  1. in_channels, which is generally 3 based on RGB
  2. out_channels defines how many filters we want the CNN to use
  3. kernel_size defines the size of the filter matrix. A size of 3 means it's a 3*3 matrix filter, and can focus on the pixel and each of its 8 surrounding neighbouring pixels
  4. Stride defines how the sliding window of the filter moves; a size of 1 means the filter is applied to each pixel
  5. Padding is applied so that the sliding window for filters can scan the corner pixels as well. For example, a kernel size of 5 will mean the padding has to be 2. Gor kernel size of 3, padding is 1.
  - <img width="1808" height="717" alt="image" src="https://github.com/user-attachments/assets/5bc38545-6d38-406b-80f2-a87fc4d4bbdf" />

# Day 59 - 16/05/2026
## CNN
- From individual pixels, it's hard to recognize any patterns.
- Filters in CNN help in identifying patterns in the image.
- These filters are auto-detected by CNNs based on the sample images

# Day 58 - 15/05/2026
## Pipeline Debugging
- To make the transform pipeline more robust, Images can be augmented to enhance training
- Augmentation can be flipping the image, rotating the image, or changing the color/condition of the image.
- The only thing is to ensure that this is not overdone, as then the model will be trained on junk data
- Catching errors and keeping track of them is another important part of a robust pipeline
- Error tracking can be for image corruption, image size, image color, etc.
- Monitoring the errors can help in identifying shuffling bugs (where all the images are not getting loaded because of buggy shuffling), Latency issues, and data imbalance ( 1/ set of images being loaded multiple times)


# Day 57 - 14/05/2026
## Data Loader
- After creating the dataset and the transform pipeline, dataloaders are used to serve the data in batches for training and validation
- First, the train test validation split has to be created, and it is done using a PyTorch module called random_split
- After this, the data loaders are used for loading the data in various batch sizes.
- Generally, a small batch size of 32 epochs is preferred to avoid CUDA/MPS memory failure issues
- If there are 10 batches required to load the entire data set once, and then there are 10 epochs (one pass of the full dataset), then in total there are 100 batches
- The data loader completes the entire epoch. That means if the batch size is 32 and at last there are 4 samples left, the last batch will be of size 4
- For train dataloaders, shuffle = true needs to be mandatorily set. For training and validation, it's optional as the model is then in an eval mode.
- Loading of data should always be done in __init__ and never in __getitem__
- <img width="981" height="600" alt="Screenshot 2026-05-15 at 12 42 25 AM" src="https://github.com/user-attachments/assets/8cdeb422-f9c6-4546-88c3-d276e9099362" />

# Day 56 - 13/05/2026
## Transform Pipelines
- After the data set class is created, we need a transformation pipeline to properly format the data
- The transforms module for image data formatting has various steps
- It starts with the resize component, which resizes the image to the desired pixel value on the shorter side
- Crop center will then just get the center of the image, thereby creating a square image
- To Tensor will transform the image to a Tensor
- Normalize will scale the tensors between 0 and 1 and then center the value using mean and standard deviation
- Ultimately, it can be added to the Dataset's __init__ method as self.transform and then used in the __getitem__ method to return the transformed image.
- <img width="1097" height="346" alt="Screenshot 2026-05-15 at 12 02 17 AM" src="https://github.com/user-attachments/assets/a48e5547-a7e4-4f6a-93c3-0ba29479299c" />

# Day 55 - 12/05/2026
## How to build a custom dataset in Pytorch
- Custom dataset classes inherit the Dataset superclass
- It mandatorily has to implement 3 dunder methods: __init__, __len__, __getitem__
- __init__ is used for lazy initialization, so that data is loaded when necessary.
- This is just defined to provide the paths of where the data is available
- <img width="1004" height="296" alt="image" src="https://github.com/user-attachments/assets/171db8ee-ac79-4189-b56f-102cc55d6dab" />
- __len__ method just gets the length of all data samples in the dataset
- <img width="1001" height="178" alt="image" src="https://github.com/user-attachments/assets/f201d0c0-fdb5-409f-ab6c-5b15e3599305" />
- __getitem__ gets a specific data sample based on the index and returns it with the corresponding label
- <img width="1015" height="443" alt="image" src="https://github.com/user-attachments/assets/86c3c893-e6d7-49f6-8618-4282326c6a1b" />

# Day 54 - 11/05/2026
## MNIST classification using PyTorch part 2
- Next, check the device to make sure the GPU is available
- Initialize the model and move it to the device. Both the model and the data need to reside on the device
- Define the loss, cross entropy, and optimizer as Adam
- Run training loops for around 10 epochs, where you put the model in the training mode, load the data on the device, clear any gradients, get the output from the data, calculate the loss, and apply the loss to the gradient
- You can calculate the progress and see how the loss is decreasing, and the accuracy is increasing.
-  Testing loop follows the same cycle with the test data, just the model is now set to eval, the loops are run with torch.no_grad and the accuracy is calculated on the unseen data.

# Day 53 - 10/05/2026
## MNIST classification using PyTorch part 1
- For vision models, PyTorch used the torchvision module
- Transforms from torchvision module is used to convert digits to tensors and normalize them using a defined mean and variance.
- MNIST dataset loading is done using the torchvision module
- Data is loaded with dataloader. The train set has shuffle set to true, but the test set is set to False.
- Below is how we can define the classifier class. Flatten is used to convert the channel and pixel values to a flat array
- <img width="516" height="427" alt="image" src="https://github.com/user-attachments/assets/8bcb7781-ee43-48c3-9be6-60b2cec990a1" />


# Day 52 - 09/05/2026
## Loading on Device
- PyTorch by default uses CPU unless a GPU is specified.
- The availability of CUDA or MPS can be tested with the code below
- ```python
  import torch
  print(torch.mps.is_available())
  ```
- Both the model weights and training data need to be shifted to the device
- The method `.to(device)` is not inplace. Therefore, it always needs to be assigned to a variable
- Batch size should be carefully considered so that we don't end up getting CUDA/MPS OOM errors.
- The entire revised workflow looks like this:
- <img width="910" height="393" alt="Screenshot 2026-05-10 at 11 29 54 PM" src="https://github.com/user-attachments/assets/cc38c346-a29f-4200-9128-a49f148a7eef" />

# Day 51 - 08/05/2026
## Optimizers and Gradients
- `loss.backwards()` calculate the gradients, which is how much each weight should change to have a minimal loss.
- Generally, SGD and Adam are used as optimizers
- Learning rate defines the step size
- The actual update is done by `optimizer.step()`.
- `optimizer.zero_grad()` clears all gradient calculations at the start of each epoch

# Day 50 - 07/05/2026
## Types of Loss
- MSE Loss used for linear regression models
- <img width="304" height="137" alt="image" src="https://github.com/user-attachments/assets/615527bb-9534-4add-ab5b-eb35b78ce3bf" />
- Cross-Entropy Loss is a soft loss for Logistic Regression models
- <img width="1014" height="327" alt="image" src="https://github.com/user-attachments/assets/cd1d7c9a-4f90-495d-bc1b-f1f3682d4f43" />
- MSE and cross-entropy loss should not be used interchangeably
- There are various types of loss functions as given below
- <img width="1005" height="319" alt="image" src="https://github.com/user-attachments/assets/f8e13e0c-ec65-4aac-8377-ccfa081e21b3" />

# Day 49 - 06/05/2026
## Model definition pipeline in PyTorch
- Rather than defining a neural network model using sequential, the better practice is to use a class that inherits nn.Module
- This class mandatorily defines 1 constructor and the forward method
- The constructor calls super to inherit the tracking mechanism from the superclass and defines the layers
- The forward method orchestrates the layers by combining them one after the other
- The forward method does not need to be called explicitly; PyTorch calls it automatically
- The training always follows a defined pattern of
  1. Looping over the data in epochs
  2. Setting the optimizer to zero grad.
  3. Forward pass by calling the model with the epoch data.
  4. Calculating the backward pass and backpropagation losses based on model output and the true label
  5. Applying the back propagation losses
  6. Taking the next step by calling optimizer.step()
- For evaluation, model.eval() is setfollowed by torch.no_grad(), so that no further gradient is calculated.
- Test data calculates the actual accuracy of the model
- If the model needs to be retrained, the model needs to be put into training mode by calling model.train()

# Day 48 - 05/05/2026
## Data Preprocessing in PyTorch
- Pytorch has a standard way to handle data
- If the data is numeric, generally, the data is first transformed into a tensor, and then it is normalized
- <img width="1011" height="335" alt="image" src="https://github.com/user-attachments/assets/0b9f1725-b538-49a9-9793-4f103237531e" />
- This is followed by the data load, where the transformation is applied
- <img width="1013" height="97" alt="image" src="https://github.com/user-attachments/assets/629cabdd-dd83-4abb-8c9f-7ad75a138097" />
- Finally, the data loader is used on the dataset to complete preprocessing
- <img width="1005" height="82" alt="image" src="https://github.com/user-attachments/assets/5008871b-4000-4684-a1e8-ce2dd6d05e4f" />
- The entire pipeline looks something like this
- <img width="1005" height="356" alt="image" src="https://github.com/user-attachments/assets/66cc941b-d37f-4098-b46e-c2d060a821c8" />

# Day 47 - 04/05/2026
## Math behind tensors
- Scalars are applied element-wise on a tensor. Hence, 2 * [[1],[2],[3]] becomes [[2],[4],[6]]
- This is done by broadcasting a scalar to match the dimension of the tensor.
- Broadcasting can also be applied to tensors where [[1],[2]] + [[2]] is automatically extended to [[1],[2]] + [[2],[2]] to give [[3],[4]]
- Broadcasting also works on multi-dimensional tensor shapes of (1,2) + (2,1), which is first converted into (2,2) + (2,2) by repeating the values and then adding them

# Day 46 - 03/05/2026
## System Design: Twitter
- Start with the client, Web, and mobile apps
- LoadBalancer: Keep it simple with round robin and the OSI layer 7, i.e., application
- Load balancer routes the traffic to API gateways, which are responsible for executing the functional requirements
- These services will primarily include
  1. TWEET CRUD service: Create, edit, and delete tweets, likes, and retweets, as well as store metadata. It should have a high throughput. For this, the primary database would be a NoSQL database, as it scales very fast, and there are no complex joins on tweets. Also, since tweets are more like a JSON structure, it is a good choice. The media should be stored in a blob storage and use a CDN for content delivery, and Redis should be used for read cache. We should add a rate limiter so that bots cannot flood the system.
  2. Reply, retweet CRUD: Similar to Tweet CRUD, just indexed by tweetID for a snappier reply
  3. Tweet Search: Reverse index on Tweet content, username, and hashtags. We can use Elastic Search as it has the capability of full-text search. Change Data Capture (CDC) will be used to update the Elastic Search index.
  4. Timeline Service: We can use Fanout on the write strategy, as when every tweet is written, it will be put in a message queue. The MQ will then call the consumer worker, who will create the timeline cache for each follower of that tweet. For hot content (celebrity tweet), we will need to have a hybrid approach with Fanout on the read approach, where the content is only pulled when the user logs in.
  5. Profile Service: User creation and deletion will be a SQL DB as the data is structured. For followers structuring, an agraph DB makes more sense, as it allows accurate relationships to be established.
  6. Auth and Security: Authentication and authorization, data encryption via HTTPS, rate limiting for DDOS attack by limiting IP address-related requests and input validation both on client and server.
  7. Monitoring:- Healthchecks via Prometheus and Grafana. ELK (Elastic search log stash in Kibana). Alert manager/ pager duty with Grafana
  8. Load testing, automated testing with GHA pipelines, and backup and recovery.

# Day 45 - 02/05/2026
## Tensor
- Tensor.shape returns the tensor size. For example, a tensor.size(6,1) means there are 6 samples(rows) and 1 feature(column)
- When building neural networks, such as ```model = nn.linear(1,3)```, passing the above tensor works because by default the 1st dimension of any tensor is expected to be the number of samples
- PyTorch itself infers data types; however, the explicit dtype can be set using the dtype parameter.
- PyTorch handles type promotion while mixing dtypes automatically
- Tensors can be created from lists and numpy arrays. numpy and tensor share memory space, so changing one changes the other as well.
- torch.zeros, torch.ones, torch.rand works similarly to numpy.
- To convert a scalar to a tensor to add a dimension (there should be a minimum of 2 dimensions), the unsqueeze method can be used
- Squeeze does the opposite, it reduces the dimension, when the dimension is 1
- Slicing works in a similar way as it does in Python.
- To convert tensors to Python, the item method can be used. It can work only on a tensor with exactly 1 element
 
# Day 44 - 01/05/2026
## Activation Function
- A linear function cannot model complex curved data patterns
- Even after adding multiple neurons, it will still be a linear combination and cannot mimic nonlinear patterns
- Activation functions help here as they convert a linear combination of each weight and bias to a nonlinear function
- ReLU (Rectified Linear Unit) is the most common activation function, which is max(0, linear function).
- Sigmoid, Leaky Relu, Tanh, etc., are common alternatives
- Below is the way PyTorch implements this
- <img width="921" height="441" alt="image" src="https://github.com/user-attachments/assets/3ef7647a-e51e-4dfd-9666-cd16a06aa570" />
- This is similar to the way RBF kernels work. RBF works on the similarity of Gaussian functions to approximate the curve, the activation function does it by turning a linear function into a non-linear function, and then combines the outputs of each neuron to approximate a complex curve.
- <img width="1097" height="630" alt="image" src="https://github.com/user-attachments/assets/06d337a2-23ce-4686-820f-cdbbf95ec5c7" />

# Day 43 - 30/04/2026
## Building a Neural network with pytorch
- 3 essential components that have to be imported - torch for core functionality, torch.nn for building a neural network, and torch.optim for importing various optimizers
- To create features that an NN can consume in PyTorch, they are converted to tensors
- Each tensor consists of a batch (outer bracket) and each batch consists of samples (inner bracket)
- <img width="830" height="162" alt="image" src="https://github.com/user-attachments/assets/25c01e8c-369d-4998-aa16-83102e35757e" />
- Then the model is defined, and here the number of input and output nodes is also provided
- <img width="451" height="71" alt="image" src="https://github.com/user-attachments/assets/3daffde8-4ba1-49ff-9e57-a2fa657d9366" />
- Then the loss function and optimizer are defined
- <img width="578" height="81" alt="image" src="https://github.com/user-attachments/assets/f518dd00-4283-4ff7-97ad-2c346b62bc8a" />
- The entire training is done in a loop with multiple epochs
- <img width="609" height="301" alt="image" src="https://github.com/user-attachments/assets/5e0fb109-3e2b-46fa-9ca6-f6a847afd203" />
- An epoch is an entire pass of the given data once. Like this, multiple passes of the same data constitute multiple epochs
- Finally, the trained model is used for inference. The no grad specifies that the model is being used for inference and no longer for training.
- <img width="1009" height="133" alt="image" src="https://github.com/user-attachments/assets/3055562c-ced8-400d-875d-2f192c5ea86a" />

# Day 42 - 29/04/2026
## Message Queues
- A message queue is a link between a producer and a consumer. This temporarily holds messages/instructions that the producer sends and forgets, and consumers pull and process at their own pace.
- Analogy is where waiters place the order on the rails for the chefs to pick up. Queues are only necessary when the process is not synchronous.
- Properties of an MQ
  1. It has to send an acknowledgement that it has processed a message. Until the ack is sent, the message sits in the queue, so that in the event of failure, the message can be processed by another worker.
  2. This creates another issue of how the other worker knows that a worker is working on the message in the first place. There are many ways to do it: by providing a timeout for ack, by making the message invisible until ack is received, by having each partition block one consumer, etc.
  3. There might be issues that, before sending an ack, the worker crashes, but the message has actually been processed. In that case, there are 3 ways to deal with it
     i. At least once - Default strategy. The message will be delivered at least once, but the logic has to ensure that the transaction is idempotent so that there is no duplicate charge
     ii. At most once - that means the message will be deleted immediately after the consumption, so it might or might not be processed
     iii. Exactly once - this means that the message will definitely be delivered exactly one time. Extremely difficult to achieve in reality
- When to use a queue
  1. If the work is asynchronous
  2. If there is a burst of traffic
  3. If there is a mismatch between the load for the producer and the consumer
  4. And if reliability is required, so that the queue can hold the messages even if the consumer is down.
- How to handle high message throughput
  1. Create queue partitions - This will ensure that all queues are getting loaded with messages
  2. Create/scale up more consumers - This ensures that as partitions increase, there are more consumers to consume those messages
  3. Consumers should not be more than the number of queue partitions, as more consumers will not have dedicated partitions to pull messages from
  4. The partition key should be chosen based on high cardinality so that messages can be distributed across partitions, and at the same time, this key should also ensure ordering, i.e., if a $100 bill is deposited and a $50 bill is withdrawn, then the transaction should be executed in that order.
- Challenges of a queue
  1. If the producers produce more than consumers can consume, they can either scale the consumers up dynamically using a hyperscaler or provide system down messages using backpressure, or at least provide an alert for someone to take action.
  2. Poison Message - If a message fails to process after multiple retries, then the message should be moved to a dead letter queue (exception queue) for an admin to later come and look at
  3. If the queue itself goes down, then the best thing to do is to use a replica queue(persisted on disk with a configurable retention window), as such, provided by Kafka
- Few examples of MQ - Kafka (the most used), Amazon SQS (simple and easy), RabbitMQ (sophisticated and complex processing)

# Day 41 - 28/04/2026
## Six stages of ML pipeline
<img width="975" height="314" alt="image" src="https://github.com/user-attachments/assets/cc5ec6ec-910c-40f1-8283-ba32628033f8" />
- Data Ingestion: Collecting data to be fed into the model. The data can be of any shape or form
- Data preparation: Preparing the data for the model training. This is the most time-consuming aspect of any ML pipeline and determines whether an ML experience is successful or not
- Model architecture: In this part, the best-fit model is determined based on the available data. Generally, EDA is performed in this stage. In the case of a neural network, factors such as the number of nodes, the number of hidden layers, etc., are decided
- Model training: Once the model architecture is decided, model training starts. Things like hyperparameters, training batches, number of epochs, optimizer, etc., are decided
- Model Evaluation: Once the model training is done, it is tested on unseen data to judge the model's accuracy. This is done with a cross-validation dataset or hold out data set
- Model deployment. Once the model is evaluated to be of a certain Threshold accuracy, the model is deployed as a production pipeline.

# Day 40 - 27/04/2026
## Sharding strategy
- Sharding is the strategy to partition the database into multiple groups to increase scalability
- Sharding can be done based on a shard key. Good strategy for choosing the key is below
- <img width="581" height="330" alt="image" src="https://github.com/user-attachments/assets/fb6ba2b6-efd4-47a4-8e97-642e20fa0aba" />
- Here, cardinality means keys that can split the data into many groups. A contrary example includes any Boolean flag, as it will only split in 2 groups
- Data distribution strategy
  1. Range-based sharding - Divides the shard into a fixed range. Downside includes recency, i.e., all new user activities will hit the latest shard, and other shards will not be utilized that much
  2. Hash-based with consistent hashing:- the partition key is hashed based on the number of shards. Very easy to add a new shard with a consistent Has-ing technique. Put Hashes in a cycle. Default sharding technique.
  3. Directory-based sharding:- Uses a directory to map the shard. Good for Celebrity shards, but includes one extra hop, decreasing performance
- Challenges
  1. Celebrity Shards/Hotspots: One shard is hot for a particular reason: Can be handled either by directory sharding or by a compound shard key
  2. Cross-Shard operation: A query hitting multiple shards. Can be mitigated to an extent by adding a cache or by duplicating frequently used data across shards (The second approach is bad as this introduces a writing operation)
  3. Consistency:- Atomic operation might be a challenge as an operation across multiple shards. This can be mitigated by attaching a compensating operation (saga pattern) to the first transaction. So if the second transaction fails, the first transaction is undone.
  - 140 TB, 50K writes per second, etc., needs to be sharded
  - Below are the cases when sharding is necessary
  - <img width="567" height="338" alt="image" src="https://github.com/user-attachments/assets/134f5b43-44a6-4d48-b458-f530c7e57cd1" />


# Day 39 - 26/04/2026
## Caching strategy
- Caching is a strategy to store the most frequently accessed data in a place that can be served the quickest.
- There are 4 places that a cache can be placed
  1. **External Caching** - The Cache in this case is stored outside the server as a dedicated server like Redis. It suffers from network hops, but if there are multiple application servers, all can get help from having a single cache
  2. **In-Process / Internal Caching** - This Caching strategy utilises the app server's own memory to store the cache. This is the fastest, but if there are multiple servers, each server would need to store its own copy of the same cache.
  3. **Content Delivery Network** - This is mostly used for files, images, and video when they have to be distributed across the world. This provides low latency.
  4. **Client-side caching** - In the form of browser cookies and app memory, to deliver similar information quickly
- There are 4 types of **cache Architectures**:
  1. **Cache aside** - Most common and most used, in this strategy, the application server first searches the data in the cache, and if there is a cache miss goes and searches the data in the DB and stores a copy in the cache
  2. **Write through Caching** - The logic is to first write to the DB and then sync with the database. Extremely hard to do this in practice for distributed databases.
  3. **Write Behind Caching** - In this case, the write is to the cache and the read is from the same cache, while the database is updated in batches asynchronously. This strategy risks data loss if the cache server crashes.
  4. **Read through caching** - In this case, if there is a cache miss, then the cache server itself fetches the data from the DB without going back to the app server. The downside is that there needs to be special logic implemented at the Cache server to be able to implement this strategy
- There are 4 types of Cache eviction policies:
  1. **Least recently used** - Generally, the default
  2. **Least frequently used** - prioritises frequency of access over recency. Useful in scenarios where access patterns are highly skewed
  3. **FIFO** - Simple and the most ineffective
  4. **Time to live** - Great for data that can go stale, like API responses
- Common Caching Issues:
  1. **Cache stampede** - If a very high-frequency cache item is out of cache because of TTL, thousands of transactions can hit the DB at the same time, causing the DB to crash. Mitigated by either implementing a first transaction fetch cache, rest wait policy, or refreshing the high-frequency cache item proactively before its TTL expires
  2. **Cache consistency** - Since writes are to the DB and reads are from the cache, the users can read the old cache even though new information (like profile picture) has been updated in the DB. This can be mitigated either by waiting out the TTL or by implementing an invalidate cache on write policy, whereby a new cache has to be read when there is a corresponding write.
  3. **Hot Keys** - If a particular cache item is used many times more times than other items, then it can cause failure due to load. This can be mitigated by sharding that item to multiple cache nodes or by implementing the internal caching mechanism in each app server.
- What are the uses ofses of caching
  1. **Read heavy workloads**
  2. **Expensive queries**
  3. **High CPU utilisation of the database**
  4. **Low latency requirements**.

# Day 38 - 25/04/2026
## Single Neuron
- A single Neuron is initialised randomly.
- Then, its weight and bias terms are adjusted based on the activation function
- If the number of features increases, then the weight matrix also keeps on increasing.
- Finally, based on differentiation, the weights and bias are adjusted.
- <img width="1893" height="800" alt="image" src="https://github.com/user-attachments/assets/e4e17007-8212-478d-b1a8-a0e22b21a23d" />
- <img width="1782" height="876" alt="image" src="https://github.com/user-attachments/assets/c886aa0d-b67d-43ca-9988-5d84fdf8553d" />

# Day 37 - 24/04/2026
## Pytorch utility
- Before PyTorch, a simple addition of 2 numbers required 5 lines of code
- This is because early frameworks depended on a static computation graph that compiled the code before runs, resulting in it being static and not changeable during runtime
- This structure also made it impossible to debug the code line by line, and errors were cryptic rather than pointing to a specific code problem
- Pytorch solved all of these issues.

# Day 36 - 23/04/2026
## Mixture of Experts
- An agent is a control flow operator that repeats in a loop until the condition for the loop is met.
- It has an LLM that is guided by the prompt, keeps track of the user conversation and decides on what action to take based on the available tools
- There is a switch that performs an action and a memory that is shared by the LLM and all tools
- Below are the pros and cons of a single-agent system
- <img width="999" height="488" alt="image" src="https://github.com/user-attachments/assets/f2d79635-96ff-4ee0-99b2-8f78c1531210" />


# Day 35 - 22/04/2026
## Mixture of Experts
- A mixture of experts model is when you have multiple blocks of feedforward layers, and only some of them are activated at a time
- In the input block of a transformer, there is an attention block and a feedforward block that any token has to pass through for next word prediction
- In the case of MoE, these feedforward blocks are duplicated for various kinds of next-word prediction.
- To choose experts, a router will be activated.
- When a new token comes, the router maps the top k feedforward blocks and ignores the rest.
- That way, only a few billion parameters from the expert are activated at any time.
- <img width="620" height="537" alt="Screenshot 2026-04-22 at 11 53 36 PM" src="https://github.com/user-attachments/assets/cded58aa-e0f9-4490-a3a8-b07b623b95d2" />


# Day 34 - 21/04/2026
## Relational tables vs a knowledge graph
- Relational tables are great for storing structured data, but fall short when there are questions connecting back to the same entity via a relationship
- <img width="1252" height="620" alt="Screenshot 2026-04-21 at 11 45 09 PM" src="https://github.com/user-attachments/assets/b574b96f-23fe-4d02-8a93-6565afaf7a2b" />
- Knowledge graphs are a much nicer way to represent such a messy situation
- <img width="1247" height="610" alt="Screenshot 2026-04-21 at 11 47 00 PM" src="https://github.com/user-attachments/assets/605b5dda-0f08-4400-bd6b-4e26c05eb796" />
- The query Language of a knowledge graph is called Cypher
- Since it's very close to natural language, it's easy for LLMs to understand.
- Knowledge graphs are good for both structured and unstructured data.

# Day 33 - 20/04/2026
## Bayes theorem for posterior distribution
- While MLE is good for estimating Parameters based on a given data, it does not incorporate any prior belief
- Bayes Theorem provides a posterior distribution where theta is the variable given the distribution D
- It is given by <img width="753" height="125" alt="image" src="https://github.com/user-attachments/assets/557d6292-3080-4717-a16f-8b6c04fdd392" />
- Often, the denominator is not considered as it is not dependent on theta, and hence it is proportionally computed against the Likelihood and the prior
- Prior and likelihood both can be jointly estimated to get parameters such as mu and sigma for the normal distribution.


# Day 32 - 19/04/2026
## Maximum Likelihood Estimate
- MLE is a way to estimate an unknown parameter based on observed data points.
- The precondition is that we should know what kind of distribution we are drawing the data from.
- Based on the assumption that the samples in the distribution are identically and independently drawn, the MLE takes the form of a product of probabilities of the individual data points.
- Then the job is to maximise the parameter that we are interested in (In a head-tail problem, the parameter is the probability of getting heads, in a Gaussian distribution, it is the mean and variance)
- Maximising the likelihood is the same as maximising the log likelihood, as log is a monotonically increasing function. This is done so that handling the sum of items is easier than handling the product of items.
- The final step is to take the derivative of the log likelihood function and set it to 0 to get the maximum point.

# Day 31 - 18/04/2026
## Monitoring Agents in Production
- In production, the system might need to scale up to a multi-agent system. This means all agentic interaction needs to be tracked.
- The agents in production might need to subsequently scale to multi-modality, thereby requiring new methods for monitoring.
- In production, agents can improve based on the feedback, which is curated in real-time, making agent behaviour unpredictable.
- These changes might introduce new failure modes, higher complexity while calling new tools via MCP servers, or if the agentic patterns need to be changed
- The same evals that are used in Dev can be carried over to monitor system performance. Some new evals might be necessary based on production usage.
- Use  LLM-as-a-judge, code-based evals, and human annotation to judge system performance.
- These can be useful for CI/CD deployments as they can point out flaws related to a new enhancement (model change, code change, etc.)
- Maintain the golden dataset, augment it with new production scenarios and run the evals in the dev env before shipping changes to production
- An example of this
<img width="1884" height="879" alt="image" src="https://github.com/user-attachments/assets/a927123e-ca9b-416a-bc38-9e01ae8be592" />

# Day 30 - 17/04/2026
## Microsoft Agent Framework - Workflow
- The whole agent integration can be orchestrated by the workflow components of the agent framework.
- Executors and handlers are sort of langgraph nodes that carry out different tasks in a workflow. These themselves can house agents.
- Edges are what connect the executors to build the graph workflow
- Events are used for interactivity. They are used to pause and run the workflow, bring human-in-the-loop and provide observability.
- The power of MAF lies with its flexible workflow types.
- Sequential workflow is straightforward, executing one task after the other
- Parallel workflow is used to spawn multiple parallel threads, and finally, a collector/merger executor collects all of them
- Branching workflow is where, based on a switch case business rule logic, the workflow dynamically takes various paths
- There is a visualizer built-in that helps visualise the workflow graph in Mermaid. 

# Day 29 - 16/04/2026
## 8 Agentic Architecture Design Patterns
1. Agentic System Design - This covers workflow and orchestration. How agents will interact with Agents, tools, and the database
2. Tool Definition and Contract - This defines how the agent leverages all tools using protocols such as MCP
3. Data Design - All data sources from which data can be retrieved as context. Such as Vector DB/ Relational DB/ Graph DB
4. Prompt Library - Maintaining a Robust prompt library which can be finetuned as necessary.
5. Reliability Design - Incorporate logic to ensure that agentic design does not fail
6. Security and safety - Ensure that the guardrails are well-maintained
7. Evaluation and observability - Ensure that production systems have well-orchestrated evaluation loops and an observability platform to view them
8. End User Experience - A very well-orchestrated system can fail if it does not stand up to the user experience. Hence, UI-UX design is critical
<img width="341" height="621" alt="image" src="https://github.com/user-attachments/assets/cb71ca11-c101-45ab-9477-acdf2c2ed66f" />
<img width="355" height="604" alt="image" src="https://github.com/user-attachments/assets/a3336f91-b97b-481e-9b99-6f88bfffdc0c" />

# Day 28 - 15/04/2026
## Deep Neural Network
- It is another type of adaptive basis function
- While the kernel function calculates the similarity of one point with all the other points to provide a grand matrix k, the neural network provides another set of parameters that can linearly combine with features to provide a different state, which can then be used to finally predict y.
- The initial function that provides the inner linear transformation to a nonlinear function within the neurons is called an activation function
- Examples: ReLU, Leaky ReLU, sigmoid, Threshold functions
- Solving a neural network is a nonconvex optimisation problem
- Neural Networks can be solved using gradient descent
- Each Neuron can be thought of as a template to represent a particular feature when trained. Where the feature (digit recognition) will be maximised when the corresponding neuron is fired, as the similarity of the template to the features would be maximised.
- If there is a large number of neurons, then any linear prediction can be approximated.
- So each interval can be approximated with the activation function curve between that interval
- Since a neural network is a nested linear combination of activation functions, it can be represented as in the diagram below
- <img width="1159" height="800" alt="image" src="https://github.com/user-attachments/assets/0b80c04b-5108-4c02-a195-fe320e2750bc" />
<br><br>
- A deep neural network is nothing but a nesting of the activation functions, and finally getting the output with the final weights.
- <img width="1150" height="764" alt="image" src="https://github.com/user-attachments/assets/174d286d-c33a-4845-9efe-b28a50e3d760" />
- The weights are updated based on back propagation using the chain rule of differentiation.
- <img width="1221" height="734" alt="image" src="https://github.com/user-attachments/assets/69ecc55b-8cfb-4e9f-9507-9d076f71a147" />

# Day 27 - 14/04/2026
## Microsoft Agent framework contd..
- MAF has two types of memory, full thread and long-term.
- Full thread means all the chat interaction information is stored in memory
- Long-term means only key behavioural attributes from the overall chat are stored.
- It also has 4 types of middleware-
  1. Timing - Measures the overall time for agent interaction
  2. Security - blocks PHI/PII or other sensitive information
  3. Functional- Lists all the tool interactions
  4. Token counter -Keeps track of overall cost.

# Day 26 - 13/04/2026
## Microsoft Agent framework
- Microsoft agent framework brings the best of Symantic Kernel and Autogen
<img width="849" height="470" alt="image" src="https://github.com/user-attachments/assets/19512f11-8185-4895-b3f9-c5ea0a10d704" />
- We can define the connection details in the client and then define the agent with the client.
- This can then be defined as MCP clients, and all tools can be utilised.
- They can also be integrated with Microsoft AI Foundry, and the agents can be managed from the AI portal.

# Day 25 - 12/04/2026
## Cursor vs GitHub Copilot agent mode vs Claude code
- Choose Cursor if you want the strongest AI-first editor experience for interactive implementation, refactoring, and codebase-wide edits.
- Choose GitHub Copilot agent mode if you already live in GitHub and want agentic help without changing editors or team workflow too much.
- Choose Claude Code if you want a terminal-first agent that is editor-agnostic and more scriptable for advanced automation.

# Day 24 - 11/04/2026
## Evaluating the performance of LLM as a judge
- It is important to judge if the LLM judging the quality is actually good itself.
- There are 2 ways to do it
- 1. Code-based eval:- you submit the entire response that you want to evaluate and supply the ground truth in terms of true and false. Now check if the LLM judgement and ground truth match based on Code level eval
- 2. Cosine similarity-based eval:- If the ground truth is a sentence or two, then code-based eval would not work. In that case, we can use cosine similarity to judge the judgment accuracy
- Below is an example
- <img width="1209" height="552" alt="image" src="https://github.com/user-attachments/assets/989f5588-c8c4-49f6-bde7-042ca56f6067" />

# Day 23 - 10/04/2026
## Levenshtein distance
- Levenshtein distance is just a way to count the minimum number of single-character edits needed to change one word into another, where the allowed edits are insert, delete, and substitute.
- Levenshtein distance is sensitive to insertions, deletions, and substitutions at the character level, so it works well for typos, OCR noise, and small string variations such as bok vs book.
- Cosine similarity ignores character edit paths and instead compares vector direction, which is why it is commonly used for bag-of-words features, TF-IDF, and embeddings.
- A typical way to use both is a 20 80 ratio between cosine similarity and Levenshtein distance
```python
def hybrid_similarity(query, candidates, w_lev=0.4, w_cos=0.6):
    texts = [query] + candidates

    vectorizer = TfidfVectorizer()
    X = vectorizer.fit_transform(texts)

    query_vec = X[0]
    candidate_vecs = X[1:]

    cos_scores = cosine_similarity(query_vec, candidate_vecs).flatten()

    results = []
    for candidate, cos_score in zip(candidates, cos_scores):
        lev_score = normalized_levenshtein_similarity(query, candidate)
        hybrid_score = w_lev * lev_score + w_cos * cos_score

        results.append({
            "candidate": candidate,
            "levenshtein_similarity": round(lev_score, 4),
            "cosine_similarity": round(float(cos_score), 4),
            "hybrid_score": round(float(hybrid_score), 4)
        })

    return sorted(results, key=lambda x: x["hybrid_score"], reverse=True)
```


# Day 22 - 09/04/2026
## Evaluation-driven development
- It's a cycle of curating a dataset, tracking model changes, prompt tool, etc., as experiments, running evaluation for each experiment, and assigning an evaluation score.
- Curating a dataset comes down to evaluating a comprehensive dataset representative of the sample size, rather than exhaustive use cases
- Tracking changes include changing prompt tool router skills models etc.
- Evaluating experiments comes down to running code as eval or LLM-as-a-judge eval
- This includes learning from prod to be put in dev
- <img width="982" height="492" alt="image" src="https://github.com/user-attachments/assets/989de4d4-b537-46b5-96e5-14d8a9848bc9" />

# Day 21 - 08/04/2026
## Agent Experiment
- An experiment is a complete run of defining a dataset and evaluating the convergence metrics for an agent
- <img width="654" height="262" alt="image" src="https://github.com/user-attachments/assets/b9609105-f82c-467f-81b7-d569210fc12c" />
- The dataset can be uploaded as a dataframe, and then experiments can be run for evaluations
- Once the eval is done, the score looks like below
<img width="1687" height="364" alt="image" src="https://github.com/user-attachments/assets/9e04e3b5-2051-4e2b-9662-5936ff033512" />


# Day 20 - 07/04/2026
## Agent Trajectory and Convergence
- Agent trajectory is the path through router steps, tool call, and logic steps that the agent took for a given input
- As we have multiple tool-calls within an agent trajectory or we have a multi-agent system, the agent trajectory can become quite complicated.
- The agent trajectory matters because, through it, we can optimize agent steps and eliminate unnecessary tool calls.
- Convergence measures how closely the agents follow the optimal path for a given query
- This measures what percentage of time the agent is taking the optimal path given the same set of inputs
- Convergence score of 1 means 100% of the time, the optimal path is being chosen by the agent
- Convergence evals won't catch inefficiencies if an unnecessary step is taken by the agent every time.
- Convergence evals should always evaluate fully completed agent runs.
- Below is the convergence calculation
<img width="1908" height="904" alt="image" src="https://github.com/user-attachments/assets/44425ced-2595-4e20-a238-db091c4241a7" />



# Day 19 - 06/04/2026
## How to set up custom evals
- define the LLM as a judge (or custom) prompt template
- Query the required span
```python
query = SpanQuery().where(
    # Filter for the `LLM` span kind.
    # The filter condition is a string of valid Python boolean expressions.
    "span_kind == 'LLM'",
).select(
    question="input.value",
    tool_call="llm.tools"
)

# The Phoenix Client can take this query and return the dataframe.
tool_calls_df = px.Client().query_spans(query, 
                                        project_name=PROJECT_NAME, 
                                        timeout=None)
tool_calls_df = tool_calls_df.dropna(subset=["tool_call"])

tool_calls_df.head()
```
- Evaluate the tool call
```python
with suppress_tracing():
    tool_call_eval = llm_classify(
        dataframe = tool_calls_df,
        template = TOOL_CALLING_PROMPT_TEMPLATE.template[0].template.replace("{tool_definitions}", 
                                                                 json.dumps(tools).replace("{", '"').replace("}", '"')),
        rails = ['correct', 'incorrect'],
        model=OpenAIModel(model="gpt-4o"),
        provide_explanation=True
    )

tool_call_eval['score'] = tool_call_eval.apply(lambda x: 1 if x['label']=='correct' else 0, axis=1)

tool_call_eval.head()
```
- Upload into the observability platform
``` python
px.Client().log_evaluations(
    SpanEvaluations(eval_name="Tool Calling Eval", dataframe=tool_call_eval),
)
```

# Day 18 - 05/04/2026
## How is the Standard Kernel equivalent to an infinite basis Function
- It can be proven that the Standard Kernel representation is equivalent to the infinite basis function
- This is possible because it depends on a limited number of data points, and the regularization term heavily penalizes higher order polynomial
- <img width="696" height="820" alt="image" src="https://github.com/user-attachments/assets/46dbcf1c-06a7-4fbf-a262-7d3993234f13" />
- <img width="691" height="451" alt="image" src="https://github.com/user-attachments/assets/167dfae9-4005-437a-83a2-c5c0408229a1" />
<br><br>
- A Gaussian RBF Kernel can also be represented in terms of this infinite series problem.
- This can be done due to the exponential term being expanded as in the Taylor series
- <img width="607" height="875" alt="image" src="https://github.com/user-attachments/assets/7daa0f5c-5b78-491d-9998-413647fa9cbb" />

# Day 17 - 04/04/2026
## Alternatives to RAG
### Long Context Windows
#### Pros
- No RAG infra required, all information is dumped in the context window
- Retrieval lottery avoidance - Reduces the chance of retrieving irrelevant documents
- Whole book problem solved - If a question is asked like what was not in a particular release, traditional RAG might retrieve all documents that are for the release. Since the entire context is passed, the long context mitigates that risk to an extent
#### Cons
- Re-reading - for dynamic context, the document has to be rewritten every time
- Needle in the haystack - If it's a very specific retrieval, like one line within a 500-page document, this approach is prone to hallucinations
- If the dataset is too large, this approach is not feasible
### Vectorless RAG
- Here, the idea is to create a content table of index based on important events in the document.
- Each of these forms a node of a tree
- These main events can be linked to specific sub-chapters within them
- These sub-chapters form sub-nodes.
- The idea is to do a tree-based traversal when a user queries something.
- Context retrieval is based on any tree-based algorithm by traversing to the leaf node, which is a pointer to pages where the required context exists.
- LLM makes the tree, so parsing is easy for them
- This can only be done by thinking/reasoning models, so it takes more time.
# Day 16 - 03/04/2026
## How does Evaluation Work?
- There are 3 types of evaluations: Code-based evals, LLM-as-a-judge, and human annotations
- <img width="822" height="585" alt="image" src="https://github.com/user-attachments/assets/fca0b292-90e6-4a49-8c38-f5b03189441c" />
<br><br>
- These skills can be applied to the router, or the path, or a particular skill or function
- For the router, we can evaluate whether the Function Calling was correct and if the parameters it passed to those functions were correct.
- Skills can be evaluated both using standard LLM or code-based evals
- <img width="1081" height="557" alt="image" src="https://github.com/user-attachments/assets/fe46ebce-b4c0-4215-8ab2-5f52a0325dfa" />

# Day 15 - 02/04/2026
## How to set up tracing
- Tracing can be set up either with the 'with' clause or tracer decorator on a function
- Primarily, there are 3 types of tracing calls: tracer.tools, tracer.agents, and tracer.chain
- While using the 'with' clause, we need to include tracer. set_input and set_output to log the calls.
- For the function decorator, the input and output of the function are captured by default.
- There are a few standard APIs for LLMs that can be defined one time, which will capture all the calls.
- Below is an example for both the decorator and the 'with' clause
```python
tracer_provider = register(
    project_name=PROJECT_NAME,
    endpoint= get_phoenix_endpoint() + "v1/traces"
)
tracer = tracer_provider.get_tracer(__name__)
OpenAIInstrumentor().instrument(tracer_provider = tracer_provider)
@tracer.tool()
def lookup_sales_data(prompt: str) -> str:
    """Implementation of sales data lookup from parquet file using SQL"""
    try:

        # define the table name
        table_name = "sales"
        
        # step 1: read the parquet file into a DuckDB table
        df = pd.read_parquet(TRANSACTION_DATA_FILE_PATH)
        duckdb.sql(f"CREATE TABLE IF NOT EXISTS {table_name} AS SELECT * FROM df")

        # step 2: generate the SQL code
        sql_query = generate_sql_query(prompt, df.columns, table_name)
        # clean the response to make sure it only includes the SQL code
        sql_query = sql_query.strip()
        sql_query = sql_query.replace("```sql", "").replace("```", "")

        with tracer.start_as_current_span(
            "execute_sql_query", 
            openinference_span_kind="chain"
        ) as span:
            span.set_input(sql_query)
            # step 3: execute the SQL query
            result = duckdb.sql(sql_query).df()
            span.set_output(value=str(result))
            span.set_status(StatusCode.OK)
        
        return result.to_string()
    except Exception as e:
        return f"Error accessing data: {str(e)}"
```

# Day 14 - 01/04/2026
## Activation Functions
- Activation functions are the ones that make the model nonlinear 
- Relu(x) - max(x,0)
- Leaky Relu - max(alpha.x,0)
- sigmoid
- <img width="495" height="148" alt="image" src="https://github.com/user-attachments/assets/c772ba1f-f2ec-4fa5-80df-548e95847bd1" />


# Day 13 - 31/03/2026
## Kernel Function part 1
- Non-linear functions help to predict data in the real world better
- The idea is to use multiple basis functions to transform a nonlinear relationship into linear functions so that we can solve for parameter theta
- Primarily 2 types of adaptive basis functions that are used are Kernel functions and Neural Networks.
- Kernel function is about finding similarity between all points provided in the distribution with itself, and then using that Kernel matrix to solve for theta
- <img width="708" height="785" alt="image" src="https://github.com/user-attachments/assets/8d76e836-3094-485c-b18d-408295265862" />
<br><br>
- So the final form looks like below with Penalty
- <img width="608" height="184" alt="image" src="https://github.com/user-attachments/assets/5f10fe18-52e6-4f4d-9488-7d4c9ee0ad63" />
<br><br>
- Kernel functions can similarly be applied to classification problems as well.
- <img width="665" height="441" alt="image" src="https://github.com/user-attachments/assets/99d19cb1-4a86-43b5-9501-16e8a918e0c7" />


# Day 12 - 30/03/2026
## Multivariate Normal Distribution part 2
- Performing PCA on a dataset is exactly equivalent to assuming the data was generated by taking an independent, perfectly aligned Gaussian blob and rotating it. PCA simply runs that process in reverse to find the axes of the original, unrotated blob
- Using Expectation Maximization. This view can help to fill the missing data.
- <img width="808" height="735" alt="image" src="https://github.com/user-attachments/assets/cb60a996-6371-475d-8b66-297dba475f14" />
<br><br>
- If MLE is performed on MVN, the resulting mean and variance are equal to the empirical mean and variance
- <img width="904" height="861" alt="image" src="https://github.com/user-attachments/assets/34a41c88-f68a-4809-bf51-87f630a218ca" />



# Day 11 - 29/03/2026
## Multivariate Normal Distribution part 1
- MVN distribution is characterized by distribution in more than one dimension, such that there is a mean vector with a collection of all means and a covariance matrix sigma with all the covariances between various dimensions
- It is represented in the form below
- <img width="924" height="961" alt="image" src="https://github.com/user-attachments/assets/66825fb6-f585-48ce-8d00-d91105c92be7" />
<br><br>
- If all Xis are independent of each other, where each xi is a normal distribution, then their concatenation is also multivariate normal
- In this case, the covariance matrix will only be a diagonal matrix with variance as the diagonal elements
- If we divide an MVN distribution into multiple parts, then the marginal distribution of each part will also be a normal distribution
- If we divide an MVN distribution into multiple parts, then the conditional distribution of each part will also be a normal distribution
- <img width="525" height="320" alt="image" src="https://github.com/user-attachments/assets/27f7f66c-3d9d-4d79-b1d5-228fed012396" />
<br><br>
- If a linear transformation is applied on mvn distribution, the transformed distribution is also MVN
- <img width="860" height="823" alt="image" src="https://github.com/user-attachments/assets/2e1b295b-2b15-4ed2-b016-e083af79c331" />
<br><br>
-


# Day 10 - 28/03/2026
## Expectation Maximization Algorithm
- It is an approximation of the maximum log likelihood estimate.
- The core idea is to use coordinate descent to solve a chicken-and-egg problem.
- Initially, mu sigma and pi (mixture parameter) are initialized randomly.
- Then an initial MLE estimation is performed with these values
- The E(expectation) step is to calculate the posterior using the formula. The gamma value is calculated for each point for every cluster and  indicates how much each cluster contributes to every point
- <img width="720" height="124" alt="image" src="https://github.com/user-attachments/assets/beaf1c44-4715-4a84-a3dd-007a7d724270" />
<br><br>
- The M (Maximization) step is to then use the gamma values and recalculate the mu, sigma, and pi.
<img width="731" height="463" alt="image" src="https://github.com/user-attachments/assets/f2532d49-c6e2-4125-9118-794020325bac" />
<br><br>
-This goes on till the values of mu sigma and pi converge
<br><br>

### Example
<br>
- <img width="407" height="499" alt="image" src="https://github.com/user-attachments/assets/17a013c3-6afc-4ebf-9a46-32b14b1aba34" />
-<img width="1064" height="780" alt="image" src="https://github.com/user-attachments/assets/71403119-e043-4d3c-95aa-b3f51eee1fe0" />




# Day 9 - 27/03/2026
## What is observability
- Generic software concept for having visibility of all layers of the application
- It consists of traces and spans. spans are smaller elements that sum up together to make traces
<img width="956" height="484" alt="image" src="https://github.com/user-attachments/assets/f22784d9-5ce2-4bd4-bc3a-e13e5f8d8d24" />
<br><br>
-Traces work on the Open Telemetry protocol. They have a process of instrumentation to capture and process spans, and then collectors and processors to collect and visualize those spans
<img width="827" height="494" alt="image" src="https://github.com/user-attachments/assets/d29bfa93-d6fa-464d-8959-e313045686a9" />
<br><br>
- This simplifies debugging, provides detailed production usage and then uses it to generate insights


# Day 8 - 26/03/2026
## How to create an orchestrated agent workflow
- For this example, first define the tool for data query. This is a simple DB call in SQL, where the SQL is created by the LLM
- Next, from the retrieved data, trends and insights can be generated by another tool
- Lastly, from the same queried data, visualization code can be generated. This was done in 2 steps, first the chart configuration was generated, and then the Python code was generated with those config.
- Finally, the entire workflow was orchestrated natively using OpenAI function definition schema and tool calling. This can be done in a simpler workflow using MCP.

- Below is the example that was orchestrated
  <img width="988" height="355" alt="image" src="https://github.com/user-attachments/assets/a59fd846-3fcc-403c-8cfa-92322d5d2acf" />
# Day 7 - 25/03/2026
## How to create custom scripts
- An Agent itself has 3 components
  - Router: This is the brain of the AI agent and decides which skill (or tool to call)
  - Skills/Tools: This can be custom skills that define entire workflows defined in skills.md, or can be tool calls where a Python function executes everything
  - Memory is where context, retrieved chunks, and previous history are stored
<img width="1602" height="746" alt="image" src="https://github.com/user-attachments/assets/7b34cae6-e3a2-44e5-aa16-ea221f782d43" />


# Day 6 - 24/03/2026
## How to create custom scripts
- Define the YAML frontmatter effectively
<img width="1542" height="782" alt="image" src="https://github.com/user-attachments/assets/6d672bdf-e836-4a69-9a2a-11507606f46a" />
- Provide step by step instruction in the body content
  <img width="1844" height="681" alt="image" src="https://github.com/user-attachments/assets/2666f673-5095-4d54-bcda-d1c44099f339" />
- Decide on how loose or tight the instructions have to be
  <img width="1410" height="630" alt="image" src="https://github.com/user-attachments/assets/595654ec-8e38-485c-902a-ead9f3f01937" />
- Organize all external references in a separate directory and link it from the skill boy. These references also work in terms of progressive disclosure.
  <img width="1784" height="454" alt="image" src="https://github.com/user-attachments/assets/b159178f-1bd2-4479-b544-5c5d6c043925" />


# Day 5 - 23/03/2026
## How Agent Skill can be combined
- Agent skills also come in predefined packages.
- One skill that is called skill creator is specifically useful for creating new skills as necessary.
- Multiple custom skills or prebuilt skills can be combined to create a holistic workflow.
- Anthropic has an open source skill library https://github.com/anthropics/skills

<img width="917" height="208" alt="image" src="https://github.com/user-attachments/assets/5a02b5bd-7f73-4950-ac3e-b36a689d926f" />


# Day 4 - 22/03/2026
## How Agent Skill interacts with other GenAI workflow components

- Agent skills can define specific and repeatable workflows that can use sub-agents and MCP tools.
- These can be integrated within the workflow definitions
- Think of tools like hammers, nails, etc. and the skills as the recipe of how to build a bookshelf
- Specific repeatable workflows like code analyzer agent, test case creation agent, etc., can utilize specific skills and MCP servers to execute that specific function

<img width="1905" height="735" alt="image" src="https://github.com/user-attachments/assets/fa482fb7-8430-43f5-8c45-1db73c3b6ead" />

# Day 3 - 21/03/2026
## Why use Agent Skills
- Agent skills are workflow patterns that guide an LLM on what to do
- It is more than a prompt library as it can have instructions for reading reference files, executing scripts, and other styling information
- It is more than an MCP tool calling as it can orchestrate the entire workflow, so that it guides the LLM on what to do without the LLM having to decide based on the doc string on the MCP server
- To avoid clogging the context window, agent skills work on the principle of progressive disclosure. At the start of every skill, which is instruction defined in markdown format, there is a YAML section that contains the skill name and description (sort of like the doc-string of the mcp server), which contains information on what that skill does. For all the skills, only this first part is initially loaded. Based on the user query, the LLM decides which skill is to be used. Once the skill is decided, the LLM then loads the instructions and executes any scripts or MCP server calls. That way, the context window does not overflow even if there are many skills in the skills.md file.
- The folder structure is as follows. The top-level folder is the skill name, which has to match the name definition of the YAML file

<img width="1217" height="524" alt="image" src="https://github.com/user-attachments/assets/724dc148-f9e4-4935-b270-7310211b481c" />

# Day 2 - 20/03/2026
## Expectation Maximization vs K-means
- K means algorithm is deterministic in nature. This creates a problem that if a particular datapoint is equidistant from both the centroids, the point has to be assigned to any one of the centroids randomly. This makes the assignment asymmetric. Expectation Maximization introduces the idea of a probabilistic model instead of a deterministic one. The idea is to assign probability to all the points to be placed at any one of the centroids and then taking an weigted probability for all the clusters for that point. That way, the centroid allocation is much more accurate than determinsitic apporach of k-means

- <img width="920" height="806" alt="image" src="https://github.com/user-attachments/assets/2c4de131-3dea-499a-9b40-cf809a1427bd" />


# Day 1 - 19/03/2026 
## Graph DB
- Video 8 talks about how to use Langchain to give multishot examples in the prompt and retrieve the correct chunks. The graph DB has to be created in the first place. Creating the cyphers is really difficult, but Langchain's GraphCypherQAChain can create the prompt as well as execute them at one go. Here, though, we have to define the schema in the prompt template, since we pass the graph itself as a parameter, we do not have to specify it manually

```python
CYPHER_GENERATION_TEMPLATE = """Task:Generate Cypher statement to query a graph database.
Instructions:
Use only the provided relationship types and properties in the schema.
Do not use any other relationship types or properties that are not provided.
Schema:
{schema}
Note: Do not include any explanations or apologies in your responses.
Do not respond to any questions that might ask anything else than for you to construct a Cypher statement.
Do not include any text except the generated Cypher statement.
Examples: Here are a few examples of generated Cypher statements for particular questions:

# What investment firms are in San Francisco?
MATCH (mgr:Manager)-[:LOCATED_AT]->(mgrAddress:Address)
WHERE mgrAddress.city = 'San Francisco'
RETURN mgr.managerName

# What investment firms are near Santa Clara?
MATCH (address:Address)
WHERE address.city = "Santa Clara"
MATCH (mgr:Manager)-[:LOCATED_AT]->(managerAddress:Address)
WHERE point.distance(address.location,
managerAddress.location) < 10000
RETURN mgr.managerName, mgr.managerAddress

The question is:
{question}"""



CYPHER_GENERATION_PROMPT = PromptTemplate(
input_variables=["schema", "question"],
template=CYPHER_GENERATION_TEMPLATE
)

cypherChain = GraphCypherQAChain.from_llm(
ChatOpenAI(temperature=0),
graph=kg,
verbose=True,
cypher_prompt=CYPHER_GENERATION_PROMPT,
)

prettyCypherChain("What investment firms are near Santa Clara?")
```
