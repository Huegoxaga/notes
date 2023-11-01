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

## Machine Learning Algorithms

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

- Linear regression is used to find the best fitting line of a set of data points
- Suitable for solving regression problems that find a predicted value
- Independent variable(s) is also named as Feature, Explanatory, or Input variable(s)
- Dependent variable is also named as Label, Response, or Output variable
- It outputs a set of coefficients for each feature and an intercept (the constant term) for a linear equation, the dependent variable will be the output value
  - It is a linear equation in `Number of Features + 1` dimensional space
- Ordinary least squares is used to calculate the best fit
  - it finds the minimum value of the square of the difference of y and y hat (Minimum RSS Error).
  - y hat is the predicted value while y is the actual value.
- Using square signify the data that is further away from the actual value
- Performance Measurment
  - Correlation Coefficient (r) - it ranges from `1` to `-1`
    - When it is close to `1`, there is a strong correlation between the predicted values and the real values
    - When it is close to `0`, the predicted values has nothing to do with the real values
    - When it is close to `-1`, there is an inverse correlation between the predicted values and the real values
  - Residual Sum of Squares or RSS Error - It calculates the sum of the square of the difference of `y` and `y` hat for each data point
  - Mean Squared Error (MSE) is the RSS divided by `N`, the number of $$y -\hat{y}$$ pairs
- Simple linear regression - The model will be a linear function with one constant, one dependent variable and one independent variable `x` times a coefficient.
- Multiple linear regression has one constant, one dependent variable and many combinations of independent variables times a coefficient.
  - The coefficient and the constant together are called the regressor vector
  - Each independent variable represents a different feature in a single row of data.
    - independent variables are called the feature vector
  - Dummy Variable - For a categorical featue each possible category will form a new field with value 0 or 1, when the current row of data is belonds this a certain category the value for this category will be 1 and others are 0.
    - Dummy Variable Trap - The number of this categorical independent variable will always be one less than the total number of the possible options since all others are 0 implys this record belong to the last category already.
  - The closed-form equation (One line solution) for minimized parameter of the function have the regressor vector equals $$\hat{\theta}=(X^TX)^{-1}X^TY$$, where `X` is the data matrix, it is called the Normal Equation
- For linear regression models all of the following assumptions must be achieved.
  - Linearity
  - Homoscedasticity
  - Multivariate normality
  - Independence of errors
  - Lack of multicollinearity

### Nonlinear Regression

#### Polynomial Regression

- When there is one independent variable, it becomes Polynomial Regression
- It is like multiple linear regression but the power of independent variable increases with the number of them
  - Second order polynomial forms a quadratic expression, it has 3 coefficients, it fits a parabolic curve
  - Third order polynomial has 4 coefficients, it fits an `N` shape curve, with one local maxima and one local minima
  - Fourth order polynomial has 5 coefficients, it fits an `M` shape curve, with two maxima/minima
  - Fifth order polynomial has 6 coefficients, the curve will bend one more time compare to the fourth order polynomial

### Decision Trees

- It can handle non-linear datasets.
- Decision Tree algorithms are often implemented as greedy algorithms
  - they always take the best looking split at each step, and never backtrack
- They can be treated as divide and conquer algorithms
  - they repeatedly divide big problems into smaller problems
- They have a naturally recursive implementation
- Pros and Cons:
  - Pros:
    - Interpretability - Decision trees can be easily read and understood by human beings. This makes them attractive, especially in domains such as medicine and the law where it is important not only to make good decisions, but to be able to understand and justify them
    - Feature Selection - Once constructed, decision trees tend to select only a few features as relevant (which means you don’t have to figure out which ones are most important)
    - Fast Classification - Once constructed, decision trees are very quick to categorize new examples
    - No Need to Normalize the data - Since decision trees don’t rely on any distance measurement (such as kNN), scaling or normalizing the features is not necessary
  - Cons:
    - High Error Rate on Small Data Sets - If you have a small training set, making vertical and horizontal cuts through the feature space might not be a good match for the natural distribution of the data, and can lead to high error rates
    - Slow Training - As the problem sets get bigger (more data, more features) decision tree algorithms tend to get exponentially slower to train
- Gini Impurity or Information Gain equations can be used to find the best fit
  - Gini Impurity is a measure of the probability of a randomly chosen element being misclassified if each split is adopted. When a split is pure, the Gini Impurity is 0.
  - Information Gain is a measure of how much each split reduces the amount of information needed to correctly classify the items. Both measures tend to come out better for splits that are more pure.
- Stopping criteria: By Default, most decision tree methods would keep splitting until every training item is correctly classified, to prevent overfitting a proper stopping strategy is required, the following parameters can be set:
  - The maximum depth for the tree
  - The maximum allowed number of leaf nodes for the tree
  - The minimum number of data points in a leaf
  - The minimum number of data points that can be split

#### Regression Trees

- It is used for regression problems
- It split the datapoints into groups based on the independent variables of a data point.
- It uses an information entropy algorithm to optimaize the split, each split will essentially add information to the dataset
- Each one of the split is called a leaf.
  - Each of the final split is called the terminal leaf
  - Terminal leaf is a result of a combination of final split sections from each independent variable
- A decision tree is a binary tree structure, each node check if one of the independent variable is greater or smaller than a certain value.
  - Nodes from the same depth are dealing with the same independent variable.
- The split add information to the datapoint and group them.
- The average of all data points in one terminal leaf will be calculated as the prediced value for all new data point if it falls in the split.
- When learning, it chooses splits based on minimizing the mean squared error of the resulting splits
- When predicting, A decision tree uses the average value of all data in the corresponding leaf node

#### Classification Trees

- It is used for classification problems
- similar to regression tree but each leaf represents one category
- Doesn't have to go the terminal leaves for result, it can be stopped at any time and return the probobility for each classification result

### Random Forests

- It is a type of ensemble machine learning algorithm called Bootstrap Aggregation or bagging.
  - Ensemble machine learning algorithm utlizes a single machine learning algorithm multiple times or uses different algorithm at the same time.
- For complicated data, a single decision tree can easily get deep and overfitting.
- It uses random subsets of the datapoints to form decision trees.
  - The number of data points in each subset should be set.
  - The total numbers of trees should be set.
