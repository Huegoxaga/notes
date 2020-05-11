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
  - online learning or batch learning
    - whether or not the learning process is done at one time(batch learning) or consequently overtime based on a stream of incoming data(online learning)
    - batch learning is also called offline learning.
    - batch learning requires a lot of computing resources while online learning uses data as mini batch which can be cheap and fast.
    - online learning is vulnerable to bad data.
  - instance-based learning or model-based learning
    - instance-based will compare new data with sample data then make judgement.
    - model-based learning will generalize sample data, then processing new data based on the model.

## Machine Learning Algorithms

- Decision Trees and Random Forests
- K-Means
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
- Eclat

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
- The algorithm uses information entripy to split datapoints into groups based on the independent variables of a data point.
- Each one of the split is called a leaf.
  - Each of the final split is called the terminal leaf.
- A decision tree is a binary tree structure, each node check if one of the independent variable is greater or smaller than a certain value.
  - Nodes from the same depth are dealing with the same independent variable.
- The split add information to the datapoint and group them.
- The average of all data points in one leaf will be calculated as the prediced value for all new data point if it falls in the split.

### Random Forests

- It is a type of ensemble learning.
  - A algorithm that utlizes a single machine learning algorithm multiple times or uses different algorithm at the same time.
- It uses subsets of the datapoints to form decision trees.
- The average of all split from each decision tree will be used to make prediction.
- It works for both classification tree and regression tree.

##### Random Forests for

### k-Nearest Neighbors

- A classfication algorithm
- Select a `k` value(small interger value). For any new data point find its `k` nearest neighbors, then the new data point belongs to the category that is the same as most of its neighbors.
- Euclidean Distance(geometrical distance, square root of the sum of the square difference) is often used.

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
- In neural science, each neuron has dedrites(receiver) and axon(transmitter), millions of millions of neuron work together. sigals are passed through synapses.
- In neural networks, the processing unit is called neuron or node. The connection between neuron is also called synapse.

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
  - Generally, the ideal number of nodes in each hidden layer is close to half of the input layer nodes plus output layer nodes.
    - Fine tuning can be made to improve, however this approximate number is good enough for determining the number of nodes for all hidden layers.
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

## Steps for a Machine Learning Project

### Data Preprocessing

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

##### Timeseries data preprocessing

##### Text data preprocessing
