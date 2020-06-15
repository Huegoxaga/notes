# Machine Learning

## Introduction

- Machines learning is one type of artificial intelligence.
  - AI is a technique which enables machines to mimic human behaviour.
- Machine Learning has 4 categories:
  - `Supervised Learning` - Machine learns from data with labels, it can deals with the following tasks
    - Classification
      - Data are labeled manually with its class, expected to let the machine determine the class after learning from the data.
    - Regression
      - It is a method of predicting a numeric value called target.
      - A set of attributes with value or features are provided for learning, they are called predictors, along with target values as labels.
        - `attribute` is a type of information that will be learned by the machine.
        - `feature` is a type of information with a value that will be learned by the machine.
  - `Unsupervised Learning` - data without label, it can deals with the following tasks.
    - Clustering
      - Grouping data
    - Anomaly detection
      - Find any data that is different from most of samples
    - Novelty detection
      - Find any data that has never been seen from all the sample data.
    - Visualizetion
      - Generates a 2D or 3D representation of input data points
    - Dimensionality Reduction
      - Sumarize data and make them have less attributes, as known as feature extraction.
      - It can be used to prepare data before putting into others machine learning algorithm.
    - Association rule learning
      - It is used to discover relations between attributes from different sample data.
  - `Semisupervised learning` - little data with label, many other data without label.
    - It uses a combination of both supervised learning algorithms and unsupervised learning algorithms .
  - `Reinforcement learning` - learning from experience or similar genetic algorithm.
    - An agent will be given different situation. The agent will perform observation and perform an action. The agent will be rewarded and penalized accordingly. Policy will then be establish for it to get the most reward in different situation.
- Any ML methods can be either one of the following type:
  - online(stochastic) learning or batch learning
    - whether or not the learning process is done at one time(batch learning) or consequently overtime based on a stream of incoming data(online learning)
    - batch learning is also called offline learning.
    - batch learning requires a lot of computing resources while online learning uses data as mini batch which can be cheap and fast.
    - online learning is vulnerable to bad data.
  - instance-based learning or model-based learning
    - instance-based will compare new data with sample data then make judgement.
    - model-based learning will generalize sample data, then processing new data based on the model.

## Classical Machine Learning Algorithms

- Decision Trees and Random Forests
- K-Means
  - It is a unsupervised learning algorithm for clustering
  - It can identify discrete groupings within data
- DBSCAN
- Hierarchical Cluster Analysis(HCA)
  - Each Cluster group can have subgroups
- One-class SVM
- Isolation Forest
- Principal Component Analysis(PCA)
- Kernel PCA
- Locally Linear Embedding(LLE)
- t-Distributed Stochastic Neighbor Embedding(t-SNE)
- Apriori
  - It is a type of association rules learning algorithm
    - It can be used to find out the association of user behaviors and be used for task like movie recommandtion
  - It calculates three values:
    - Support: divide the number of users interested in the topic by the total number of users.
    - Confidence: divide the number of users interested in the related topic by the number of users interested in the original topic.
    - Lift, divide the confidence score by the support score.
  - This algorithm compares all possible combination from the sample.
    - Each combination is a potential rule.
  - Only the samples have support and confidence scores higher than the minimum value set at the beginning of the calculation will be recorded.
  - The final result will rank the lift score from high to low.
- Eclat
  - It is a type of association rules learning algorithm
  - It only has a support score which is calculated by dividing the rule set by the total number of samples
  - It also need to set a minimum support value and the support score will be ranked from high to low as the final result.

### Linear Regression

- Linear regression is used to find the best fitting line(not nesscessirily straight) of a set of data points
- suitable for solving regression problems that find a predicted value.
- Ordinary least squares is used to calculate the best fit
  - find the minimum value of the square of the difference of y and y hat.
  - y hat is the predicted value while y is the actual value.
- Simple linear regression - The model will be a linear function with one constant, one dependent variable and one independent variable `x` times a coefficient.
- Multiple linear regression has one constant, one dependent variable and many combinations of independent variables times a coefficient.
  - Each independent variable represents a different feature in a single row of data.
  - Dummy Variable - For a categorical featue each possible category will form a new field with value 0 or 1, when the current row of data is belonds this a certain category the value for this category will be 1 and others are 0.
    - Dummy Variable Trap - The number of this categorical independent variable will always be one less than the total number of the possible options since all others are 0 implys this record belong to the last category already.