- It uses random combination of features of a data point.
- It works for both classification tree and regression tree.
  - For regresssion: the average of all split from each decision tree will be used to make prediction.
  - For classification: the most common categories result among all trees will be used as the final result.

### k-Nearest Neighbors

- A supervised learning algorithm
- For Classification:
  - Select a `k` value(small interger value). For any new data point find its `k` nearest neighbors, then the new data point belongs to the category that is the same as most of its neighbors.
  - Euclidean Distance(geometrical distance, square root of the sum of the square difference) is often used.
- For regression:
  - Queries K-Nearest Neighbors and returns average value for the instance
- It does not scale well for large datasets
- `k = 1` leads to overfit
- Increase the number of `k` to avoid ties when counting the neighbor types
  - To avoid ties, one can use weighted voting where the weight of each count is the inverse of the distance
- When using kNN for regression, predict a value for a new example using the mean value of the k nearest neighbours
  - Optionally, using a weighted average, where the inverse of its distance is used to calculate a weighted average for neighbor data

### Logistic Regression

- It is a classification algorithm.
- Fit the linear regression result to fall within the range of 0 and 1 as the probabilities of an event using the logistic regression formula.
  - Subsitute `y` in the linear regression formula into the sigmoid function will return the logistic regression formula.
- It can generate `P` hat as predicted probability of a given value.
- It can return ethier 0 or 1 as `y` hat value if categorical results are preferred
  - return `y` hat as 1 if the probability is higher than a certain defined value and vise versa.
- Log-odds or Decision Surface is the original function that sum up all the input with its weight
  - $$z=g(x)=\theta_0+x_1\theta_1+\cdots+x_n\theta_n=x^T\theta=\theta^Tx$$
- Sigmoid function can be used to narrow down the output of the Log-adds equation between 0 and 1
  - When Log-odds equation is substituted into the Sigmoid function, it's called the hypothesis function
  - It's expressed as $$\hat{p}=h(z)=\sigma(x^T\theta)=\frac{1}{1+e^{-x^T\theta}}$$
  - Hypothesis function yields the probability of a input belongs to one class from 0 to 1
- Loss function is used to evaluate error. it compares the actual label with the predicted value then return the cost of the predicted value
  - If output is close to 1 when label is 1, the cost is low. If the the output is close to 0 when label is 1, the cost is high
  - A log function fits the purpose
  - Then substituting the hypothesis function into a log function, then take the average cost of all training data. The equation is known as the Categorical Cross-Entropy loss function or log-loss, $$-\frac{1}{N}\sum_{i=1}^{N}[y\ln(\hat{p})+(1-y)\ln(1-\hat{p})]$$ where `y` is the class of the `ith` instance. `y=1` for positive instance, and `y=0` for negative instance
- Lastly, gradient descent algorithm can be used to find the parameters that minimize the output of the log-loss function

### Support Vector Regression(SVRs)

- Compare to linear regression, instead of finding the best fitting line, it find the best fitting tube
- The tube, known as `ε-Intensitive Tube`, `ε` is the width of the tube, projected on the y-axis
- All data inside the tube will be ignore, so this algorithm allows a margin of error
- When the data can't be fit by a linear model, data can be projected on a kernel function and the best fitting plane (for 2-D data) can be found
  - Similar to tube for a line, The plane has a "thinkness", the predicted plane is surrended by one plane that is one `ε` above, and the other plane one `ε` below, all data within the block will be ignored. The data outside the block will be used to determine the best fitting plane

### Support Vector Machines(SVMs)

- It is a classificaton algorithm
- It focuses on finding the boundary, then make decision only based on the boundary
- The boundary is found to separate all data points with maximum margin.
  - One single point that is cloest to the boundary is selected from each category
  - Maximum margin is found to have the greatest distance to all of those selected points
- Those points that have the same closest distance to the boundary is called support vectors
- The boundary is called maximum margin hyperplane or maximum margin classifier
- The lines which are parallel to the maximum margin hyperplane and have zero distance to the support vectors are called positive or negative hyperplane
- Compare to other algorithm, `SVM` focuses on the looking at the extreme cases rather than analyze the generate features of a category

#### Kernel SVM

- When dataset is non-linear seperatble, a mapping function is used to move the data into a higher demension
  - For example, non-linear seperatble happens when data from category A is completed surrounded by data from category B
  - For example, a mapping function can move data from 2-D to 3-D with one catepory located at lower part and the other located at a higher position, then seperate by a plane
- However, mapping all data to a higher demension can be highly compute-intensive, so a kernel function is used as a model to fit and classify the data, some commonly used functions are:
  - `Gaussian RBF Kernel` - A steep mountain shape with a constant which defines the radius of the model
  - `Sigmoid Kernel`
  - `Polynomial Kernel`

### Bayesian Classification

- It calculates the likely-hood of one data belongs to one class by using the Bayes' Rule, given the probability of one class having a certian feature based on the training data
  - Bayes' Rule, $$P(CLASS|FEATURE)=\frac{P(FEATURE|CLASS)P(CLASS))}{P(FEATURE))}$$
  - The probabilities from different features can be multiplied to yield the final result
- For numerical features, Gaussian Naive Bayes can be used when values between features are independent and values of a feature follows normal distribution
  - It compares the test data's one feature with the mean of this feature from the training and yields the probability of each classes having the feature value to be close to the mean of all feature values from the training data
- Output can be read as a level of confidence in each possible class
  - The overall probability for the data to be each class is calculated, then the highest wins
- Both training and categorization are fast
- Bayesian classifiers can often do well with a small amount of training data
- There are very few learning parameters to tweak
- Naïve Bayes model uses multinominal distributions (multiple occurrance of one class)
- Complement Naïve Bayes is a a variation of Naïve Bayes model. It also takes the data from other classes into consideration. When a word appears in a complement class frequently, the appearance of this word can reduced the probability result of the target class
  - This method take more info into the training and yields better results
  - It works well when the dataset is imbalanced

### k-Mean Clustering

- It is an automatic clustering (belongs to unsupervised learning) that group together similar items in the data
- Automatic clustering algorithms are widely used for big data analysis
  - For example: Netflix divides its users into "taste communities" based on similarities, then uses membership in a taste community to customize its recommendations
