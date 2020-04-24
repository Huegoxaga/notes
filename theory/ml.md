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

- Support Vector Machines(SVMs)
- Decision Trees and Random Forests
- Logistic Regression
  - It will output the probability of an instance belonging one class, hence it is suitable for classification.
- k-Nearest Neighbors
- Linear Regression
- Logistic Regression
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