- Polynomial(linear) regression - It is like Multiple linear regression but the power of independent variable increases with the number of them.
- For linear regression models all of the following assumptions must be achieved.
  - Linearity
  - Homoscedasticity
  - Multivariate normality
  - Independence of errors
  - Lack of multicollinearity

### Decision Trees

##### Classification Trees

- It is used for classification problems

##### Regression Trees

- It is used for regression problems
- It split the datapoints into groups based on the independent variables of a data point.
- It uses an information entripy algorithm to optimaize the split.
- Each one of the split is called a leaf.
  - Each of the final split is called the terminal leaf.
- A decision tree is a binary tree structure, each node check if one of the independent variable is greater or smaller than a certain value.
  - Nodes from the same depth are dealing with the same independent variable.
- The split add information to the datapoint and group them.
- The average of all data points in one terminal leaf will be calculated as the prediced value for all new data point if it falls in the split.

### Random Forests

- It is a type of ensemble learning.
  - A algorithm that utlizes a single machine learning algorithm multiple times or uses different algorithm at the same time.
- It uses random subsets of the datapoints to form decision trees.
  - The number of data points in each subset should be set.
  - The total numbers of trees should be set.
- The average of all split from each decision tree will be used to make prediction.
- It works for both classification tree and regression tree.

### k-Nearest Neighbors

- A supervised learning algorithm
- For Classification:
  - Select a `k` value(small interger value). For any new data point find its `k` nearest neighbors, then the new data point belongs to the category that is the same as most of its neighbors.
  - Euclidean Distance(geometrical distance, square root of the sum of the square difference) is often used.
- For regression:
  - Queries K-Nearest Neighbors and returns average value for the instance
- It does not scale well for large datasets

### Logistic Regression

- It is a classification algorithm.
- Fit a linear regression into a range of 0 and 1 as the probabilities using the logistic regression formula.
  - Subsitute `y` in the linear regression formula into the sigmoid function.
- It can generate `P` hat as predicted probability of a given value.
- It can return ethier 0 or 1 as `y` hat value if yes or no is the only required result.
  - return `y` hat as 1 if the probability is higher than a certain defined value and vise versa.

### Support Vector Machines(SVMs)

- It is a classificaton algorithm
- It focuses on finding the boundary, then make decision only based on the boundary.
- The boundary is found to separate all data point with maximum margin.
  - Maximum margin means the greatest distance to points from different categories.
- The points that have the same cloest distance to the boundary is called support vectors.
- The boundary is called maximum margin hyperplane or maximum margin classifier.
- The lines which are parallel to the maximum margin hyperplane and have zero distance to the support vectors are called positive or negative hyperplane.

##### Support Vector Regression

### Neural Networks

- It was first introduced in 1980s, it was getting popular recently only becase the improved stroage and computing
- Can be used for both regression and classification tasks.
- Most Neural Networks are consist of a Feedforward Process and Backpropagation.
  - FeedForward Process(Nerual Network) uses static mapping as the output only depend on the input and the weights
  - Going from output to input and finding the better weights for the model using stochastic gradient descent with the chain rule
- In neural science, each neuron has dedrites(receiver) and axon(transmitter), millions of millions of neuron work together. sigals are passed through synapses.
- In neural networks, the processing unit is called neuron or node. The connection between neuron is also called synapse.
- Overfitting and Underfitting - Underfitting(High Bias) implys a model that is too simply to make prediction, Overfitting(High Variance) implys a model that is learning too hard from the train data and too complicated to effectively and correctly make prediction.
  - The goal is to aim to build a model that is a bit overfitting and slightly adjust it to prevent overfitting.
  - The most important indicator of overfitting is the train set accurancy is much better than the test set.
- Hyperparameters are parameters used to build and train models.

##### Artificial Neural Networks(ANNs)

- The initial input values for the artificial neural network would be multiple features about one sample.
- The final output values for the artificial neural network could be either a predicted value(one output), a boolean value(one output) or categorical values(multiple output nodes)
- Each input value is associated with a weight, the neural network learns by adjusting the weight of each input value.
- Each nerual will have the sum of all input value times the weight.
- Activation function determine the output of each nerual based on the inputs' sum value
  - Threshold function - either yes or no(0 or 1)
  - Sigmoid function - gradually increase(0 to 1) close to but never reaches 0 or 1
  - Hyperbolic Tangent - gradually increase(-1 to 1) close to but never reaches -1 or 1
  - Rectifier function - either 0 or linearlly grows from 0 to 1.
