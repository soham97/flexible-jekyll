---
published: true
layout: post
title: Quora's Insincere Question Classification Challenge (Kaggle)
date: 2019-02-20 00:00:00 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: quora/quora_logo.png # Add image post (optional)
tags: [Kaggle, competition, NLP, silver medal] # add tag
---

An existential problem for any major website today is how to handle toxic and divisive content. Quora wants to tackle this problem head-on to keep their platform a place where users can feel safe sharing their knowledge with the world. On Quora, people can ask questions and connect with others who contribute unique insights and quality answers. A key challenge is to weed out insincere questions -- those founded upon false premises, or that intend to make a statement rather than look for helpful answers. In this Kaggle competition, Quora challenges data scientist to build models to identify and flag insincere questions. This will help quora in developing more scalable machine learning based methods apart from manual review to detect toxic and misleading content. Moreover it will help Quora in upholding their policy of “Be Nice, Be Respectful” and continue to be a place for sharing and growing the world’s knowledge.

An insincere question is defined as a question intended to make a statement rather than look for helpful answers. Some characteristics that can signify that a question is insincere: <br>

- Has a non-neutral tone
	- Has an exaggerated tone to underscore a point about a group of people
	- Is rhetorical and meant to imply a statement about a group of people
- Is disparaging or inflammatory
	- Suggests a discriminatory idea against a protected class of people, or seeks confirmation of a stereotype
	- Makes disparaging attacks/insults against a specific person or group of people
	- Based on an outlandish premise about a group of people
	- Disparages against a characteristic that is not fixable and not measurable
- Isn't grounded in reality
	- Based on false information, or contains absurd assumptions
- Uses sexual content (incest, bestiality, pedophilia) for shock value, and not to seek genuine answers

This was a kernel only competition, therefore the entire solution right from preprocessing to training deep learning models had to be <u> done under 2 hours runtime of kaggle kernel </u>, otherwise the team was disqualified. The official site of competition containing competition details: [https://www.kaggle.com/c/quora-insincere-questions-classification](https://www.kaggle.com/c/quora-insincere-questions-classification)

The competition was challenging in terms of finding correlated local validation, running the solution in 2 hours, and producing reproducible results, to name a few. We found a nearly correlated validation set before 1 week of the competition end. We used simple averaging where each trained NN model (Pytorch) was different either in terms of learning rate, pre-processing, embedding or architecture to maintain model diversity. One important thing we realised was: given small learning rate and large number of epochs, single FastText embedding based models were beating our glove+paragram models. So we focused on tuning FastText based models which could provide considerable score within 5-6 epochs. We also added Gaussian Noise to some models after embeddings to reduce the overdependence of RNN on specific keywords.

**Solution summary:**

 - **Runtime**: 6352.2 secs
 - **Preprocessing**: Cleaning special characters, number pre-processing, misspell cleaning (For some models changed preprocessing sequence to add diversity)
 - **Embedding**: GLoVe, FastText, Paragram embeddings 
 - **Neural Network architecture** (trained for 5-6 epochs with no fold): 
	  - Stacked LSTM-GRU-128 hidden units, with GloVe+Paragram embedding
	  - Stacked LSTM-GRU 60 hidden units with attention and capsule, and GloVe+Paragram embedding
	  - Stacked LSTM-GRU-60 hidden units with GloVe+Paragram embedding
	  - Stacked LSTM-GRU-60 hidden units with FastText embeddings
	  - Stacked LSTM-GRU-80 hidden units with FastText embeddings and different preprocessing sequence 
 - **Blending**: Averaging prediction of each model with linear regression coefficients 

**Things that did not work**

 - We tried pseudo labelling in different ways, but it didn't provide major boost considering its running time for it, so we dropped it in the end.
 - We tried variety of preprocessing techniques to no avail. All of them tend to decrease the LB score with slight improvement in cv. Fearing overfitting pre-processing to training data with kept it to minimum.
 - One trick that we tried was weight saving and retraining. For example, we trained the model and saved its weights before the model reached optimum. Then for the next model we loaded the weights for LSTM and GRU and did not pass gradients through them. This forced the new parts of model like an extra CNN layers or linear units to cover up for this. This saved time as the new model reached optimum within 2 epochs. But this did not add considerable benefit to the ensemble. In my opinion, majority of the information pertaining text was captured by RNN units, leaving little information required to be captured by newly added layers.

This wouldn’t have been possible without awesome teammates, Ashish and Rahul, who put in lot of effort and made this competition a great learning experience.


### <b>Results</b>: 
We ranked 33rd out of 4037 teams and achieved a Silver medal with final F1-score of 0.70658 on test set. I entered about 2 months late in this competition, leaving me only about 1 month for developing the solution. I learnt a lot of coding in pytorch, effect of random initilization, new machine learning learning techniques and got to interact with great Data Scientist. It was great experience for me!

<b>GitHub repo</b>: [https://github.com/soham97/Quora-Insincere-Questions-Classification-Challenge-NLP](https://github.com/soham97/Quora-Insincere-Questions-Classification-Challenge-NLP)
