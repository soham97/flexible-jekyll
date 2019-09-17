---
published: true
layout: post
title: Threat Intelligence using Fusion Hidden Markov Model
date: 2019-07-01 00:00:00 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: threat/plot.png # Add image post (optional)
tags: [predictive threat intelligence, machine learning, overview, research paper] # add tag
---
Extending the topic of my final year project of Predictive Threat Intelligence, particularly in developing novel algorithm for understanding attacker behaviour and attack pattern to better predict attackers future actions. Link to my previous work in the domain <b> [link](https://soham97.github.io/Predictive-Threat-Intelligence/) </b>

In this work, we propose a framework for inspecting and modelling the behavioural aspect of an attacker to obtain better insight predictive power on his future actions. For modelling we propose a novel semi-supervised algorithm called Fusion Hidden Markov Model (FHMM) which is more robust to noise, requires comparatively less training
time, and utilizes the benefits of ensemble learning to better
model temporal relationships in data. We further evaluate the
performances of FHMM and compares it with both traditional
algorithms like Markov Chain, Hidden Markov Model (HMM)
and recently developed Deep Recurrent Neural Network (Deep
RNN) architectures. We conduct the experiments on dataset consisting of real data attacks on a Cowrie honeypot system. FHMM
provides accuracy comparable to deep RNN architectures at
significant lower training time. Given these experimental results,
we recommend using FHMM for modelling discrete temporal
data for significantly faster training and better performance than
existing methods.

If the above seems interesting to you, do check out our full paper for theortical proof of the algorithm and the system developed on top of that: <b> [link](https://arxiv.org/pdf/1905.11824.pdf) </b>