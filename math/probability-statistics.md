# Probability & Statistics

## Counting

- Systematic listing - Methods used for count objects
  - One-Part Tasks: use lists
  - Two-Part Tasks: use tables
  - Multiple-Part Tasks: use trees
- FUNDAMENTAL COUNTING PRINCIPLE
  - Under uniformity(independent and equally possibility) criterion: the way c it can be done is equals to products of the ways in different steps.
- Factorial
  - `n!=n×(n− 1)×(n− 2)×...×2×1`
  - By definition: `0!=1`
- Arrangements(order matters) of `n` Distinct Objects
  - It equals to `n!`
  - if same objects are found in the group(Ex, same color same letter same age in an arrangement), its arrangement can be calculated by dividing `n!` by the factorial of the size of special group.
- Permutations(order matters) is the ways of making arrangements of small group r from a big group n
  And order matters
  - It equals to `nPr = n!/(n-r)!`
  - `n` minus `r` excluded objects form a same group for all arrangements.
- Combination is like permutations but order doesn't matter
  - It euqals to `nCr=n!/r!(n-r)!`
  - Extra `r!` in the formula is used to make orders not matter.
- Strategies
  - Draw graph and make analogy to solve different senareio in questions.
  - Methods using steps of combanation&Pemutation is more reliable.
  - The idea of dividing into event and analysis the independence is crutial.

## Probability

- Probability is the prediction of a certain outcome when something occurs
- All the possible outcomes(an elements or member, same points) of experiments make the sample space(a set, denoted by omega Ω). `S= {a,b,c,d,….}`.
- Favourable outcomes or successes make an event that is the subset of the sample space.
- Venn diagram is used to describe sets relationship: intersection, union, compliment, adjoint, subset and difference(minus sign). total box is the sample space omega.
- `n(set)` is the cardinal number of set(the number of its element)
- `A'` is the complement of set A
- A and B means A intersect with B, `A ∩ B`
- A or B means A union B, `A ∪ B`
- Laws
  - demorgan's laws - `(A ∪ C)' = A' ∩ C'` `(A ∩ C)' = A' ∪ C'`
  - events for not A - `n(U) = n(A) + n(A')` if U contains all events
  - events for A or B - `n( A ∪ B ) = n( A ) + n( B ) − n( A ∩ B )`
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
  - Subjective probability - Based on experience or intuition. (guess)
  - Empirically (experimentally) - Based on historical and geological records.(gather data)
  - Theoretically (mathematically) - Based on predictable parameters. (coin has two sides)
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
- Conditional probability
  - A probability that takes into account a given condition is called a conditional probability.
  - It is denoted as P(B|A) and pronounce it "the probability of B given A."
  - To find the probability of the event B given the event A(after event A occur), we restrict our attention to the outcomes in A. We then find in what fraction of those outcomes B also occurred.
  - `P(B|A) = P(A and B) / P(A)`
  - `P(A)` cannot equal 0, since A has occurred for sure.
  - A and B is A and B happens not equivalent to `P(A)*P(B)`, because A and B is not two steps.
  - For condition possibility, events are not independent , hence they use the previous multiplication rule now has a general version: For any two events A and B, `P(A and B) = P(A) x P(B|A)` or `P(A and B) = P(B) x P(A|B)`
- Baye’s theorem
  - Theorem 1 - if A must result in one of the mutually exclusive events A1,A2,A3…An then, `P(A1nA2nA3) = P(A1)P(A2|A1)P(A3|A1nA2)`
  - Theorem 2 - `P(A) = P(A1)P(A|A1)+P(A2)P(A|A2)+….+P(An)P(A|An)`
  - From 1 and 2 baye’s theorem can be derived. If A must result in one of the mutually exclusive events A1,A2,A3,Ai,...,An `P(Ai|A) = P(Ai)P(A|Ai)/n sigama i=1 P(Ai)P(A|A1)`
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
  - Two parameters define the Binomial model: n, the number of trials; and, p, the probability of success. We denote this Binom(n, p).
  - In n trials, there are nCk ways to have k successes. (`nCk = n! / k!(n - k)!`)
  - Hence, for a Binomial distribution model the probability of successes equals `nCk * p^x * q^n-x`. where
    - `p` = probability of success
    - `q` = `1 – p` = probability of failure
    - `X` = number of successes in n trials
    - if x can have more values, the probabilities for different x values can be added together

