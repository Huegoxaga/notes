# Probability & Statistics

## Probability

- Probability is the prediction of a certain outcome when something occurs
  - represented by a number between 0 and 1 which expresses the chance that an event will occur
- Experiment - An activity or measurement that results in an outcome
- Sample space - All possible outcomes of an experiment
- All the possible outcomes(an elements or member, same points) of experiments make the sample space(a set, denoted by omega Ω). `S = {a,b,c,d,….}`.
- An event is any collection (subset) of outcomes contained in the sample space S
  - An event is simple if it consists of exactly one outcome and compound if it consists of more than one outcome
  - Mutually Exclusive Events: If one event occurs, the other cannot occur
  - Exhaustive Events: A set of events is exhaustive if it includes all of the possible outcomes of an experiment
- Favourable outcomes or successes make an event that is the subset of the sample space
- Venn diagram is used to describe sets relationship: intersection, union, compliment, adjoint, subset and difference(minus sign). total box is the sample space omega.
- `n(set)` is the cardinal number of set(the number of its element)
- `A'` is the complement of set A
- A and B means A intersect with B, `A ∩ B`
- A or B means A union B, `A ∪ B`
- Laws
  - demorgan's laws - `(A ∪ C)' = A' ∩ C'` `(A ∩ C)' = A' ∪ C'`
  - events for not A - `n(U) = n(A) + n(A')` if U contains all events
  - events for A or B - `n( A ∪ B ) = n( A ) + n( B ) − n( A ∩ B )` when A and B are not mutually exclusive
    - When A and B are mutually exclusive `n( A ∩ B ) = 0`, and `n( A ∪ B ) = n( A ) + n( B )`
  - events for A and B - `n ( A ∩ B)`
  - if A ⊂ C, B ⊂ C, then A ⊂ C
    - `A ∪ B = B ∪ A`
    - `A ∪ (B ∪ C) = (A ∪ B) ∪ C + A ∪ B ∪ C`
    - `A ∩ B = B ∩ A`
    - `A ∩ (B ∩ C ) = (A ∩ B) ∩ C = A ∩ B ∩ C`
    - `A ∩ (B u C) = (A ∩ B) ∪ (A ∩ C)`
    - `A ∪ (B ∩ C) = (A ∪ B) ∩ (B ∪ C)`
    - `A - B = A n B'`
  - if A ⊂ C then C' ⊂ A'
    - `A ∪ null = A` `A ∩ null = null`
  - `U` means universe, if A ∪ U = U
    - then A ∩ U = A
  - `A = (A ∩ B) ∪ (A ∩ B')`
- The probability of an event as a numerical value is determined in one of three ways:
  - Subjective Probability - Based on experience or intuition. (guess)
  - Relative Frequency Probability (empirically, experimentally) - Based on historical and geological records.(gather data)
  - Classical Probability (theoretically, mathematically) - Based on predictable parameters. (coin has two sides)
- The Law of Large Numbers (LLN) says that the long-run relative frequency of repeated independent events gets closer and closer to a single value.
  - The single value is used to represent the probability of the event.
- The probability of an event is the number of outcomes in the event divided by the total number of possible outcomes(sample space).
  - A probability function `P` returns a number between 0 and 1. For any event A, `0 ≤ P(A) ≤ 1`.
- Probability Assignment Rule:
  - The probability of the set of all possible outcomes of a trial must be 1.
  - P(S) = 1 (S represents the set of all possible outcomes.)
  - independent events are not disjoint, and dependent events are disjoint.
- Complement Rule:
  - The set of outcomes that are not in the event A is called the complement of A, denoted A with superscript c.
  - The probability of an event occurring is 1 minus the probability that it doesn’t occur.
- Addition Rule:
  - Events that have no outcomes in common (and, thus, cannot occur together) are called disjoint (or mutually exclusive).
  - For two disjoint events A and B, the probability that one or the other occurs is the sum of the probabilities of the two events.
  - `P(A or B) = P(A) + P(B)`, provided that A and B are disjoint(known as independent or mutually exclusive).
  - theoretically the probability of a independent event does’t change after the occurrence of other events.