- The input values are called the input layer the output values are called output layer.
- Nodes in between are called hidden layers, each layers will process values and generate output for the next layer.
  - Each neuron in the same layer focuses on different aspects of the input info.
  - Hidden layers can have as many as possible, the neural network can be called deep learning if there are lots of layers of neurons in between.
  - ANNs with fewer hidden layers can be called shallow learning.
- The final output will be compared with the labeled target value, and use back propagation to adjust all weights of synapse, in order to achieve a higher accuracy.
  - `y` is the actually value, `y` hat the is output value.
  - A cost function is used to calculate the difference between `y` and `y` hat. The most frenquely used cost function is mean squared error which divides the squares of the difference of `y` and `y` hat by 2.
  - During each back propagation all of the weight for each synapse in the entire neural network are adjusted at the same time.
  - All the weight are initially set to a random small number close to zero.
  - Learning rate can be set to control how much the weights can be adjusted at a time.
- A single layer feed forward nerual network(perceptron) is the base machine learning unit in ANNs.
- There are several ways of adjust the weights:
  - Try all possible combination of weight values and calculate its cost function value, this is not practically since it takes billions of years.(curse of dimensionality)
  - Gradient Descent - adjust the combination of weights by calculating the slope, hence each trials will move closer to the minimum value. The sum of cost functions of all rows of data in the dataset are calculated in one guess.
    - It might find the local minimum if all the cost function values are not convex.
  - Stochastic Gradient Descent - Similar to gradient descent, but make adjustment based on cost function of every single row of data.
    - It will find the global minimum.
    - It is light weight and faster.
  - Mini-batch Gradient Descent - runs one batch of rows at a time.
- One epoach is the process of finding minimun cost function value of a batch of dataset after many times of iteration of the forward propagation and backpropagation adjusting of the weights.
  - One epoach will be repeated many times in order to improve accuracy.

##### Convolutional Neural Networks(CNNs)

- It is an ANN for image recoginion.
- For a computer, a back and white image is an array of numbers from 0-255(8 bits data) where 0 represents black, 255 represents white and grey scale colors in between.
- A colorful image is a 3-D array with 3 layers of 2-D values from 0-255. Each layer represents the intensity of red, green and blue. Each layer of data is called red, green and blue channel repectively.
- CNNs will process an image in the following order:
  - Convolution operation is to use a feature detector to generate a feature map.
    - The feature detector is a small matrix(2-D array) that has a certain predefined value in it. Its has different sizes in various CNNs.
    - The feature detector(filter) will be moving across the image(all pixel will only be processed once, line by line) and count the number of matches(non-zero) found when it overlapse with the image.
      - A stride the step the feature detector moves across the image.
    - Feature detector has negtive value to dim the image pixel and positive value to highlight.
  - A feature map(convolved feature) will be generated according to hte stride and feature detector size, the feature map will summarize the feature of the image.
  - Multiple feature detectors will be used on a single image and generate various feature maps that each emphasis on different features of the image.
  - Feature maps will be processed by rectifier function to generate rectifier linear unit layer breakup the linearality of feature maps and amplify the features for further process.
    - Dark part of the feature map is represented by negtive value, bright part of the feature map is represented by positive value. Rectifier function remove the dark part of the feature map.
  - Pooling will be used on the feature map to preserve the feature and remove unnesscery info to prevent overfitting(overfitting means too much info on one feature). There are serveral types of pooling.
    - Max pooling(most used) - Using a small matrix to scan the feature map with certain stride line by line(all pixel will only be processed once). Only the max value will be recorded.
    - Average pooling - same process as max pooling, but record the average value.
    - Sum pooling - record the sum of the value.
    - Min pooling - record the minimum value only.
  - Process from convolution to pooling can be repeat once again for some CNNs
  - The 2-D array result will be flatten to a 1-D array then it will be fed into an artificial neural network.
    - Hidden layer in the ANN used by CNNs are called fully connected layers.
    - Back propagation in CNNs not only change weight, it also changes feature dectectors.
  - The last fully connected layer will vote for the result for image recognition.
  - The softmax function is used to calculation possibilities of each result for image recogition so possibilities of all possible answers add up to 1.
  - The cost function in CNNs is called loss function, cross-entropy formula is frequenly used.