## Statistics

### Random Variable:

- It is a variable that represents the outcomes of a event. It is the independent variable of the probability function.
- Random variable can have three types:
  - Discrete variable: integer value, single event.
  - discrete infinite variable: multiple event.
  - continuous(nondiscrete) variable: events happens overtime.

### Data Representation

- Categorical data categorize data into categories and the number of data in each category can be represented by a frequency table, frequency chart, bar chart, and pie chart using number of occurrence or percentage(probability) value to represent the value.
  - Histogram uses adjacent bars. It is used to show the distribution of values.
  - Pie chart has its central angle = 360 X percentage
  - A stem-and-leaf plot shows quantitative data values in a way that sketches the distribution of the data.
    - first column represent the tens place as stem, leaves are the digits.
    - "back-to-back" (double)stem - The stem can be in the middle with two leaves on the sides.
    - stem and leave can also divide numbers into smaller categories.
  - A dot plot graphs a dot for each case against a single axis.

### Probability Distribution

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
    - 3(mean-median)/standard dev. For left skewed data the SC is negative, and for right-skewed data is positive.
- mean(average), `x(with - hat)= sum(all x)/ n`
- median, the middle reading. for even number of data, get the average of the two data in the middle.
- mode , the value occurs the most.
  - The mode is the value that occurs the most often. If there are two different numbers that occur the most​ often, then the set is bimodal. or has M shape Three or more different items sharing the highest frequency of occurrence rarely offer useful information. Such a distribution has no mode. If each number occurs exactly​ once, then there is no mode.
  - Unimodal – having one mode
  - bimodal- having two mode
- Spread (Variability, Dispersion) represents a numerical summary of how tightly the values are clustered around the “center”.
- Range, you subtract the maximum value and minimum value
  - midrange
    - midrange = range/2
    - Measures of dispersion characterize how concentrated or spread out items in a data set are with respect to a central point.
- Quartiles, if n is the number of value
  - Q1 (the First Quartile 25 percentile)
    - it is the middle value of the first half of the data when sorted ascending order.
    - it is the value in the (n+1)/4 th position. (round up)
    - If n is even: the Q1 is a value between two middle numbers A and B that are in both in the position. In this case Q1 = A + 0.25 (B - A)
    - If n is odd, there are no problems. even number is the average of adjacent two value.
  - Q2 is the median
  - Q3 (the Third Quartile, 75 percentile)
    - It is the middle value of the second half of the data when sorted ascending order.
    - It is the value in the 3(n+1)/4 th position.(round down)
    - If n is even, the Q3 is a value between two middle numbers C and D that are in both in the position. In this case Q3 = C + 0.75 (D - C)
    - If n is odd, there are no problems. even number is the average of adjacent two value.
- Percentile
  - percentile divide the data into 100 set
  - multiply this decimal from the percentage of the percentile by the number of items in the list.​ Finally, identify the next item in the list. This number is the nth percentile.
- IQR – Interquartile Range is the difference between the third and the first quartile. It represents the most "important" 50% of the data.
  - The interquartile range measures dispersion because it indicates the size of the span in which half of the data is located.
- Outliers are extreme values that don’t appear to belong with the rest of the data plotted as a separate dot in box plot.
  - To detect potential outliers you find the 1.5 IQR value and go lower than Q1 and higher than Q3. Or more specifically, the outliers are values of the data (if they exist) that are less than Q1 - 1.5 IQR, and more than Q3 + 1.5 IQR.