- It uses distance calcuation to group data into clusters, so normalization and feature weighting are important for k-Mean clustering
- k-parameter specifies the number of clusters, the algorithm assign k number of random data points as centroids and group data into k groups around the centroids. For each group, calculate the mean distance from each point in group to the centroid of the group and use the mean value as the new centroid and repeat the process until there is no big improvement
- It is easy to implement. But it is slow on large data sets, and it takes multiple runs to get the optimal solution
- To measure the outcome, using the square sum of the distance from all data points to their assigned group centroid, the lower the sum, the better the outcome
  - This is known as the inertia or the Sum Squared Error (`SSE`) of the clusters
- For prediction, find the centroid that is closest to the new data, then the new data belongs to group represented by that centroid
- The `SSE` of clusters will always decrease as `k` increases. To find the right number of `k`, looking for the `elbow` where it is the last `k` that significantly decreases the `SSE`

### Neural Networks

- It was first introduced in 1980s, it was getting popular recently only becase the improved stroage and computing
- Can be used for both regression and classification tasks.
- Most Neural Networks are consist of a Feedforward Process and Backpropagation.
  - FeedForward Process(Nerual Network) uses static mapping as the output only depend on the input and the weights
  - Going from output to input and finding the better weights for the model using stochastic gradient descent with the chain rule
- In neural science, each neuron has dedrites(receiver) and axon(transmitter), millions of millions of neuron work together. sigals are passed through synapses.
- In neural networks, the processing unit is called neuron or node. The connection between neuron is also called synapse.
- In a fully connected NN, each neuron receives the output of all the neurons in its previous layer
- Overfitting and Underfitting - Underfitting(High Bias) implys a model that is too simply to make prediction, Overfitting(High Variance) implys a model that is learning too hard from the train data and too complicated to effectively and correctly make prediction.
  - The goal is to aim to build a model that is a bit overfitting and slightly adjust it to prevent overfitting.
  - The most important indicator of overfitting is the train set accurancy is much better than the test set.
- Hyperparameters are parameters used to build and train models.

#### Artificial Neural Networks(ANNs)

- The initial input values for the artificial neural network would be multiple features about one sample.
- The final output values for the artificial neural network could be either a predicted value(one output), a boolean value(one output) or categorical values(multiple output nodes)
- Each input value is associated with a weight, the neural network learns by adjusting the weight of each input value.
- Each neuron will have the sum of all input value times the weight, plus a bias term which equals to a dummy input $$x_0$$ with a value of `1` multiply by a weight of $$w_0$$
  - Each neuron itself is a linear binary classifier called perceptron
    - linear classifier guarantees to converge on a solution as long as the data is linearly separable
  - Perceptron model can be trained using perceptron learning algorithm
    - During training, weight and threshold are adjusted - increase / decrease all weight by input value times learning rate and decrease / increase threshold at the learning rate, based on the output result
    - Works on normalized data
- Activation function determine the output of each nerual based on the inputs' sum value
  - Most of them are non-linear functions
  - Activation functions used for the same layer of neurons are generally the same
  - Some of them are:
    - Threshold function - either yes or no(0 or 1) or it uses a bias value and the threshold is always 0
    - Sigmoid function - gradually increase(0 to 1) close to but never reaches 0 or 1
    - Hyperbolic Tangent - gradually increase(-1 to 1) close to but never reaches -1 or 1
    - Rectifier function - either 0 or linearlly grows from 0 to 1.
- Artificial Neurons are often referred to as units and named by their activation function: Threshold Units, Sigmoid Units, Tanh Units, and Rectified Linear Units(ReLU)
- A single layer feed forward nerual network(perceptron) is the base machine learning unit in ANNs.
- ANN or A multi-layer perceptron(a.k.a. MLP, or deep learning network) consists of a network of artificial neurons arranged into layers
  - An MLP should have at least one hidden layer with nonlinear activation function
  - The whole MLP represent a nonlinear function (𝐺(𝑋)). The goal is to design MLP to implement some desired nonlinear function
- The input values are called the input layer the output values are called output layer.
  - For regression task, it uses no activation function in the output layer. Instead, it just outputs the total activation level
  - The number of the neurons in the output layer is equal to the number of the outputs of the function
- Nodes in between are called hidden layers, each layers will process values and generate output for the next layer.
  - Each neuron in the same layer focuses on different aspects of the input info.
  - Hidden layers can have as many as possible, the neural network can be called deep learning if there are lots of layers of neurons in between.
  - ANNs with fewer hidden layers can be called shallow learning.
- The final output will be compared with the labeled target value, and use back propagation to adjust all weights of synapse, in order to achieve a higher accuracy.
  - `y` is the actually value, `y` hat the is output value.
  - A cost function is used to calculate the difference between `y` and `y` hat. The most frenquely used cost function is mean squared error which divides the squares of the difference of `y` and `y` hat by 2.
  - During each back propagation all of the weight for each synapse in the entire neural network are adjusted at the same time.
  - All the weight are initially set to a random small number close to zero
    - depending on where it starts, it might converge on a better or worse solution
  - Learning rate can be set to control how much the weights can be adjusted at a time.
- There are several ways of adjust the weights for ANNs:
  - Try all possible combination of weight values and calculate its cost function value, this is not practically since it takes billions of years.(curse of dimensionality)
  - Gradient Descent - adjust the combination of weights by calculating the slope, hence each trials will move closer to the minimum value. The sum of cost functions of all rows of data in the dataset are calculated in one guess.
    - It might find the local minimum if all the cost function values are not convex.
    - Each weight value will be moved towards right on its axis if the derivative of weight to cost function is positive, and left if negative
      - Old weight minus a positive learning rate times the derivateive is the new weight
    - Each row of data will generate a new weight, the average of the new weights will then be used in the next step
    - for a multilayer neural network,the error must be back-propagated to every individual weight through every possible path from the weights to the output
  - Stochastic Gradient Descent - Similar to gradient descent, but make adjustment based on cost function of every single row of data.
    - It will find the global minimum.
    - It is light weight and faster.
  - Mini-batch Gradient Descent - runs one batch of rows at a time.
- One epoach is the process of finding minimun cost function value of a batch of dataset after many times of iteration of the forward propagation and backpropagation adjusting of the weights.
  - One epoach will be repeated many times in order to improve accuracy.