##### Recurrent Neural Networks(RNNs)

- RNNs are a type of ANNs that can capture temporal dependencies.
  - Temporal Dependencies or Dependencies Over Time - Current output dependent on both current and past inputs.
- Most speed recognition, natural language processing(NLP), time series prediction, gesture recognition uses RNNs.
  - Gesture recoginition combine CNNs and RNNs.
- The inputs for RNNs are in a certain sequence in stead of a single independent input.
- The output of a hidden layer will be stored by the previous layer as additional inputs for that hidden layer.
  - Thoses additioanl input nodes are the memory that stores the states info of the RNNs.
  - The value of the previous state node is applied with the activation function.
  - Each feed back from the previous output is called a time step.
- The exploding gradient Problem happens when it grows too large
  - It can be solved by gradient clipping which will normalize the gradient when it is over a certain threshold.
- RNNs uses Back propagation through time
- vanishing gradient problem causes the RNNs only remember inputs from only a few time step.
- RNNs has a folded model that has a circular arrow which point to the node itself with memory value _s_. The model looks the same at any given time.
- RNNS has a unfolded model that represent the changes of one node throughout a given time period.
  - For unfolded models the input layer is at the bottom the output layer is at the top. Time goes from left to right.
- Time Delay Neural Networks(TDNNs) - The first attempt to add memory to the nerual networks.
- Simple RNNs or Elman(Jordan) network
  - A basic three layer neural network with feedback that serve as memory inputs.
- Long Short Term Memory(LSTM)
  - solving the problem called vanishing gradient problem of other RNNs in which contributions of information decayed geometrically over time.
- Gated Recurrent Networks(GRUs) refines the LSTM.

### Optimatization Tips for Neural Networks

#### Data Preprocessing

##### Numeric Data Preprocessing

1. Importing the data.
2. Replacing missing values by the average of all other values.
3. Encoding categorical data - generating dummy variables.
4. Splitting the dataset into the Training set and Test set.
5. Feature Scaling - put all the features on the same scales.
   - Not all models need to have feature scaling.
   - Applied on training set only.
   - There are two ways for Feature Scaling
     - Standardization returns a result from -3 to 3, Standardization alway works.
     - Normalization returns a result from 0 to 1, Normalization works only if data have a normal distribution in most of the features.
   - Dummy variables do not need to apply feature scaling.

##### Image Preprocessing

- The color value of the images can be rescaled from 0-255 to 0-1 to simplify the data.
  - The training data and testing data should use have the same recaling setting.
- Image augumentation step alteres the images by zooming, flipping and shearing to provide variaties for training.

##### Timeseries data preprocessing

##### Text data preprocessing

#### Hyperparameters Tuning

- Hyperparameters Tuning can be done during model building and model training.

### Build Model

- Hyperparameters in the build model step is called Model Hyperparameters.
- Generally, the ideal number of nodes in each hidden layer is close to half of the input layer nodes plus output layer nodes.
  - Fine tuning can be made to improve, however this approximate number is good enough for determining the number of nodes for all hidden layers.
  - The number nodes in each hidden layer determines the capacity of the model to learn a complex model. When the capacity is greater than needed it will learn to much and cause overfitting.
  - the first hidden layer is suggested to have more nodes than the input layer.
- the number of layers
  - For the number of hidden layer, 3 layer is way better 2. A 4, 5, 6 layers ANNs won't necessarily increase the accurancy greatly.
  - More convolutional layer will increase the accuracy of the prediction.
  - The more fully connected hidden layers, the better the model predict.
- Transfer Learning for CNNs - Use good trained model that can accomplish similar tasks.
  - One technique is to remove the last few convolutional layers then train the data since only those layers are reponsible for specific feature detecting for trained model's own labeling strategy.
  - Fine-Tuning - replace the last fully connected layers with a new layer then train the model based on existing weight from trained model.

### Train Model

- Hyperparameters in the train model step is called Optimizer Hyperparameters.
- Epochs
  - If the number of epochs is too small the model will be underfitting, If the number of epochs is too large the model will be overfitting.
    - The best number of epochs will make the test set and the model have the best performance, this is called the Goldilocks point.
    - Early Stopping is the algorithm for finding the Goldilocks point, hence determine the best number of epochs to train the model.
      - It can be set to stop whenever accurancy decreace, or when accurancy doesn't improve in the next 10 or 20 epoch.
