---
published: true
layout: post
title: Google's Toxic Comment Classification Challenge (Kaggle)
date: 2018-08-06 00:00:00 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: toxic/tcc.png # Add image post (optional)
tags: [kaggle, competition, nlp, gold] # add tag
---

Internet has enabled people to communicate and learn from each other. Learning from others and at the same time expressing ones feeling and opinions to others requires a consoling and comforting environment. Online hate, abuse, toxicity shuns people from opening up and taking full advantage of the opportunities that online communication provides. The Conversation AI team, a research initiative founded by Jigsaw and Google (both a part of Alphabet) are working on tools to help improve online conversation. So far they’ve built a range of publicly available models served through the Perspective API, including toxicity. But the current models still make a lot of errors and doesn't distinguish between different toxicity. 

In kaggle competition, the conversation AI challenges data scientist to build a multi-headed model that’s capable of detecting different types of of toxicity like threats, obscenity, insults, and identity-based hate better than Perspective’s current models. The dataset includes comments from Wikipedia’s talk page edits. The comments are labelled in following 6 categories: <br>
- toxic
- severe_toxic
- obscene
- threat
- insult
- identity_hate

The official site of competition containing competition details: https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge

I have included some visualisation below, for you get the distribution and target proportion of data. Some example of comments or samples of data have <u>NOT</u> been included due to their profanity.

![1]({{site.baseurl}}/assets/img/toxic/pertarget.png){:height="300px" width="450px"}
![2]({{site.baseurl}}/assets/img/toxic/tagspertarget.png){:height="300px" width="450px"}

The solution or pipeline developed consisted of 3 parts:
1. Preprocessing and dataset preparation
2. Architecture
3. Ensembling- stacking

<b>Part 1</b>: Preprocessing consisted of completely cleaning the data of some random characters, removing stopwords, converting to lower case to name a few. Stemming and lemmatization were also used to generate different sets of data to be passed to model.

<b>Part 2</b>: As most of model complexity resided in embedding layer, various pretrained embeddings were used namely:
- GloVe
- fastText
- word2Vec
- Byte-Pair Encoded subword embedding (BPE)

The architures developed and employed after this embedding are:
- Bidirectional LSTM
- Bidirectional GRU
- Bidirectional LSTM with Attention
- Deep pyramid CNN
- DeepMoji Architecture (Recurrent base)
- Modified DeepMoji with CNN base
- Text CNN (1D and 2D)
- Stacked CNN and Bidirectional GRU
- Stacked double Bidirectional GRU
- Capsule Networks for text
- Logreg and NB-SVM
- LightGBM

One major score boost and edge we obtained from competitors was by incorporating end part of long sentences. Many normal sentences contained toxic remarks in the end part, changing the tone of the sentence. Hence two embedding layers were fed into the model consisting of initial 200 sequence length and 200 sequence length from the end.

Capsule Network which employed RNN as its base was developed by us to capture contextual information and twisting language use. This network modelling beats all the other models in benchmark scores. The details of this network will be released soon, in a paper <u>(accepted in conference- IEEE procedings, yet to be published)</u>

<b>Part 3</b>: 
- First Layer: A bit preamble about stacking methodolgy used, the training data was divided into 10 fold. The network was trained on 8 folds, validated on 1 fold and made predictions on the 1 fold. This process was continued until we had prediction on all train folds. Using this out of fold strategy, we generated leakage free predictions on train data itself. This predictions on train data from different models were concatenated column-wise, and formed the intermediate train data.

- Second Layer:Then on the intermediate train data, models like LightGBM, Xgboost, Logistic regression were trained and then used to make prediction on test data.

- Third Layer:Then all the test predictions of second layer models were averaged using geometric mean.

### <b>Results</b>: 
We ranked 15th out of 4551 teams and achieved a Gold medal with final AUC ROC score of 0.9874 on test set. The competition ran for 4 months. During that time I learnt a lot of machine learning techniques, various new tricks, and got to interact with great Data Scientist. It was great experience for me !

<b>Github repo<b>: https://github.com/soham97/Toxic-Comment-Classification-Challenge-NLP