- Multiplication Rule:
  - For two independent events A and B, the probability that both A and B occur is the product of the probabilities of the two events.
  - `P(A and B) = P(A) x P(B)`, provided that A and B are independent.
- The General Addition Rule:
  - when events are not disjoint, this earlier addition rule will double count the probability of both A and B occurring.
  - For any two events A and B, P(A or B) = P(A) + P(B) – P(A and B).
- Marginal probability - The probability that a given event will occur. No other events are taken into consideration, e.g. `P(A)`
- Conditional probability
  - A probability that takes into account a given condition is called a conditional probability
  - It is denoted as P(B|A) and pronounce it "the probability of B given A."
  - To find the probability of the event B given the event A(after event A occur), we restrict our attention to the outcomes in A. We then find in what fraction of those outcomes B also occurred.
  - `P(B|A) = P(A and B) / P(A)`
  - `P(A)` cannot equal 0, since A has occurred for sure
  - If `A` and `B` are independent, `P(A| B) = P(A)`
  - A and B is A and B happens not equivalent to `P(A)*P(B)`, because A and B is not two steps.
  - For condition possibility, events are not independent , hence they use the previous multiplication rule now has a general version: For any two events A and B, `P(A and B) = P(A) x P(B|A)` or `P(A and B) = P(B) x P(A|B)`
  - The Law of Total Probability - If the events A1, A2,..., Ak be mutually exclusive and exhaustive events. Then for any other event B, P(B) equals the sum of all `P(B|Ai)P(Ai)`
- Odds
  - Odds(in favour of) for an event `A = P(A)/P(not A)` (`P(A)` to `P(not A)`)
  - Odds against(on) an event A = P(not A) / P(A) (`P(not A)` to `P(A)`)
  - for gambling `odd against * invest money = prize`
- General possibility for binary situation: `P(k-head, n-k-tails) = nCk/2^n`
- For at least one occurs after n times: `P(at least one occurs) = 1 - [P(no occurs)]^n`
- Geometric probability solves how long it takes to achieve a success.
  - If `x` is the number of times it takes for success, then, `P(x) = q^x-1 * p`
- Bernoulli trials satisfy the following properties:
  - there are two possible outcomes (success and failure).
  - the probability of success, p, is constant.
  - the trials are independent.
    - The 10% condition: Bernoulli trials must be independent. If that assumption is violated, it is still okay to proceed as long as the sample is smaller than 10% of the population.
- A Binomial model tells us the probability for a random variable that counts the number of successes in a fixed number of Bernoulli trials.
  - It is a special type of multinomial model when there are only two outcomes
  - Two parameters define the Binomial model: n, the number of trials; and, p, the probability of success. We denote this Binom(n, p).
  - In n trials, there are nCk ways to have k successes. (`nCk = n! / k!(n - k)!`)
  - Hence, for a Binomial distribution model the probability of successes equals `nCk * p^x * q^n-x`. where
    - `p` = probability of success
    - `q` = `1 – p` = probability of failure
    - `X` = number of successes in n trials
    - if x can have more values, the probabilities for different x values can be added together

### Bayes' theorem