- Learning rate
  - can be a value from 0.1 - 0.00001
  - It controls how fast weight changes during gradient descent.
  - 0.01 suggested starting value.
  - If to small it will take longer steps to find the best weight, if too big the algorithm might not be able to find the best weight.
  - Learning rate decay is an algorithm that helps the model to find the best weight.
    - it can decrease the learning rate linearly or exponentially after a certain epochs.
    - Adaptive Learning Rate changes learning rate dynamically based on the data and training result after each epoch.
- Minibatch size
  - It is 2^n and it can be anywhere from 1 - 256, 32 is a good starting point, then 64, 128, 256.
  - Larger batch size requires more computational resources, and it might cause out of memory errors.
  - Smaller batch size helps preventing the weight to be found at local minima, and it will be slow.

## Advanced Machine Learning Algorithms

- fastText
  - It is used for text data
  - fastText is a library for learning of word embeddings and text classification created by Facebook's AI Research (FAIR) lab.
  - It is implemented through python ML library `Gensim`
  - Facebook makes available pretrained models for 294 languages.
  - fastText uses a neural network for word embedding.
  - It is extended as BlazingText as an AWS Sagemaker built-in algorithm
  - It can be a unsupervised learning algorithm. It converts text to vector(Word2Vec)
    - Word2Vec is a text preprocessing step for downstream NLP, Sentiment analysis, named entity recognition and translation.
    - Words that are semantically similar have vectors that are closer to each other
  - It can be a supervised learning algorithm that supports multi-class, multi-label classification
- Object2Vec
  - A bulit-in algorithm from the AWS Sagemaker
  - It utlizes average-pooled embeddings, hierarchical Convolutional Neural Networks (CNNs), as well as multi-layered Bi-Directional-Long-Short-Term-Memory (BiLSTM)-based Recurrent Neural Networks as encoders
  - It is a supervised learning algorithm for classification, regression.
  - It is extends Word2Vec
  - It can capture structure of sentences and learn relationship between pair of objects
- Factorization Machines
  - A supervised learning algorithm for classification, regression.
  - Works very well with high dimensional sparse datasets
  - Popular algorithm for building Recommender systems. Ex, Movie Recommendation based on your viewing habits
  - It can do collaborative filtering, Ex, cross recommend based on similar users
- Linear Learner
  - Supervised ML algorithm.
  - An AWS sagemaker built-in algorithm for linear regression and logistic regression
  - It works for for regression, binary classification and multi-class classifcation problems.
- XGBoost
  - Supervised ML algorithm for regression and classification problems
  - Gradient Boosted Trees Algorithm
  - Very Popular Algorithm - Won several competitions
- AWS Sagemaker DeepAR
  - Supervised learning algorithm for timeseries forecasting
  - The built-in RNN model in AWS Sagemaker
  - It is the enhanced version of classical forecasting methods, such as autoregressive integrated moving average (ARIMA) or exponential smoothing (ETS), fit a single model to each individual time series.
  - Train multiple related time series using a single model
  - Generate predictions for new, similar timeseries
- Amazon Sagemaker Object Detection
  - The name of the CNNs model provided by AWS Sagemaker.
  - A supervised learning algorithm for classification.
  - It detects and classifies Objects in an image then returns a bounding box of each object location.
- Amazon Sagemaker Image Classification
  - The name of the CNNs model provided by AWS Sagemaker.
  - A supervised learning algorithm for classification.
  - It classify the entire image and it supports multi-labels.
- Amazon Sagemaker Semantic Segmentation
  - A supervised learning algorithm for classification.
  - an AWS sagemaker built-in model
  - Image Analysis Algorithm for Computer Vision Applications
  - Tags each pixel in an image with a class label
- Amazon SageMaker Sequence to Sequence
  - A supervised learning algorithm for convert sequence of tokens
  - the input is a sequence of tokens (for example, text, audio) and the output generated is another sequence of tokens.
  - Example applications include: machine translation, text summarization, speech-to-text.
  - It uses Recurrent Neural Networks (RNNs) and Convolutional Neural Network (CNN) models with attention as encoder-decoder architectures.
