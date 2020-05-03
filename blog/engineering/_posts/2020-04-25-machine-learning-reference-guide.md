---
layout: post
title:  "Machine Learning - Reference Guide"
date:   2020-04-25 00:00:00 +0000   
categories: engineering highlight
tags: engineering
teaser: Machine Learning reference guide - supervised learning, deep learning, unsupervised learning
img-url: /assets/blog/engineering/ml.jpg
permalink: /blog/machine-learning-reference-guide
math: true
---
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Data Processing](#data-processing)
  - [Log-transform the skewed features](#log-transform-the-skewed-features)
  - [One-hot Encoding](#one-hot-encoding)
  - [Manual Encoding](#manual-encoding)
  - [Scikit - Feature Scaling](#scikit---feature-scaling)
  - [Split Data - Training and Testing](#split-data---training-and-testing)
- [Supervised Learning](#supervised-learning)
  - [References](#references)
  - [K-Nearest-Neighbours (K-NN)](#k-nearest-neighbours-k-nn)
    - [Classification And/Or Regression?](#classification-andor-regression)
    - [Properties and Assumptions](#properties-and-assumptions)
    - [Real-World Applications](#real-world-applications)
    - [Strengths](#strengths)
    - [Weaknesses](#weaknesses)
    - [References](#references-1)
  - [Perceptron](#perceptron)
    - [Classification And/Or Regression?](#classification-andor-regression-1)
    - [Properties and Assumptions](#properties-and-assumptions-1)
    - [References](#references-2)
  - [Naive Bayes](#naive-bayes)
    - [Classification And/Or Regression?](#classification-andor-regression-2)
    - [Real-World Applications](#real-world-applications-1)
    - [Strengths](#strengths-1)
    - [Weaknesses](#weaknesses-1)
    - [Gaussian Naive Bayes](#gaussian-naive-bayes)
  - [Decision Trees](#decision-trees)
    - [Classification And/Or Regression?](#classification-andor-regression-3)
    - [Strengths](#strengths-2)
    - [Weaknesses](#weaknesses-2)
    - [References](#references-3)
- [Misc Definitions](#misc-definitions)
    - [Parametric and Non-Parametric Models](#parametric-and-non-parametric-models)
- [Misc Math](#misc-math)
  - [Lines](#lines)
  - [Vectors](#vectors)
  - [Probability](#probability)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Data Processing

## Log-transform the skewed features
A dataset may sometimes contain at least one feature whose values tend to lie near a single number, but will also have a
non-trivial number of vastly larger or smaller values than that single number. Algorithms can be sensitive to such 
distributions of values and can underperform if the range is not properly normalized.    
Using a logarithmic transformation significantly reduces the range of values caused by outliers.
```python
skewed = ['<feature_column_name_1>', '<feature_column_name_2>']
features_log_transformed = pd.DataFrame(data = features_raw)
# log(x + 1) to avoid log(0) which is undefined
features_log_transformed[skewed] = features_raw[skewed].apply(lambda x: np.log(x + 1))
```

## One-hot Encoding
Typically, learning algorithms expect input to be numeric, which requires that non-numeric features [called categorical
variables] be converted. One popular way to convert categorical variables is by using the one-hot encoding scheme. 
One-hot encoding creates a "dummy" variable for each possible category of each non-numeric feature. For example, 
assume someFeature has three possible entries: A, B, or C. We then encode this feature into someFeature_A, someFeature_B
and someFeature_C.
```python
features_final = pd.get_dummies(features_original)
```

## Manual Encoding
If a column/feature has only two possible categories, we can avoid using one-hot encoding and simply encode these two
categories as 0 and 1, respectively.
```python
income = income_raw.replace(['<=50K', '>50K'], [0, 1])
```

## Scikit - Feature Scaling
Normalisation/Scaling ensures that each feature is treated equally when applying supervised learners.
```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler() # default=(0, 1)
numerical = ['age', 'education-num', 'capital-gain', 'capital-loss', 'hours-per-week']

features_log_minmax_transform = pd.DataFrame(data = features_log_transformed)
features_log_minmax_transform[numerical] = scaler.fit_transform(features_log_transformed[numerical])
```

## Split Data - Training and Testing
```python
from sklearn.model_selection import train_test_split

# Split the 'features' and 'income' data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X_raw, 
                                                    y_raw, 
                                                    test_size = 0.2, 
                                                    random_state = 0)
```

# Supervised Learning

[Supervised Learning - Notes](/assets/blog/engineering/ML-Supervised-Learning-Notes.pdf)

## References
* [Introduction to Machine Learning Nanodegree, Udacity](https://www.udacity.com/course/intro-to-machine-learning-nanodegree--nd229)
* [Machine Learning for Intelligent Systems, Prof Kilian Weinberger, Cornell University](https://www.cs.cornell.edu/courses/cs4780/2018fa/page18/index.html)

## K-Nearest-Neighbours (K-NN)

### Classification And/Or Regression?
Used for both classification and regression problems

### Properties and Assumptions
* As n [size of training data set] -> ∞, the 1-NN classifier is only a factor of 2 worse than the best possible 
classifier.
* Assumes that similar points share similar labels.
* "Lazy" learners, i.e there is no learning or training step. Instead there is a computation step [computing the nearest
neighbours] to make every prediction.
* Neighbors-based methods are known as _instance based_ or _non-generalizing_ machine learning methods, since they 
simply “remember” all of its training data [possibly transformed into a fast indexing structure such as a Ball Tree or 
KD Tree].
* The optimal choice of the value k is highly data-dependent: in general a larger k suppresses the effects of noise, but 
makes the classification boundaries less distinct.

### Real-World Applications
* [Recommendation systems](https://en.wikipedia.org/wiki/Recommender_system#Collaborative_filtering)

### Strengths
* Simple to understand and implement.
* k-NN is a simple and effective classifier if distances reliably reflect a semantically meaningful notion of the 
dissimilarity of data points.
* As $$ n\to\infty $$, k-NN becomes provably very accurate, but also very slow.<sup>1</sup>
* It is often successful in classification situations where the decision boundary is very irregular.

### Weaknesses
* As $$ d >> 0 $$, i.e. dimensionality of the data becomes high, points drawn from a probability distribution stop being 
similar to each other, and the k-NN assumption breaks down.<sup>1</sup>
* Can become prohibitively slow to make predictions on new data when the training data set is very large.<sup>1</sup>

### References
1. [http://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote02_kNN.html](http://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote02_kNN.html)
2. [https://scikit-learn.org/stable/modules/neighbors.html](https://scikit-learn.org/stable/modules/neighbors.html)

## Perceptron
Perceptron algorithm is historically important: it was one of the first machine learning algorithms ever derived and was
even implemented in analog hardware

### Classification And/Or Regression?
Classification

### Properties and Assumptions
* A single perceptron can only be used to implement linearly separable functions.<sup>1</sup>
* If a data set is linearly separable, the Perceptron will find a separating hyperplane in a finite number of updates. 
[If the data is not linearly separable, it will loop forever.]<sup>1</sup>
* Perceptrons work well with high dimensional data. 
* Doesn't require a learning rate.
* It updates the model only on mistakes.

### References
1. [https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote03.html](https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote03.html)
2. [https://towardsdatascience.com/perceptron-learning-algorithm-d5db0deab975](https://towardsdatascience.com/perceptron-learning-algorithm-d5db0deab975)
3. [https://scikit-learn.org/stable/modules/linear_model.html#perceptron](https://scikit-learn.org/stable/modules/linear_model.html#perceptron)

## Naive Bayes
Different flavours of NB exist and are used depending the properties of the features, x.
* Categorical NB: When features take a categorical value. Ex: Patient Gender feature used to predict probability of a 
certain disease.
* Multinomial NB: When features values represent counts and not categorical values: Ex: Number of occurrences of a word
in an email that needs to be classified as spam or ham. 
* Gaussian NB: When features take on real values and follow a gaussian distribution. 

### Classification And/Or Regression?
Classification 

### Real-World Applications
* Document classification [multinomial NB]
* Spam filtering [multinomial NB]

### Properties and Assumptions
* A generative learning algorithm.<sup>2</sup>
* When X is a vector of discrete-valued attributes, Naive Bayes learning algorithms can be viewed as linear classifiers;
that is, every such Naive Bayes classifier corresponds to a hyperplane decision surface in X. The same statement holds
for Gaussian Naive Bayes classifiers if the variance of each feature is assumed to be independent of the class.<sup>3</sup> 

### Strengths
* They require a small amount of training data to estimate the necessary parameters.<sup>1</sup>
* Naive Bayes learners and classifiers can be extremely fast compared to more sophisticated methods.<sup>1</sup>
The decoupling of the class conditional feature distributions means that each distribution can be independently 
estimated as a one dimensional distribution. This in turn helps to alleviate problems stemming from the curse of 
dimensionality.<sup>1</sup>

### Weaknesses
* [Gaussian NB] Doesn't work well with outliers. There can be cases where a linear decision boundary for classification
exists, but GNB fails to make correct prediction for outliers. On the other hand, in such a scenarios, a simple 
Perceptron works and makes correct prediction. However, NB is much faster compared to perceptron as the perceptron can 
be slow to converge.<sup>4</sup>
* Although naive Bayes is known as a decent classifier, it is known to be a bad estimator.<sup>1</sup>

### References
1. [https://scikit-learn.org/stable/modules/naive_bayes.html](https://scikit-learn.org/stable/modules/naive_bayes.html)
2. [https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote05.html](https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote05.html)
3. [https://www.cs.cmu.edu/~tom/mlbook/NBayesLogReg.pdf](https://www.cs.cmu.edu/~tom/mlbook/NBayesLogReg.pdf)
4. [Machine Learning Lecture 10 "Naive Bayes continued" -Cornell CS4780 SP17](https://youtu.be/rqB0XWoMreU?t=2722)

## Decision Trees

### Classification And/Or Regression?
Used for both classification and regression problems 

### Strengths
* Simple to understand and to interpret. People are able to understand decision tree models after a brief explanation. 
Trees can be visualised in a way that is easy for non-experts to interpret.
* Mirrors human decision making more closely than other approaches. This could be useful when modeling human 
decisions/behavior.
* Requires little data preparation. Other techniques often require data normalisation, dummy variables need to be 
created and blank values to be removed.
* The cost of using the tree [i.e., predicting data] is logarithmic in the number of data points used to train the tree.
* Performs well with large datasets. Large amounts of data can be analyzed using standard computing resources in 
reasonable time.
* Able to handle both numerical and categorical data.
* Able to handle multi-output problems.
* Uses a white box model. If a given situation is observable in a model, the explanation for the condition is easily 
explained by boolean logic. By contrast, in a black box model [e.g., in an artificial neural network], results may be 
more difficult to interpret.
* Possible to validate a model using statistical tests. That makes it possible to account for the reliability of the 
model.
* Non-statistical approach that makes no assumptions of the training data or prediction residuals; e.g., no 
distributional, independence, or constant variance assumptions
* In built feature selection. Additional irrelevant feature will be less used so that they can be removed on subsequent 
runs.
* Decision trees can approximate any Boolean function eq. XOR.

### Weaknesses
* Trees can be very non-robust. A small change in the training data can result in a large change in the tree and 
consequently the final predictions. This problem is mitigated by using decision trees within an ensemble.
* The problem of learning an optimal decision tree is known to be NP-complete under several aspects of optimality and 
even for simple concepts. Consequently, practical decision-tree learning algorithms are based on heuristics such as the 
greedy algorithm where locally optimal decisions are made at each node. Such algorithms cannot guarantee to return the 
globally optimal decision tree. 
* Over-fitting or high variance: decision-tree learners can create over-complex trees that do not generalize well from 
the training data. Mechanisms such as pruning are necessary to avoid this problem [with the exception of some algorithms 
such as the Conditional Inference approach, that does not require pruning]. Other methods to avoid this problem include
setting the minimum number of samples required at a leaf node or setting the maximum depth of the tree.
* For data including categorical variables with different numbers of levels, information gain in decision trees is 
biased in favor of attributes with more levels. However, the issue of biased predictor selection is avoided by the 
Conditional Inference approach, a two-stage approach, or adaptive leave-one-out feature selection.
* Decision tree learners create biased trees if some classes dominate. It is therefore recommended to balance the 
dataset prior to fitting with the decision tree.
* Trees generally do not have the same level of predictive accuracy as some of the other regression and classification 
approaches and are typically used in an ensemble.

### References
* https://scikit-learn.org/stable/modules/tree.html
* https://en.wikipedia.org/wiki/Decision_tree_learning
* An Introduction to Statistical Learning, Gareth James et all

# Misc Definitions

## Parametric and Non-Parametric Models
Models that have a fixed number of parameters are called Parametric models, while models in which number of parameters 
grow with the amount of training data are called Non-Parametric models. Parametric models have the advantage of often 
being faster to use, but the disadvantage of making stronger assumptions about the nature of the data distributions. 
Non-parametric models are more flexible, but often computationally intractable for large datasets.    

Example: K-NN is non-parametric classifier. Linear and Logistic regression are examples of parametric models.    

Ref:    
  * Sec 1.4.1 Machine Learning A Probabilistic Perspective, Kevin P. Murphy

## Generative and Discriminative Learning
Generative classifiers learn a model of joint probability $$ p(x, y) $$, of the inputs x and the label y, and make their 
prediction using Bayes Theorem to calculate $$ P(y|x) $$ and picking the most likely label y. Discriminative classifiers
model the posterior $$ P(y|x) $$ directly, or learn a direct map from inputs x to class labels.    
* When we estimate $$ P(X,Y) = P(X \mid Y) P(Y) $$ , then we call it generative learning.
* When we only estimate $$ P(Y|X) $$ directly, then we call it discriminative learning.    
Ref:
  * [https://ai.stanford.edu/~ang/papers/nips01-discriminativegenerative.pdf](https://ai.stanford.edu/~ang/papers/nips01-discriminativegenerative.pdf)
  * [https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote04.html](https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote04.html)

## Maximum Likelihood Estimation, MLE and Maximum a Posteriori Probability Estimation, MAP
In supervised Machine learning you are provided with training data D. You use this data to train a model, represented by
its parameters θ. With this model you want to make predictions on a test point $$x_t$$.
* MLE Prediction: $$ P(y|x_t;\theta) $$ Learning: $$ \theta=\operatorname*{argmax}_\theta P_\theta(D) $$. Here θ is 
purely a model parameter. [Frequentist Statistics Approach]
* MAP Prediction: $$ P(y|x_t,\theta) $$ Learning: $$ \theta=\operatorname*{argmax}_\theta P(\theta|D)\propto P(D \mid \theta) P(\theta) $$.
Here θ is a random variable. [Bayesian Statistics Approach]    
Ref:
  * [https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote04.html](https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote04.html)
  * [https://www.youtube.com/watch?time_continue=1277&v=pDHEX2usCS0](https://www.youtube.com/watch?time_continue=1277&v=pDHEX2usCS0)

## Accuracy, Precision and Recall
* Accuracy measures how often the classifier makes the correct prediction. It’s the ratio of the number of correct 
predictions to the total number of predictions (the number of test data points).
$$ Accuracy = \dfrac{True Positive + True Negative}{Total Predictions} $$

* Precision tells us what proportion of messages we classified as spam, actually were spam. It is a ratio of true 
positives [words classified as spam, and which are actually spam] to all positives [all words classified as spam, 
irrespective of whether that was the correct classification].    
**High precision = Ok if not all spam is found. But if marked as spam, better be spam.**    
$$ Precision = \dfrac{True Positive}{True Positive + False Positive} $$

* Recall tells us what proportion of messages that actually were spam were classified by us as spam. It is a ratio of
true positives [words classified as spam, and which are actually spam] to all the words that were actually spam.    
**High Recall = Ok if not all are sick, but find all sick people**    
$$ Recall = \dfrac{True Positive}{True Positive + False Negative} $$

# Misc Math

## Lines
* Slope intercept form          
$$ 
    y = mx + k
$$

* General form    
$$
    ax + by = c
$$    
where,    
$$
    m = \dfrac{-a}{b}, k = \dfrac{c}{b}
$$

## Vectors
* Norm of a vector    
$$
    W = \begin{bmatrix}    
        w_1 \\
        w_2 \\ 
        w_3 \\
        \end{bmatrix}    
$$        
then 
$$
    ||W|| = \sqrt{W^T W} = \sqrt{w_1^2 + w_2^2 + w_3^2}
$$
* Cauchy Schwartz inequality    
$$
    | u . v | \leq ||u|| \times ||v|| 
$$

## Probability
* Binomial Probability Distribution    
$$
    P(k \: out \: of \: n) = {n \choose k} \times p^k {(1-p)}^{n-k}
$$    
where,     
p = probability of positive event, of which we are looking for k occurrences
* Bayes Theorem    
$$
    P(A|B) = \dfrac{P(A)P(B|A)}{P(B)} = \dfrac{P(A)P(B|A)}{\sum_{i=1}^{n}P(a_i)P(B|a_i)} 
$$
* Multiplication rule    
$$
    P(A ∩ B) = P(B|A)P(A) = P(A|B)P(B)
$$    
Ref: 
  * [https://faculty.arts.ubc.ca/hkasahara/Econ325/notes_probability.pdf](https://faculty.arts.ubc.ca/hkasahara/Econ325/notes_probability.pdf)
  * [https://www.youtube.com/watch?v=RIawrYLVdIw&list=PLl8OlHZGYOQ7bkVbuRthEsaLr7bONzbXS&index=7](https://www.youtube.com/watch?v=RIawrYLVdIw&list=PLl8OlHZGYOQ7bkVbuRthEsaLr7bONzbXS&index=7)