- Theorem 1 - if A must result in one of the mutually exclusive events A1,A2,A3…An then, `P(A1nA2nA3) = P(A1)P(A2|A1)P(A3|A1nA2)`
- Theorem 2 - `P(A) = P(A1)P(A|A1)+P(A2)P(A|A2)+….+P(An)P(A|An)`
- From 1 and 2 bayes' theorem can be derived. If A must result in one of the mutually exclusive events A1,A2,A3,Ai,...,An. It has extended form as $$P(A_i|B) = \frac{P(B|A_i)P(A_i)}{\sum_{i=1}^n P(B|A_i)P(A_i)}$$ where $$P(B)= \sum_{i=1}^n P(B|A_i)P(A_i)$$, or in short $$P(A|B)= \frac{P(B|A)P(A)}{P(B)}$$.
- True Negative and False Positive divide by the actual negative count will get the True Negative rate and False Positive rate.
- True Positive and False Negative divide by the actual positive count will get the True Positive rate and False Negative rate.
- Accuracy rate - correct prediction count over the total prediction count.
- Error rate - wrong prediction count over the total prediction count.
- `Sensitivity of a test = true positive / all actual positive = true positive / (True Positive + False Negative))` Ex, Test is 95% sensitive, when 95 positive result are predicted out of 100 known positive cases. The 5 false negative are called escapes.
- `Specificity of a test = true negative / all actual negative = true negative / (True Negative + False Positive))` Ex, Test is 95% specific, when 95 negative result are predicted out of 100 known negative cases.
- `Prevalence = Actual Positive / Total`
- `Positive Predicted Value(PPV) = true positive / total positive`
- `Negative Predicted Value(NPV) = true negative / total negative`
- `Precision = True Positive/(True Positive + False Positive)`
- `Recall = True Positive/(True Positive + False Negative)`
- F1 Score = harmonic mean of Precision and Recall = `2*Precision*Recall / (Precision + Recall)`
  - F1 Score closer to 1 is better. Closer to 0 is worse.