- Amazon SageMaker Latent Dirichlet Allocation
  - A unsupervised learning algorithm for topic modeling
  - Group documents by user specified number of topics
  - For documents, it assigns a probability score for each topic
- Amazon SageMaker Neural Topic Model
  - Similar to Amazon SageMaker Latent Dirichlet Allocation

## Model Evaluation

## Machine Learning Frameworks(Libraries)

- A ML frameworks is a libray for a certain programming language which contains various ML algorithm as methods.

#### [TensorFlow](https://www.tensorflow.org)

- It was developed by the Google Brain team for internal Google use. It was released under the Apache License 2.0 on November 9, 2015.
- It is the most popular deep learning framework for Python
- There are also experimental interfaces available in JavaScript, C++, Java and Go, C# and Julia.
- TensorFlow can run on multiple CPUs and GPUs
- TensorFlow is available on 64-bit Linux, macOS, Windows, and mobile computing platforms including Android and iOS.
- Static computation graph - The model should be defined first then compile and train it after.
- TensorFlow 2.0 uses Keras as its official high-level API

#### [PyTorch](https://pytorch.org)

- PyTorch is an open source machine learning library based on the Torch library
  - Torch is an open-source machine learning library, a scientific computing framework, and a script language based on the Lua programming language.It provides a wide range of algorithms for deep learning
- PyTorch also has a C++ interface
- It is developed by Facebook's AI Research lab (FAIR).
- Dynamically Updated Graph - The model is compile after each line of the model definition
- PyTorch is suited for small projects and prototyping

#### [Sonnet](https://sonnet.readthedocs.io/en/latest/)

- Sonnet is a high level library to build complex neural network structures in TensorFlow.
- It is designed to create neural networks with a complex architecture by DeepMind.

#### [MXNet](https://mxnet.apache.org)

- It is owned by Apache Software Foundation
- The framework initially supports a large number of languages (including C++, Python, Java, Julia, Matlab, JavaScript, Go, R, Scala, Perl, and Wolfram Language.)
- MXNet is supported by public cloud providers including Amazon Web Services (AWS) and Microsoft Azure.
- Amazon has chosen MXNet as its deep learning framework of choice at AWS.
- Apache MXNet is a lean, flexible, and ultra-scalable deep learning framework that supports state of the art in deep learning models, including convolutional neural networks (CNNs) and long short-term memory networks (LSTMs).
- MXNet is designed to be distributed on dynamic cloud infrastructure, using a distributed parameter server, and can achieve almost linear scale with multiple GPUs or CPUs.
- It is powered by the high-level API library [Gluon](https://gluon.mxnet.io),
  - Gluon simplifies the creation of deep learning models.
  - the Gluon supports work with a dynamic graph.

## Dataset

- There are many dataset that are ready for various models to use.
- Training on the same dataset is a way to compare the quality of a certain mode.
- Some competition are hosted based on a certain dataset.
- Dataset are often used as the data source for acedemic researches.
- See a complete list [here](https://en.wikipedia.org/wiki/List_of_datasets_for_machine-learning_research).

### Image Data

##### MNIST

- It contains Database of handwritten digits.
- It has 60,000 images, created by National Institute of Standards and Technology in 1998.

##### [ImageNet](http://www.image-net.org)

- ImageNet is an image database organized according to the WordNet hierarchy (currently only the nouns), in which each node of the hierarchy is depicted by hundreds and thousands of images.
  - WordNet is a large lexical database of English. Nouns, verbs, adjectives and adverbs are grouped into sets of cognitive synonyms (synsets), each expressing a distinct concept.

##### [COCO](http://cocodataset.org/#home)

- Microsoft Common Objects in Context (COCO)
- Images are preprocessed with object highlighting, labeling, and classification into 91 object types.

##### [ADE20K](https://groups.csail.mit.edu/vision/datasets/ADE20K/index.html)

- Released by MIT CSAIL Computer Vision Group
- 20210 images are fully annotated with objects and, many of the images have parts too.
- 2000 images are fully annotated with objects and parts

### Numeric Data

##### [Iris Dataset](http://archive.ics.uci.edu/ml/datasets/Iris)

- It has measurement data for three types of iris plants taken by R. Fisher, released in 1936.
- The dataset contains a set of 150 records under 4 attributes - sepal length, sepal width, petal length, petal width.
