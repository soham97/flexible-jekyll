---
published: true
layout: post
title: Predictive Threat Intelligence
date: 2019-01-01 00:00:00 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: threat/nodes.png # Add image post (optional)
tags: [predictive threat intelligence, machine learning, overview, research paper] # add tag
---


Predictive Threat Intelligence is one of the emerging focus of information security. In short, Predictive Threat Intelligence is based on understanding attacker behaviour and attack pattern to better predict his/her future actions. The foresight of attackers next actions, intentions and targets can help industries and organizations to take better precautionary decisions beforehand. Moreover, the foresight can expose major vulnerabilities or leaks in the existing system. This will help the industries and organizations fix unauthorized access points in their system before they can be used for intrusion. 

This being an active research area, researchers are working on different ways to accurately model the temporal actions of attacker. The model developed has to be sophisticated to understand complex pattern and at the same time generalizable to new unseen attack patterns. This can mainly lead to researchers taking two approaches:
1. Anomaly detection: This is the most common approach used, where an attack sequence or pattern is considered deviation from normal and the problem is framed as detection this deviation
2. Statistical Modelling: This is a promising approach to model attacker behaviour and then using the trained model to predict attacker state. The research community has not be able to fully extract the benefit of this approach due to hurdles like lack of real attack data, lack of benchmarks for evaluating results, and difficulty in modelling complex discrete patterns.

My work guided by Dr. Faruk Kazi lies uses the second approach to model attacker pattern. My work is divided into two parts which have following implications:
1. To collect real attack patterns, we setup Cowrie Honeypot at COE-CNDS lab. The honeypot attacks as traps and collects logs of real attackers attacking the system. This has led to collection of data rich in feature set which can be used in modelling and benefit research community.
2. We have developed a semi-supervised Hidden Markov Model and a generative Long Short Term Memory Approach (LSTM) for modelling this data which can accurately predict the attacker’s future action 8 out of 10 times (80% accuracy). The approach and preliminary results are documented in paper titled 'Temporal and Stochastic Modelling of Attacker Behaviour' which is published in Springer CCIS (volume no. 941) - [paper link](https://link.springer.com/chapter/10.1007/978-981-13-3582-2_3)

The end to end developed system which works on live data was presented to [Cyber Peace Foundation](https://www.cyberpeace.org/) and Economist from British Embassy. The work was also presented to IPS officer with prospects on implementing it on existing government infrastructure. The model are deployed on [DNIF](https://dnif.it/), an industry standard analytics platform.

Some photos:
<p align="center">
<img src="{{site.baseurl}}/assets/img/threat/DNIF.jpeg" alt="working with DNIF engineers"/>
</p>
<br>

<b> Soon to be updated with more photos and ongoing research work. <b>