- See more [here](https://en.wikipedia.org/wiki/Precision_and_recall#Recall)
- Confusion Matrix can be used to determine the outcome - It is a table which has predicted result on one axis and actual result on the other axis.
  - True Positive - Correctly predicted a positive result.
  - True Negative - Correctly predicted a negative result.
  - False Positive - A false prediction which is predicted as Positive.
  - False Negative - A false prediction which is predicted as Negative.
- Tree Diagram can be used to determine the outcome:
  - Each actual result will have a branch, each branch can have all predicted result.

### Markov Chains

- A Markov chain is a mathematical system that experiences transitions from one state to another according to certain probabilistic rules
- It is used predict the future state(matrix $$X_1$$) by multiply the matrix of transition probabilities(P) by the current state(matrix $$X_0$$).
  - Each current or future state has `N` elements and represented by a `N X 1` matrix. During each step, each element will
    - lose part of it to other element
    - gain from other element
    - have part of it unchanged
  - The probability(transition) matrix is a `N X N` matrix. It has element from first to last on each row from left to right, and first row represents how each element will transit to the first element, and second row represents how each element will transit to the second element and so on.
    - The probability matrix should be stochastic which means all element in each column will add up to 1.
  - The probability matrix should be a regular matrix which means for all P^n(n>1) all its element should be greater than one.
  - Using the transpose of all the matrix can be an alternative way to write the formula. In this case multiply the initial state by the probability matrix.
    - The probability matrix should be stochastic which means all element in each row will add up to 1.
  - To calculate the future state after n-steps: $$X_n = P^n X_0$$
  - After certain interation the state matrix will be stable and won't change, then it is called the stable distribution matrix($$\overline{X}$$).
  - The $$P^n$$ for the stable distribution matrix is the stable probability matrix, it will keep the same when `n` is greater than a certain value, the production of stable probability matrix with any initial state will return the same stable distribution matrix.
  - Every column(when state represented by a `N X 1` matrix) of a stable probability matrix is a stable distribution matrix.
  - When the stable probability matrix or the stable distribution matrix is found, all probability matrix from P to P^n together, are called regular markov chain.
  - If $$P \overline{X} = \overline{X}$$, then $$\overline{X}$$ is the stable distribution matrix and $$\overline{P}X_0 = \overline{X}$$.
  - $$P \overline{X} = \overline{X}$$ can be used to solved for stable distribution matrix based on any known probability matrix.
  - If a Markov chain has one more elements never lost part of it to other elements, it is called the absorbing Markov chain. When the states represented by a `N X 1` matrix:
    - In the probability matrix, it will have one column or row with one element on the diagnal as 1 and all others as 0.
    - For an absorbing Markov chain, the element that has 100% probability in the probability matrix must have connection with all other element.
    - Reorder the elements in the transition matrix to make the `From` columns and `To` rows starts with the absorbing elements. Then this transition matrix is called in stardard form.(column with ones on diagnal starts from the left)
    - In stard form the stable probability matrix for an absorbing Markov chain with one absorbing element has `1`s on the first row and rest element as `0`. The final state is `1` for the absorbing element and `0` for all others.
    - When there are two or more absorbing states,
      - The transition matrix can be divided by for section:
        - Top-left is the identity matrix `I`
        - Top-right is the `S` matrix
        - Bottom-left is the `0` matrix with all elements as `0`
        - Bottom-right is the `R` matrix
      - The stable transition matrix will then be:
        - Top-left is the identity matrix `I`
        - Top-right equals `S` matrix multiply by the inverse of matrix `(I-R)`
        - Bottom-left is the `0` matrix with all elements as `0`
        - Bottom-right is the `0` matrix with all elements as `0`
      - For absorbing Markov chains with two or more absorbing states, different initial state will have different final state.

## Statistics

- Descriptive Statistics – summary and description of collected data
- Inferential Statistics – generalizing from a sample to a population
- A population is a well-defined collection of objects
- When information is available for the entire population we have a census
- A subset of the population is a sample
- Univariate data consists of observations on a single variable
  - Multivariate – more than two variables

### Random Variable

- It is a variable that represents the outcomes of a event. It is the independent variable of the probability function.
- Random variable can have three types:
  - discrete variable: integer value, single event.
  - discrete infinite variable: multiple event.
  - continuous(nondiscrete) variable: events happens overtime.
- A Monte Carlo simulation is a model used to predict the probability of different outcomes when the intervention of random variables is present
  - It can be a program that brutal force all the random outcomes, it iterates many times until there is a consistent outcome
  - The more random our system, the larger the universe, the more iterations are needed to test the system
  - It is good at solving complex problems due to the intervention of random variables

### Features

- mean(average), $$\overline{x}=\frac{ \sum_{i=1}^n x_i}{n}$$.
- median, the middle reading. for even number of data, get the average of the two data in the middle.
- mode, the value occurs the most.
  - The mode is the value that occurs the most often. If there are two different numbers that occur the most​ often, then the set is bimodal, or has M shape. Three or more different items sharing the highest frequency of occurrence rarely offer useful information. Such a distribution has no mode. If each number occurs exactly​ once, then there is no mode.
  - Unimodal - having one mode
  - bimodal - having two mode
- Spread (Variability, Dispersion) represents a numerical summary of how tightly the values are clustered around the ”center“
- Range, you subtract the maximum value and minimum value
  - midrange
    - midrange = range/2
    - Measures of dispersion characterize how concentrated or spread out items in a data set are with respect to a central point
- Quartiles, if n is the number of value
  - Q1 (the First Quartile 25 percentile)
    - it is the middle value of the first half of the data when sorted ascending order.
  - Q2 is the median
  - Q3 (the Third Quartile, 75 percentile)
    - It is the middle value of the second half of the data when sorted ascending order.
  - if Q position in the middle of two numbers calculate the average
- Five number sumamry - Min, Q1, Q2, Q3, Max
- Percentile
  - percentile divide the data into 100 set
  - multiply this decimal from the percentage of the percentile by the number of items in the list.​ Finally, identify the next item in the list. This number is the nth percentile.
- After the n observations in a data set are ordered from smallest to largest, the lower (upper) fourth is the median of the smallest (largest) half of the data, where the median is included in both halves if n is odd
  - A measure of the spread that is resistant to outliers is the fourth spread
  - fourth spread = upper fourth – lower fourth
  - Also known as IQR
- IQR – Interquartile Range is the difference between the third and the first quartile. It represents the most "important" 50% of the data.
  - The interquartile range measures dispersion because it indicates the size of the span in which half of the data is located
- Quartile Devication: The half of the interquartile range
- Outliers are extreme values that don't appear to belong with the rest of the data plotted as a separate dot in box plot.
  - To detect mild outliers you find the 1.5 IQR value and go lower than Q1 and higher than Q3. Or more specifically, the outliers are values of the data (if they exist) that are less than Q1 - 1.5 IQR, and more than Q3 + 1.5 IQR.
  - outlier is extreme if it is more than 3 IQR rather than 1.5 IQR
- expected value
  - expected value(centre value typical value)(weighted value of the random variable)
  - expected value is the sum of the product of each random variable and its corresponding probability.
  - insurance company is aimed to make the expected value 0 for their policies.
  - when the distribution is symmetrical the mean = expected value
  - Rules of the Expected Value - `E(aX +b)=a*E(X)+b`
- Variance
  - for equally likely values $$\frac{ \sum_{i=1}^n (x_i-\overline{x})^2}{n}$$
    - Use `n-1` in the denominator for sample standard deviation denoted as `sx`.
  - for values with probability distribution $$\sum_{i=1}^n P(E_i)(x_i-E(x))^2$$ where `P(Ei)` is the probability of `i`, and `E(x)` is the expected value.
  - When all data is increased by a constant, the SD is unchanged
  - When all data is multiplied by a constant, the SD is multiplied by the square of the constant
- standard deviation(σ)(represent the range of x-axis)
  - $$\sigma= \sqrt{variance}$$
  - When all data is increased by a constant, the SD is unchanged
  - When all data is multiplied by a constant, the SD is multiplied by the constant

### Data Representation

- Categorical data categorize data into categories and the number of data in each category can be represented by a frequency table, frequency chart, bar chart, and pie chart using number of occurrence or percentage(probability) value to represent the value.
- Histogram uses adjacent bars. It is used to show the distribution of values
- Pie chart has its central angle = 360 X percentage
- A stem-and-leaf plot shows quantitative data values in a way that sketches the distribution of the data.
  - first column represent the tens place as stem, leaves are the digits.
  - "back-to-back" (double)stem - The stem can be in the middle with two leaves on the sides.
  - stem and leave can also divide numbers into smaller categories.
- A dotplot graphs a dot for each case against a single axis
- Probability Distribution
  - It is a chart represent chances of different random variable.
    - x-axis is the variable(nondiscrete is usually like time)
    - y-axis can be the number of occurrence for the variable
    - y-axis can be the probability of the variable(normalized)
    - for normalized distribution chart the sum of all y-value is always 1.
    - The curve on chart is a representation of the probability function.
  - continuous distribution can be solved by either calculus or round values into groups and use histogram.
  - non-symmetrical graph is called a skewed diagram.(people choose to stand after a long line)
    - The distribution is left-skewed if the tail is longer from the left side
    - It is called right-skewed if it is longer from the right side.
    - The Skewness Coefficient can be found by the formula:
      - `3(mean-median)/standard dev`
      - For left skewed data the skewness coefficient is negative, and for right-skewed data it is positive
- Box Plots
  - Box plots are particularly effective for comparing groups.
  - When comparing distribution of several groups, consider the shape, centre, and spread
  - A graph that displays measures of central tendency and dispersion of the data with outliers
  - When comparing groups with box plots:
    - Compare the medians, to see which group has a higher centre
      - The group that generally did better on the test is the one with the higher median value. Note that if the median values are the​ same, you can also compare the upper quartiles and lower quartiles
    - Compare the IQRs; check which group is more spread out
    - Check for possible outliers. Identify them.
  - report the median and IQR when the distribution is skewed. If it is symmetric we summarize the mean and standard deviation
- Grouped Data - Grouped data is a convenient summary of raw data; however, some of the original information contained in the data is lost, thus, resulting to approximate measures of central tendency and dispersion if the original data is not made available
  - Approximate value of the sample mean from grouped data - sum of the product of group midpoint and its group size divided by the group size total
  - Approximate value of variance from grouped data - sum of the product of group midpoint square and its group size minus total group size times mean square, then divided the difference by the group size total
    - use group size total minus 1 for sample data
  - Formula for the grouped median - Median = L + (j/f)C
    - L - lower boundary of the class containing the median
    - j - frequency required to reach the median
    - f - frequency of the class containing the median
    - C - Class width

### Types of Probability Distribution

- The probability distribution or probability density function has random variable on x-axis and probability on y-axis
- The area of the graph is 1
- The graph of f is the density curve
- f (x) > 0 for all values of x
- Cumulative Distribution Function (`F(x)`) - it measures the total possibility for any random variables that is smaller than `x`
  - `F(x)` is the area under the density curve to the left of x
  - the derivative of cmulative distribution function is its corresponding probability density function
- The median of a continuous distribution x is where `F(x) = 0.5`
- The expected value of f(x) equals $$\mu = E(x) = \int^{\infty}_{-\infty} x \cdot f(x) dx$$
- Variable of f(x) is $$\int^{\infty}_{-\infty} (x- \mu)^2 \cdot f(x) dx$$
  - or $$E(x^2)-[E(x)]^2$$

#### Uniform Distribution

- A continuous random variable X is said to have a uniform distribution on the interval `[A, B]` if the `f(x) = 1/(B-A)`
- The density curve is a horizontal line

#### Normal Distribution

- the normal distribution function is written as: $$f(x)=\frac{1}{\sigma \sqrt{2 \pi}} e^{\frac{-(x- \mu)^2}{2 \sigma^2}}$$
  - $$y_{max}=\frac{1}{\sigma \sqrt{2 \pi}}$$
  - `μ` is the x value of the highest point, when `μ = 0`, the graph is symetrix on y-axis.
  - `σ` determine the height of the graph. Smaller `σ` value will result in a taller graph.
- Characteristics
  - symmetric about the mean
  - mean, median, mode are equal to `μ`.
  - total area under the curve is equal to one
  - curve approaches but never touches x-axis
- standard normal distribution
  - Between `u-a` and `u+a` graph curves downward. other `x` value graph curves upward. `u-a` and `u+a` is the inflection point.
  - standard normal distribution is a normal distribution with mean = 0 and a = 1
- To transform values into standard normal distribution (z-score):
  - z also mean the number of times of the standard deviation value below or above the mean.
  - `z-value = (value-mean)/standard deviation`
  - z-score is the corresponding x-axiz value of a standard normal distribution
  - it can be calculated and used to find the performance of one data in among the sample. in the graph. the higher the better.
- z-score is used to find the cumulative area of the graph in the standard normal table(Z-score table). first column is the - base value first row is the hundredth place. Use the closest value to solve problems.
  - when `z = -3.49` area is close to 0 when z=3.49 area is close to 1
  - when `z = 0` area is 0.50
- `α` denoted the area to the right of z-score $$z_{\alpha}$$
- according to the Empirical Rule:
  - `±1σ = 68%`
  - `±2σ = 95%`
  - `±3σ = 99.7%`
- If the binomial probability histogram is not too skewed, X may be approximated by a normal distribution with $$\mu = np$$ and $$\sigma = \sqrt{npq}$$
  - To approximate: `z-value = (value + 0.5 - mean)/standard deviation`

#### Binomial Distribution

- It is the distribution of the results of a binomial experiment.
  - n trials
  - 2 outcomes
  - independent
  - probability unchanged
- p is the probability of success
- q is the probability of failure
- p + q = 1
- the possible outcomes of i success in n trials satisfy Pascal's triangle nth i column. the sum of nth column is 2^n(the all possible outcomes)
- It represents the probability of m successes in n trials, given the probability of success of each trial p
- In the Binomial Distribution, for each possible `m` it has a `Pm` value on y-axis as $$P_m = C^m_n p^m (1-p)^{n-m}$$ or $$P_m = \frac{n!}{m!(n-m)!} p^m q^{n-m}$$
- `expected value = np` = `number of trials X probability of success`
- `variance = npq`
- standard deviation = sigma = sqrt(variance)
- for normal(gaussian) and binomial distribution
  - expected value in the middle, then
  - according to the Empirical Rule:
    - `±1σ = 68%`
    - `±2σ = 95%`
    - `±3σ = 99.7%`
- For Binomial Experiment, the condition for sampling is without replacement (resulting in changing p after each sample) is the sample size n is at most 5% of the population size

#### Poisson Distribution

- It measures the possibility of a certain number of pulses or events `x` during a time interval, given the expected number `μ` of pulses (events) during any such time interval
  - When `ɑ` is the expected rate for the events to occur, `μ = ɑ*t` where `t` is the length of the time interval
- For expected value `μ > 0`: $$p(x;\mu)=\frac{e^{- \mu} \cdot \mu ^{x}}{x!}$$ for `x = 1, 2, 3,...`
  - `e` is the base of the natural logarithm
- The area of this distribution equals one is the consequence of the Maclaurin series expansion of `e^μ`
- It can be used to simplify Binomial Distribution when n is at least `50` and np is smaller than `5`
  - The `μ` will then be `np`
  - mean and variance of a binomial variable should approach those of a Poisson variable
- Three Assumptions of Poisson Process
  - There exists a parameter `ɑ > 0` such that for any short time interval of length `Δt`, the probability that exactly one event is received is `ɑ*Δt+o(Δt)`
  - The probability of more than one event during `Δt` is `o(Δt)`
  - The number of events during the time interval `Δt` is independent of the number that occurred prior to this time interval

#### Central Limit Theorem

- For x number of samples taken from a population for n data during one sampling.
  - the mean of one sample is x bar.
  - the size of the samples is n,
  - the sd of the sample is s
  - sigama σ is the sd of the population
- Sampling Distribution - It is the distribution of means for each sample.
- For large n and x from any distribution of a population:
- the sampling distribution is approximately Normal.
- the mean sampling distribution is approaching the mean of the population.
- 3z is used to estimated sd. in a normal curve.
- The sd of the sampling distribution is equals sd(population)/sqrt(n)
- Condition:
  - the samples are all independent and random.
  - when the sample content are all unique. n<10% of population(x>10)
  - to be accurate considering n>25 or 30 or more.

#### Confidence Intervals for Means

- It is a range of value of the sampling distribution. It uses percentage like 95% to indicate the change of a sample has a mean that falls within the range.
- For small n we have:
  - t-distribution is a normal distribution that depends on sample size
  - It has thicker tails when sample size is low.
  - It uses degrees of freedom to indicate sample size.
    - `Degrees of freedom(df) = sample size - 1`
    - For a greater df, the t-value get closer to z-value.
  - on a t-table find the Degrees of freedom first then find the closest t-value according the confident interval required.
  - `t-value = (sample mean - population mean)/Standard Error`
  - estimated sd of the sampling distribution is called standard error.
    - `SE(estimated sample sd) = s(sample sd)/sqrt(sample size)`
    - this time we use sample sd to make estimation, so it is called standard error
  - `confidence intervals = mean ± t-value * standard error` (similar to z-score calculation)
    - it represents the confidence of the true mean of the population would be in the interval.
    - `t-value * standard error` is also called the margin of error.
- for infinite population at least 10 target sample in a sample set is preferred.
- The assumptions needed in order to use the​ Student's t-models are shown below.
  - The data are independent.
  - The data arise from a random sample or suitably randomized experiment.
  - The sample size is no more than​ 10% of the population.
  - The data are from a population that is nearly normal.
  - For small samples​ (less than​ 15), the data must closely follow a normal model.
  - For sample sizes between 15 and 40 or​ so, the data must be unimodal and reasonably symmetric.
  - When the sample size is larger than 40 or​ 50, the t methods are safe to use unless the data are extremely skewed.
- To find the sample size needed for certain margin of error, according to the ME formula we need s (sd of the sample) and t-value, in this case, t-value can be replaced by z-value(0.475 or 0.025 for 95%) and s can be any sample’s sd.