- if Q position in the middle of two numbers calculate the average.
- Box Plots
  - Box plots are particularly effective for comparing groups.
  - When comparing distribution of several groups, consider the shape, centre, and spread.
  - When comparing groups with box plots:
    - Compare the medians, to see which group has a higher centre
      - The group that generally did better on the test is the one with the higher median value. Note that if the median values are the​ same, you can also compare the upper quartiles and lower quartiles
    - Compare the IQRs; check which group is more spread out
    - Check for possible outliers. Identify them.
  - report the median and IQR when the distribution is skewed. If it is symmetric we summarize the mean and standard deviation.
- expected value
  - expected value(centre value typical value)(weighted value of the random variable)
  - expected value is the sum of the product of each random variable and its corresponding probability.
  - insurance company is aimed to make the expected value 0 for their policies.
  - when the distribution is symmetrical the mean = expected value.
- for equally likely values
  - variance ó^2x = sum((x-average(x))^2)/n
  - its root is the population standard deviation
- for values with probability distribution
  - `variance = sum(Probability(x)*(x- expected value)^2)`
- standard deviation(sigma)(represent the range of x-axis)
  - sigma = sqrt(variance)
  - variance ó^2x = óx(sd)^2
  - n-1 is used for sample standard deviation denoted as sx

#### normal distribution

- the normal distribution function is written as: `f(x) = 1/(sigma*sqrt(2*PI))*e^(-(x-u)^2/(2*sigma^2)`, `ymax = 1/(sigma*sqrt(2*PI))`, `xmiddle = u`
- symmetric about the mean
- mean median mode are equal
- total area under the curve is equal to one
- curve approaches but never touches x-axis
- Between u-a and u+a graph curves downward. other x value graph curves upward. u-a and u+a is the inflection point.
- standard normal distribution is a normal distribution with mean = 0 and a = 1
- To transform values into standard normal distribution (z-score):
- z also mean the number of times of the sd below or above the mean.
- z value = (value-mean)/standard deviation
- z-score is the x-axiz value of a standard normal distribution
- it can be calculated and used to find the performance of one data in among the sample. in the graph. the higher the better.
- z-score is used to find the cumulative area of the graph in the standard normal table. first column is the - base value first row is the hundredth place. Use the closest value to solve problems.
  - when z= -3.49 area is close to 0 when z=3.49 area is close to 1
  - when z=0 area is 0.50

#### binomial distribution

- It is the distribution of the results of a binomial experiment.
  - 1 n trials
  - 2 2 outcomes
  - 3 independent
  - 4 probability unchanged
  - p is the probability of success
  - q is the probability of failure
  - p + q = 1
- the possible outcomes of i success in n trials satisfy pasca triangle nth i column. the sum of nth column is 2^n(the all possible outcomes)
- The probability of m successes in n trials.
- `Pm = nCm*p^m*(1-p)^n-m`
- expected value:
  - u = `n*p` = number of trials `*` probability of success
- `variance = n*p*q`
- standard deviation = sigma = sqrt(variance)
- for normal(gaussian) and binomial distribution
  - expected value in the middle, then
  - according to the Empirical Rule:
    - +- 1 sigma = 68%
    - +- 2 sigma = 95%
    - +- 3 sigma = 99.7%

#### Central Limit Theorem

- For x number of samples taken from a population for n data in one sample.
- the mean of one sample is x bar.
- the size of the samples is n,
- the sd of the sample is s
- sigama ó is the sd of the population
- Sampling Distribution It is the distribution of means for each sample.
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
  - Degrees of freedom(df) = sample size - 1
  - For a greater df, the t-value get closer to z-value.
  - on a t-table find the df first then find the closest t-value according the confident interval required.
  - t-value = (sample mean - population mean)/Standard Error
  - estimated sd of the sampling distribution is called standard error.
  - SE(estimated sample sd) = s(sample sd)/sqrt(sample size)
    - this time we use sample sd to make estimation, so it is called standard error
  - confidence intervals = mean +- t value `*` standard error (similar to z-score calculation)
  - it represents the confidence of the true mean of the population would be in the interval.
  - t value `*` standard error is also called the margin of error.
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
