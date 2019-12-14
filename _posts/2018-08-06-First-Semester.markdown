---
published: true
layout: post
title: My first semester at CMU
date: 2019-12-14 00:00:00 +0300
description: concepts that I learn't in the first semester at CMU
img: sem/CMU.png # Add image post (optional)
tags: [CMU, semester, learnings, lessons, concepts] # add tag
---
Its December 12th Thursday here, the semester at CMU has come to an end. My last exam finished on Tuesday 10th December which was for Introduction to Machine Learning (18-661). My other two subjects MLSP (18797) and Cloud & ML infrastructure (18847F) had poster session and exam on Monday the same day. The MLSP poster session got extended a bit and unfortunately was late to 18847F exam (quiz) due to that by 20 mins. I still managed to get above median score on the quiz despite the time loss but it's mistake on my behalf that I didn't inform the professor about so close timings and lesson learnt. Overall, the semester provided me a great foundational background in machine learning, signal processing and got up to speed with latest research topics in machine learning infrastructure.

The 18661 course taught by Professor Yeuji Chi and Carlee Joe-Wong provided me a lot of fundamentals required for understanding advanced topics of machine learning and something that one can build on over time. I enjoyed how some of the traditional algorithms like linear regression, ridge regression had rich probabilistic interpretation behind them. Then we learn't how we are doing empirical risk minimisation and how it can be broken down into bias, variance and noise and the tradeoff's between them. Then we went to naive bayes, logistic regression (binary and multi-class). The way we learnt is we came up with an intuition of what we should be modelling then formally framed the intuition and did maximum likelihood estimation for parameter estimation. Then after that we went into SVMs, in which the dual formulation of SVM by setting up the Lagrangian and kernel trick later used are pretty neat. Then the class explored k-NN, decision trees and some popular ensemble methods like bagging, random forest, boosting etc with some nice proofs of Adaboost formulation. The class then went into neural networks. We started with perceptron and then later went to neural nets their forward propagation, backward prorogation coupled with SGD and other methods like dropout and regularisations, followed by Convolutional networks (CNNs) and brief touch on the Recurrent Neural Nets (RNNs). Then the class ventured into unsupervised machine learning, particularly K-means, K-means ++, and then GMM and the EM method. The GMM was used to motivate the incomplete likelihood problem followed by the Expectation Maximisation (EM) methodology. I got to admit it was first difficult to wrap my head around the EM method's intuition and math but as I did more problems like missing data, classic runs of head-tails the whole procedure got clearer along with the usage of Jensen's equality and how the bound is formed. Though EM is a good hammer, it does not necessarily give global optimum but can get stuck in local minima or saddle point, but I guess that's the case for every iteration optimisation algorithms which try to approximate the solution. The next couple of lectures where on dimensionality reduction and we touched on topics like online learning, multi armed bandits and basic introduction to reinforcement learning like state value function, action value function and Q learning. Overall, it was a fun course and provided me a good mathematical background and insight to some of the core machine learning algorithms and techniques.  

MLSP course (18797) was particularly interesting, first of all it was a PhD level course, second of all the material that was covered in here assumed a lot of background in machine learning and signal processing, so I was a bit doubtful on my preparedness to take the course and benefit from it. However, after talking to professor Bhiksha about the requisite and benefits of the course, I decided to go for it. In the hindsight, I am glad I took the course. The course started with some overview of where signal processing and machine learning intersect and where signal processing methods can be used to aid machine learning. The courses started with foundational linear algebra methods like vector spaces, projections, EVD, SVD followed with basics of convex optimisation and deterministic representations like wavelets, fourier etc. Then the class explored data driven representations like Eigen representations, Karhunen-Loeve transform, PCA, ICA, NMF, overcomplete representations, sparsity based representations, bag of words, K-means, kernel k-means, dictionary based representations and their application to de-noising. Then the class switched gears to classifiers and we studied Adaboost specifically with respect to face detection, followed by linear classifiers, perceptron, SVM, naive bayes and max entropy modelling. In the domain of prediction/modelling the class covered Nearest neighbour, Linear regression, Kernel regression, Regularisation along with sparsity. In modelling, we studied statistical modelling of signals, ML estimation, Expectation Maximisation, Gaussian mixture models, MAP estimation, linear gaussian models, HMM and the three problems. In supervised representations, the class covered CCA and LDA.  The last lecture was about Linear dynamical models, Kalman filter and extended Kalman filter. Overall the class covered a lot of material from the perspective of signals and provided me with a new way of thinking about things. However, I think the course could have been more organised with more fluent transition between topics and well defined motivation.

18847F was a special topics course in computer system: Foundations of Cloud and Machine learning infrastructure taught by professor Gauri Joshi. The objective of this course is to introduce students to modern cloud and machine learning infrastructure, and its theoretical foundations. The first half of the course covered distributed computing and storage systems, frameworks such as MapReduce and Spark, and discuss scheduling and load balancing policies used in them. In the context of distributed storage systems, the course discusses coding-theoretic techniques used to improve availability and repair failed nodes. This section covered papers such as 'Sparrow', 'Attack of clones', 'Rateless coding', 'Gradient coding' etc. The second half of the course focused on machine learning infrastructure in stochastic gradient descent and its implementation in large-scale systems coupled with adaptive communication strategies.  Some of the papers covered where: 'DistBielef', 'HolgWild!', 'Slow and stale gradients', PipeDream', 'Cooperative SGD', Adacomm', 'Federated learning' etc. The third section was a bit exotic and covered wide range of sysML topics ranging from model compression to hyperparamter tuning to multi-armed bandits, Gaussian processes and bayesian optimisation. This covered paper such as 'TernGrad', 'ATOMO', PowerSGD', 'HyperBand', 'Neural Architecture Search', 'Parallel Bayesian optimisation' etc and guest lectures on Multi-armed bandits and Gaussian processes. Overall the course provided me a system's perspective of Machine Learning and equipped me with problem solutions when the ML systems are scaled. 

In the next semester, I intend to take courses which build on what I have learned in first semester. Currently, I am enrolled for 11785 (Introduction to Deep Learning), 11747 (Neural Networks for NLP) and 18-898D (Graph signal processing and learning). Hope to see you then!

Attaching some photos below:

<b> First snow at CMU: </b>
<p align="center">
<img src="{{site.baseurl}}/assets/img/sem/cmu_winter.png" alt="First snow at CMU"
width="100%"/>
</p>
<br>

<b> Working on some problem: </b>
<p align="center">
<img src="{{site.baseurl}}/assets/img/sem/board.png" alt="First snow at CMU"
width="100%"/>
</p>
<br>

<b> My oncampus job lending desk photo: </b>
<p align="center">
<img src="{{site.baseurl}}/assets/img/sem/oncampus.png" alt="First snow at CMU"
width="100%"/>
</p>
<br>

<b> Random: </b>
<p align="center">
<img src="{{site.baseurl}}/assets/img/sem/random.png" alt="First snow at CMU"
width="100%"/>
</p>
<br>