- When determining the number of layers or nodes for a model, consider:
  - Each layer is computing a new representation of the classification task, with the final layer rendering the problem linearly separable. Examine the output of each hidden neuron as an interim classification computed along the way, and learn from these interim classifications
  - If a layer has more neurons than the one before, it can transform the input by adding new meta-features (e.g. a neuron could learn to output 1 if two of its inputs are large and 0 if they are small, ignoring the othersentirely). This can add information to be used by the next layer
  - If a layer has fewer neurons than the layer before, then it will send less information forward to the next layer. If features are redundant, or if it’s useful to combine features, this can be a good thing. Otherwise, it might hurt performance
  - As a general rule, the more layers the model have, the more epochs are needed to train the network

#### Convolutional Neural Networks(CNNs)

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
  - The cross-entropy formula is frequently used as the cost function (loss function) in CNNs.
  - Famous CNNs Architectures
    - CNNs Architectures are models with predefined structures
    - [LeNet-5](https://homl.info/lenet5)
      - Created by Yann LeCun in 1998 for MNIST dataset.
    - [AlexNet](https://homl.info/80)
      - Won the 2012 ILSVRC challenge
    - [GoogLeNet](https://homl.info/81)
      - Won the 2014 ILSVRC challenge
    - [VGGNet](https://homl.info/83)
    - [ResNet](https://homl.info/82)
      - Won the 2015 ILSVRC challenge
      - The CNN is called Residual Network.
    - [Xception](https://homl.info/xception)
      - A variant of GoogLeNet
    - [SENet](https://homl.info/senet)
      - Squeeze-and-Excitation Network
    - You Only Look Once(YOLO),
      - [YOLO](https://homl.info/yolo)
      - [YOLOv2](https://homl.info/yolo2)
      - [YOLOv3](https://homl.info/yolo3)
      - The model(weight) is trained using the `darknet` framework
        - It is written in C and CUDA
        - [Click](https://github.com/pjreddie/darknet) to view the repo from the original auther of the `darknet`
        - [Click](https://github.com/AlexeyAB/darknet) to view the modified version that supports Window OS

#### Recurrent Neural Networks(RNNs)

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
  - It keeps track of both of the long term and long term memeory
  - It uses four layers to filter and combine long and short term memory. Each layer get input from both current input vector and previous short-term state.
    - The main layer is used to generated output that will be added to the current long-term state.
    - The other three layers are gate controllers for the following gates:
      - forget gate - instruct what can be forget from the previous long-term state before adding new info.
      - input gate - controls what info from the main layer output can be added to the long term state.
      - output gate - uses a copy of the current long term state to generate the short term state.
- Gated Recurrent Networks(GRUs)
  - A refined and simplified version of the LSTM.
- A `Seq2Seq` model can be a RNN model that takes a sequence of items (words, letters, time series, etc) and outputs another sequence of items.
  - The use case is translation between two languages
  - A typical sequence to sequence model has two parts – an encoder and a decoder. Both the parts are practically two different neural network models combined into one giant network.
  - The task of an encoder network is to understand the input sequence, and create a smaller dimensional representation of it. This representation is then forwarded to a decoder network which generates a sequence of its own that represents the output.
  - The attention mechanism add weights to each work from the input sequence for encoder to improve the accuracy
    - Transformer is an application of the attention mechanism without using RNNs to record the order of words, it uses positional encoding instead
- Amazon SageMaker Sequence to Sequence
  - A supervised learning algorithm for convert sequence of tokens
  - the input is a sequence of tokens (for example, text, audio) and the output generated is another sequence of tokens.
  - Example applications include: machine translation, text summarization, speech-to-text.
  - It uses Recurrent Neural Networks (RNNs) and Convolutional Neural Network (CNN) models with attention as encoder-decoder architectures.

#### Hyperparameters Tuning

- For Neural Networks, hyperparameters tuning can be done during model building and model training.
- Build Model
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
- Train Model
  - Hyperparameters in the train model step is called Optimizer Hyperparameters.
  - Epochs - an epoch refers to one cycle through the full training dataset
    - If the number of epochs is too small the model will be underfitting, If the number of epochs is too large the model will be overfitting.
      - The best number of epochs will make the test set and the model have the best performance, this is called the Goldilocks point.
      - Early Stopping is the algorithm for finding the Goldilocks point, hence determine the best number of epochs to train the model.
        - It can be set to stop whenever accurancy decreace, or when accurancy doesn't improve in the next 10 or 20 epoch.
  - Learning rate
    - can be a value from 0.1 - 0.00001
    - It controls how fast weight changes during gradient descent.
    - Larger valuesmightlead to faster convergence. Smallervalues might yieldhigher accuracy
    - 0.01 suggested starting value.
    - If to small it will take longer steps to find the best weight, if too big the algorithm might not be able to find the best weight.
    - Learning rate decay is an algorithm that helps the model to find the best weight.
      - it can decrease the learning rate linearly or exponentially after a certain epochs.
      - Adaptive Learning Rate changes learning rate dynamically based on the data and training result after each epoch.
  - Minibatch size
    - It is 2^n and it can be anywhere from 1 - 256, 32 is a good starting point, then 64, 128, 256.
    - Larger batch size requires more computational resources, and it might cause out of memory errors.
    - Smaller batch size helps preventing the weight to be found at local minima, and it will be slow.
      - Shuffle training data in each epoch can reduce the chances of getting local minima
  - Regularization
    - Regularization refers to a set of mathematical techniques applied to the backpropagation algorithm to avoidoverfitting
    - Also known as the alpha parameter

### Reinforcement Learning

- It has an agent
- The agent makes observations and takes actions within an environment.
  - Observation is a snapshot of the environment states.
- An environment can be "solved" when an agent is built to achieve reward above a threshold.
- It receives rewards.
- The objective of the algorithm is to maximize rewards.
  - Rewards can be either positve or negative, only positive, or only negative. Maximize rewards is the same as minimize nagetive reward only, or maximize positive reward only, or both.
    - Similar to minmax algorithm which aim at minimizing the possible loss or maxinizing the possible gain
  - The rules to get rewards need to be designed to encourage the agent to make preferred behavior and punished promptly. It is not only about the outcome, the performance need to be quantified.
  - The punishment should not limit novel strategies which can provides creative solution to gain more rewards.
- The algorithm the agent uses to make action is called policy.
  - A stochasitc policy is a policy involves randomness.
  - Policy parameter are the variables that is used to determine the action.
  - Policy serach is the process of finding the policy parameter that will determine an action that maximize the reward.
  - Policy space is all the possible combination of the policy parameter.
  - Policy can be deterministic - all decision is based on a function of state.
  - Policy can be probabilistic - some decision is made randomly by using probability function(distribution)
- After make one action the agent completes one step. After complete all possible actions, the agent completes one episode.
  - The set of all possible action in a certain state is called the action space.
- Episode is consist of many state, each action will change the state from one to another.
  - The set of all possible state is called the state space.
  - The terminal state is a state that ends an episode.
  - The duration of an episode is from the initial state to the terminal state.
  - The state doesnot have to be a single observation, it can be a certain number of obeservation in a group.
- When a task is continuous and cannot be measured in an episode, it is called a non-episodic task.(e.g. control room temperature)
  - Most tasks can be assumed as episodic tasks.
- Generic algorithm is a way to reduce the policy space by generating a certain amount of policy as the first generation and only keep a small portion of the policy which has the most rewards, then generated offsprings from them. Offsprings is a copy of selected policys with some random variation. Keep creating generations until a good policy is found.
- Policy gradients(PG) evaluates the relationship between reward and policy parameters, then tweak the parameter following to the gradient towards higher rewards.
  - Reinforce Algorithm is one type of PG, It finds the gradients of the probability for each action by leting neural network play the game several times, then compute action's advantage after several episodes. Multiply the gradient vector by the action's advantages. Lastly use the mean of all gradient vecotrs to perform gradient descent.
- Creating an environment is the first step of RL
  - For real world learning, simulated environment is usually used first. The advantages are fast and cheap. Here are the libraries for generating environment.
    - Comprehensive environment generating tool: [OpenAI Gym](http://gym.openai.com/)
    - 3D physics simulation: [PyBullet](https://pybullet.org/), [MuJoCo](http://mujoco.org/)
- A neural network policies uses ANN with an observation(environment states) as input and the probabilities for taking each actions as output.
  - If every aspect of the environment is described, then past actions and observations can be ignored.
  - The action that will be taken based on the output will still be random based on the output's probabilities, it make the algorithm possible to try all actions with a certain known tendency.
- The Credit Assignment Problem - It is used to find out the credit of each step for the final consequence.
- The return for an action is a way to evaluate all the consequent rewards followed by an action, the reward immediately after the reward of the current action will have a discount by multiplying the discount factor(𝛾), the reward after that second action after the current action will have to multiply the discount factor square and so on, the sum of all the discounted rewards for an action is called the return.
  - Discount Factor(𝛾) typically ranges from `0.9` to `0.99`. The smaller the factor is, the sooner the consequent actions become not important as the factor approaches `0`.
  - The normolized returns from a large number of trails(episodes) are called the action advantage. It describes the good or bad of an action compares to all other possible actions.

#### Explore-Exploit Dilemma

- When making decision for max reward, two things need to be done.
  - Exploration - It the process of gathering data for making decision
  - Exploitation - Using the known info to make decision to maximize the reward
  - These two options cannot be done at the same time, this can be called explore-exploit dilemma
- Algorithm or methods for solving this dilemma are:
  - A/B Testing
    - also known as split testing, is the process of comparing two versions of a web page, email, or other marketing asset and measuring the difference in performance.
    - The performance can be measured using
      - click-through rate(CTR), number of click on the page divide by the number view of the page.
      - conversion rate - the number of sales divided by the total number of visitors.
  - Epsilon Greedy
    - Greedy means picking the bandit with highest Maximum Likehood Estimation(MLE) win rate without considering the sample size and the confidence
    - Epsilon is the percentage of random chioces this algorithm will make regardless the MLE
      - `ε` is typically around `5%` to `10%`
    - In conclusion Epsilon Greedy Algorithm uses greedy method to make decision with a percentage of random decision
    - `ε` will decrease the reward if it is a constant even when the sample size is big enough to make correct decision. Hence, it can decay over time:
      - `ε` can be proportional to `1/t` where `t` is the number of selection(steps)
      - Linearlly decay with a minimum value
      - exponential cooling
      - one over logarithm
  - Optimistic Initial Values
  - UBC1(Upper Confidence Bound)
  - Thompson Sampling(Bayesian Bandit)

#### Markov Decision Processes(MDPs)

- Markov Models
  - Hidden Markov Models is used by speech recognition
- Gridworld is a simple example environment for understanding RL concepts.
  - It is a `3 X 4` table
  - The state is determined by the location of the agent, the top left corner is described by tuple as `(0, 0)`
  - An agent starts at the bottom left corner, location `(2, 0)`
  - The agent move towards all direction available one at a time.
  - `(1, 1)` is a wall
  - When the agent get to point `(0, 3)` it have have one reward.
  - When the agent get to point `(1, 3)` it have lost one reward.
- The Markov Property only consider the propability of the predicted state to be dependent on its previous one or two states
  - when only one previous state is considered(bigram), this is called the first-order Markov assumption
  - the sequence of states before the dependent states will be ignored
- A single step of `MDP` consists of `{Current State, Action, Reward from the Action, State after the Action}` which can be represent by the tuple `{s, a, r, s'}`
  - the environment can be represented as `p(s', r| s, a)`
  - lowercase letter notations focus on a specific realiztion, replace the lowercase letter with uppercase plus subscribes like `t` or `t+1` to represent the random variables
  - compare to regular Markov Chain model, `r` and `a` are extra

## Ready-to-use Algorithms

- fastText
  - It is used for text data
  - fastText is a library for learning of word embeddings and text classification created by Facebook's AI Research (FAIR) lab
  - It is implemented through python ML library `Gensim`
  - Facebook makes available pretrained models for 294 languages
  - It provides a python libaray and a command line tool for word representation and classification related tasks
  - It is written in `C++` and supports multiprocessing during training
  - It is extended as BlazingText as an AWS Sagemaker built-in algorithm
  - It implements an unsupervised learning algorithm using text to vector(Word2Vec)
  - It implements a supervised learning algorithm that supports multi-class, multi-label classification
    - Multi-label can be done by using independent binary classifiers for each label with command `-loss one-vs-all` or `-loss ova`
  - Classification is achieved by
    - To predict a label for a sentence, a vector representation of the sentence is obtained by averaging the word embeddings vector results for each word in the sentence
    - Then, use linear classifier(multinomial logistic regression) to predict the label based on the vector value
  - Language models can have the following types
    - Unigram - each single word is considered as one unit, for a sentence contains words `A B C`. `A`, `B`, `C` are considered.
    - Bigram - each two words are considered as one unit, for a sentence contains words `A B C`. `AB`, `BC` are considered.
      - The model will then calculate the probability of `AB` given `A` by counting and dividing the occurrence of `AB` by `A`, it aims to find all probability of each word for all other words in a large text corpus
        - Add-one smoothing - During prediction, the probability of any word followed by `A` cannot be `0`, to introduce the possibility during training, this case should be included in the calculation, so the calculation should be dividing the occurrence of `A` followed by `B` plus `1` over the number of `A` plus the total number of unique words in the training corpus
      - Once the model has the all the probability info, it chains the predicted words into a sentence, as `P(A,B,C) = P(C|B)P(B|A)P(A)`
        - based on the Bayes rule, `B C` depended on `A` also need to be found by doing counting, however, `B C` depended on `A` is trigram and will not be used, based on Markov Assumption, what we see only depends on the what we see in previous step, so the term `B C` depended on `A` will be ignored in the calculation, it is also easier to model because the occurrence of shorter word sequences (two word phrases) is higher than long sentences in the training corpus
        - Use log probability in the actually calculation to avoid the product of chained probability reaches zero, add up the logarithm of the probability, and get the average of this log value for each word by dividing the sum by the number of words in a sentence, to avoid biase introduced by various sentence length
    - N-gram - each group of consecutive N words are considered.
      - fastText even consider n-gram for group of characters within a word("ora", "ran", "ang", "nge" when `minn` is 3) and make it different from `Word2Vec`. Hence, it works good with misspelled words.
      - Default `minn` is 3, `maxn` is 6
    - Bigram or N-gram will take the sequence of words into consideration. Unigram will not.
  - The hierarchical softmax is a loss function that approximates the softmax with a much faster computation
  - When dealing with languages that does not contain space in between word, word segementation is required
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
- Amazon Sagemaker Linear Learner
  - Supervised ML algorithm.
  - An AWS sagemaker built-in algorithm for linear regression and logistic regression
  - It works for for regression, binary classification and multi-class classifcation problems.
- XGBoost
  - Supervised ML algorithm for regression and classification problems
  - It is evolved from decision tree in the following order
    1. Decision Trees - A graphical representation of possible solutions to a decision based on certain conditions.
    2. Bagging - Bootstrap aggregating or Bagging is a ensemble meta-algorithm combining predictions from multiple decision trees through a majority voting mechanism.
    3. Random Forest - Bagging-based algorithm where only a subset of features are selected at random to build a forest or collection of decision trees.
    4. Boosting - Models are built sequentially by minimizing the errors from previous models while increasing(boosting) influence of high-performing models.(New model trained by data points that can’t correctly predict by previous model until no further improvement can be made.)
    5. Gradient Boosting - Gradient Boosting employs gradient descent algorithm to minimize errors in sequential models.
    6. XGBoost - Optimized Gradient Boosting algorithm through parallel processing, tree-pruning, handing missing values and regularization to avoid overfitting.
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
- Amazon SageMaker Latent Dirichlet Allocation
  - A unsupervised learning algorithm for topic modeling
  - Group documents by user specified number of topics
  - For documents, it assigns a probability score for each topic
- Amazon SageMaker Neural Topic Model
  - Similar to Amazon SageMaker Latent Dirichlet Allocation

## Data Preprocessing

- Ideally training data should be balanced
  - For balanced data, each class should have (almost) the same amount of samples
  - Otherwise, rebalancing the training set or weighted voting should be used

### Numeric Data Preprocessing

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
       - Min-Max Norm uses `value - min / max - min` for each data
       - L1 Norm uses `Value / Sum of the Abs of All Values` for each data
       - L2 Norm uses `Value / Root of Sum of Square of All Values` for each data
   - Dummy variables do not need to apply feature scaling.

### Image Preprocessing

- The color value of the images can be rescaled from `0-255` to `0-1` to simplify the data.
  - The training data and testing data should use have the same recaling setting.
- Image augumentation step alteres the images by zooming, flipping and shearing to provide variaties for training.
- Labeling
  - [LabelImg](https://github.com/tzutalin/labelImg) is a graphical image annotation tool.
    - Annotations are saved as XML files in PASCAL VOC format, the format used by ImageNet. Besides, it also supports YOLO format.
  - [VoTT](https://github.com/microsoft/VoTT) is an open source annotation and labeling tool for image and video assets.
    - VoTT can be installed as a native application or run from source. VoTT is also available as a stand-alone Web application and can be used in any modern Web browser.
    - they can be exported into a variety of formats:
      - Azure Custom Vision Service
      - Microsoft Cognitive Toolkit (CNTK)
      - TensorFlow (Pascal VOC and TFRecords)
      - VoTT (generic JSON schema)
      - Comma Separated Values (CSV)
- Image related task can be:
  - Classification: what is contained in an image
  - Localization: specify the location of a single object in an image
  - Detection: Object Detection specifies the location of multiple objects in the image
  - Segmentation: Identify the shapes of different objects
- Use the following formula to convert color image to grey scale
  - `gray_image = 0.2989 * red_channel + 0.5870 * green_channel + 0.1140 * blue_channel`
- A histogram provides infomation on the distribution of intensity of an image
  - The Histogram Equalization algorithm enhances the contrast of images by flattening the histogram chart
- Point processing process image pixel by pixel
  - Negative image uses the max intensity substract by the intesnsity of each pixel to replace the original pixel
  - Thresholding sets a threshold to generate a binary image
    - The gap on the histogram can be chosen as the threshold
- Neighbourhood operations perform the calculation for each pixel with the information from its surrounding pixels
  - A 3 by 3 or 5 by 5 square kernel `A` around the pixel is used in the calculation
  - Some simple neighbourhood operations include:
    - Min: Set the pixel value to the minimum in the neighbourhood
    - Max: Set the pixel value to the maximum in the neighbourhood
    - Average: Set the pixel value to the average value in the neighbourhood
    - Median: The median value of a set of numbers is the midpoint value in that set (e.g. from the set [1, 7, 15, 18, 24] 15 is the median). Sometimes the median works better than the average
  - Filtering operation
    - the new pixel intensity is obtained by $$A\cdot B$$, where `B` is the filter matrix of the same size
    - Low pass filter (Smoothing operation), it can reduce noise and highlight gross details
      - Simple averaging filter performs a smoothing operation. e.g. it has `1/9` for all of the values in a `3 x 3` filtering matrix
      - Weighted Smoothing Filters add a weight to the averaging. e.g. the filtering matrix can be $$\begin{bmatrix} \frac{1}{16}&\frac{2}{16}&\frac{1}{16} \\ \frac{2}{16}&\frac{4}{16}&\frac{2}{16}\\\frac{1}{16}&\frac{2}{16}&\frac{1}{16} \end{bmatrix}$$
    - High pass filters (Edge Detection, Sharpening), it emphasizes fine details in the image
      - Example filters: $$\begin{bmatrix}0&-\frac{1}{4}&0\\ -\frac{1}{4}&1&-\frac{1}{4}\\0&-\frac{1}{4}&0 \end{bmatrix}$$ or $$\begin{bmatrix}-\frac{1}{8}&-\frac{1}{8}&-\frac{1}{8}\\-\frac{1}{8}&1&-\frac{1}{8}\\-\frac{1}{8}&-\frac{1}{8}&-\frac{1}{8} \end{bmatrix}$$
      - Note that all coefficients sum to `0`

### Timeseries Data Preprocessing

### Text Data Preprocessing

#### Normalization

- Clean text
  - Removal of infrequent words - The number of unique words can be reduced greatly if many infrequent words are removed, this procedure can incresed the training speed, and might reduce the accuracy
  - Removal of infrequent words - If a word appears too frequently, it might not prove to be very useful for classification. Removing frequent words might speed things up a little bit and also make the classification task easier
- leave out all double qoutes
- Stop Words - are words that are not providing useful information and will be excluded from the text.
- Stemmer - are used to transform various forms of a word to a common one. Ex, different tense of a verb to the present tense.
- Replace all non alphapetic and numerial character to space.
- Use lower case for words
- Example command for a quick cleanup, `cat <filemane>.txt | sed -e "s/\([.\!?,'/()]\)/ \1 /g" | tr "[:upper:]" "[:lower:]" > <filemane>.preprocessed.txt`

#### Tokenization

- Tokenization of raw text is a standard pre-processing step for many NLP tasks. For English, tokenization usually involves punctuation splitting and separation of some affixes like possessives
  - Break a sentense apart based on punctuations and possessives
- Other languages require more extensive token pre-processing, which is usually called segmentation.
  - Break a sentense apart based on words, when a word in a language can be various number of characters without spacing and punctuations
  - Some commonly used tool are shown as below: - [Stanford word segmenter](https://nlp.stanford.edu/software/segmenter.html) for Chinese and Arabic. - [Mecab](https://taku910.github.io/mecab/) for Japanese - [UETsegmenter](https://github.com/phongnt570/UETsegmenter) for Vietnamese - [Europarl](http://www.statmt.org/europarl/) for Latin, Cyrillic, Hebrew or Greek scripts - ICU tokenizer - [Click](https://arxiv.org/abs/1802.06893) to learn more

#### Word Representations

- one-hot vectors - a way to represent a word in a set vocabulary by an vector (array), each word in the vocabulary is associated with one index and the word is represented by an array that has `1` on the correponding index and everywhere else is `0`
  - The demesion of the vector equals the number words in the vocabulary
- Bag of words - It is a way to preprocess text data by using an array of count for all unique words to record the occurrence of each word in the text data.
  - Each list of occurrence is a data record that has one label attached
    - Then, the data can be fed into other algorithms. Ex, ANNs or Native Bayes for classfication.
  - Bag of words fits the multinominal model (study the different number of occurrance of the same outcome)
  - The list of words can be ordered by its frenquent among all words in the text data
    - Most frenquent words are important, words that are not frenquently seen in the text are usually names, places, holiday etc.
    - Taking frenquent vocabulary can reduce the demension
- Set of words - a document is represented as a list of 1's and 0's indicating the presence or absence of each vocabulary word in the document
  - It fits the Bernoulli model (binary outcomes)
  - It contains less information than the bag of words
- Term Frequency-Inverse Document Frequency (tf-idf) - For each feature, it computes the term frequency and multiply it by the inverse document frequency
  - the term frequency is the number of times the word appears in the document divided by number of words in the document
  - the inverse document frequency is the number of documents in the corpus divided by number of documents with that term in it
  - It increases the weight of a word if it appears in fewer documents
  - It fits multinominal and Gaussian model
- Word2Vec
  - Word2Vec are used to predict a vector representation of a word using a model trained by a text corpus
    - It is a word embedding(representation) method, word embedding is the collective name for a set of language modeling and feature learning techniques in natural language processing (NLP) where words or phrases from the vocabulary are mapped to vectors of real numbers
      - language model is a model of the probability of a sequence of words (sentence)
    - it converts every word in a large text corpus into a vector
    - text corpus is a language resource consisting of a large and structured set of texts
    - It can predict any word if all its subwords presented in the training text corpus
      - Subwords are groups of letter within a word
  - Word2vec is a group of two-layer neural networks models that are used to produce word embeddings
    - It can be obtained using two methods: Skip Gram or `CBOW`
      - skipgram - It predicts the target using a random close by word of the target word, each close-by word are considered indiviaully
      - cbow `(continuous(common)-bag-of-words)` - It uses the sum of a certain range of close-by word for prediction
      - In practice, the skipgram models works better with subword information than cbow
      - CBOW is faster and has better representations for more frequent words
  - It has the following parameters:
    - The subwords are all the substrings contained in a word between the minimum size (minn) and the maximal size (maxn). Usually, all the subword are between 3 and 6 characters
    - The dimension (dim) controls the size of the vectors, the larger they are the more information they can capture but requires more data to be learned
      - any value in the 100-300 range is as popular
      - if they are too large, they are harder and slower to train
  - Word2Vec is a text preprocessing step for downstream NLP, Sentiment analysis, named entity recognition and translation.
  - Words that are semantically similar have vectors that are closer to each other
  - The average of vectorized words in a sentence can the be fed into logistic regression classifiers or any other models
- GloVe is another unsupervised learning algorithm for obtaining vector representations for words.
  - It puts emphasis on the importance of word-word co-occurences to extract meaning rather than other techniques such as skip-gram or bag of words
  - GloVe creates a global co-occurrence matrix by estimating the probability a given word will co-occur with other words.
  - it proves to perform better than Word2vec in the word analogy tasks.

## Model Evaluation

### Evaluating Regression Models

#### Root Mean Square Error(RMSE)

- The smaller the better

#### Residual Histograms

- Residual value equals to the actual value minus predicted value.
- Residual Histograms have Residual value for each prediction on x-axis and count on y-asix.
- It can represent the distribution of the residual if 0 is in the center and the range of x-axis is small, the model is good.

### Evaluating Classification Models

- Confusion Matrix
  - It is a table which has predicted result on one axis and actual result on the other axis, then for a binary classification each prediction has four kinds of outcome:
    - True Positive - Correctly predicted a positive result.
    - True Negative - Correctly predicted a negative result.
    - False Positive(type I error) - A false prediction which is predicted as Positive.
    - False Negative(type II error) - A false prediction which is predicted as Negative.
  - Accuracy represents the percentage of correct prediction, it equals `(True Positive + True Negative) / All`
    - Accuracy paradox - It happens when only use accuracy rate as the reference to consider the performance of a model. because the number of the actual positive and negative results does not always be the same
  - Because of accuracy paradox, precision and recall are preferred:
    - Precision - it equals `True Positive / (True Positive + False Positive)`. For an object detection model, low precision means many detected objects are wrong objects
    - Recall - it equals `True Positive / (True Positive + False Negative)`. For an object detection model, low recall means many objects are missed
    - Precision and recall move in opposite directions under different parameter settings, hence precision vs. recall graph is a good way to represent the performance of a model
    - The overall best result for both precision and recall happens when they are close, this is where one model achieves the best performance
    - F1 score is defined as the weighted harmonic mean of the precision and recall, it equals `2*((precision*recall)/(precision+recall))`
  - For Multiclass classifier that has `n` classes, use confusion matrix with shape `n X n`. There are different ways to calculate the average
    - The micro-average is calculated by expanding the formula to include related `TP`, `TN`, `FP`, `FN` for all class
      - For example the micro-average for precision for two classes classifier is calculated using `(TP1 + TP2) / (TP1 + TP2 + FP1 + FP2)`
    - The macro-average for accuracy, precision, recall or F-1 score is calcualted by taking the average of accuracy, precision, recall and F-1 score result of different class, respectively
    - The weighted-average happens when the macro-average calculation applys a weight based on the instance percentage of one class
- Area Under Curve (AUC)
  - AUC is the area of a curve formed by plotting True Positive Rate against False Positive Rate at different cut-off thresholds
  - Good model have AUC closer to 1
  - 0.5 is considered random guess
  - Closer to 0 is unusual and it indicates model is flipping results
- CAP
  - The number of correct prediction is on the y-axis. The total number of prediction is on the x-axis.
  - A a random prediction will generate a linear line.
  - A better model will generate a curve with higher slope at the beginning
  - There is a perfect linear model that get every prediction correct.
  - If the area under the line for random model is `Sr` and `Sp` for the perfect model, the area under the curve for the model is `S`. The accuracy rate can be calculated with `(S-Sr)/(Sp-Sr)`.
  - A good model can be determined by curve when the x value is in the middle of x-asix the point on the curve will have y-value at above 70% of the y-axis
- Use one class again all other classes for multiclass classifier.

## Machine Learning Frameworks(Libraries)

- A ML frameworks is a libray for a certain programming language which contains various ML algorithm as methods.

### [TensorFlow](https://www.tensorflow.org)

- It was developed by the Google Brain team for internal Google use. It was released under the Apache License 2.0 on November 9, 2015.
- It is the most popular deep learning framework for Python
- There are also experimental interfaces available in JavaScript, C++, Java and Go, C# and Julia.
- TensorFlow can run on multiple CPUs and GPUs
- TensorFlow is available on 64-bit Linux, macOS, Windows, and mobile computing platforms including Android and iOS.
- Static computation graph - The model should be defined first then compile and train it after.
- TensorFlow 2.0 uses Keras as its official high-level API

### [PyTorch](https://pytorch.org)

- PyTorch is an open source machine learning library based on the Torch library
  - Torch is an open-source machine learning library, a scientific computing framework, and a script language based on the Lua programming language.It provides a wide range of algorithms for deep learning
- PyTorch also has a C++ interface
- It is developed by Facebook's AI Research lab (FAIR).
- Dynamically Updated Graph - The model is compile after each line of the model definition
- PyTorch is suited for small projects and prototyping

### [Sonnet](https://sonnet.readthedocs.io/en/latest/)

- Sonnet is a high level library to build complex neural network structures in TensorFlow.
- It is designed to create neural networks with a complex architecture by DeepMind.

### [MXNet](https://mxnet.apache.org)

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

#### MNIST

- It contains Database of handwritten digits.
- It has 60,000 images, created by National Institute of Standards and Technology in 1998.

#### [ImageNet](http://www.image-net.org)

- ImageNet is an image database organized according to the WordNet hierarchy (currently only the nouns), in which each node of the hierarchy is depicted by hundreds and thousands of images.
  - WordNet is a large lexical database of English. Nouns, verbs, adjectives and adverbs are grouped into sets of cognitive synonyms (synsets), each expressing a distinct concept.

#### [COCO](http://cocodataset.org/#home)

- Microsoft Common Objects in Context (COCO)
- Images are preprocessed with object highlighting, labeling, and classification into 91 object types.

#### [ADE20K](https://groups.csail.mit.edu/vision/datasets/ADE20K/index.html)

- Released by MIT CSAIL Computer Vision Group
- 20210 images are fully annotated with objects and, many of the images have parts too.
- 2000 images are fully annotated with objects and parts

### Numeric Data

#### [Iris Dataset](http://archive.ics.uci.edu/ml/datasets/Iris)

- It has measurement data for three types of iris plants taken by R. Fisher, released in 1936.
- The dataset contains a set of 150 records under 4 attributes - sepal length, sepal width, petal length, petal width.
