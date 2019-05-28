---
published: true
layout: post
title: Predictive Threat Intelligence (Final Year B.Tech Project)
date: 2019-05-01 00:00:00 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: threat/nodes.png # Add image post (optional)
tags: [predictive threat intelligence, machine learning, overview, research paper] # add tag
---

Big data analytics solutions, backed by machine learning and artificial intelligence, can help tackle the problems of cybersecurity breach and hacking. By employing the power of big data and machine learning, we can significantly improve cyber threat detection mechanisms. Predictive Threat Intelligence is one of the emerging focus of information security. In short, Predictive Threat Intelligence is based on understanding attacker behaviour and attack pattern to better predict his/her future actions. The foresight of attackers next actions, intentions and targets can help industries and organizations to take better precautionary decisions beforehand. Moreover, the foresight can expose major vulnerabilities or leaks in the existing system. This will help the industries and organizations fix unauthorized access points in their system before they can be used for intrusion. 

This being an active research area, researchers are working on different ways to accurately model the temporal actions of attacker. The model developed has to be sophisticated to understand complex pattern and at the same time generalizable to new unseen attack patterns. This can mainly lead to researchers taking two approaches:
1. Anomaly detection: This is the most common approach used, where an attack sequence or pattern is considered deviation from normal and the problem is framed as detection this deviation
2. Statistical Modelling: This is a promising approach to model attacker behaviour and then using the trained model to predict attacker state. The research community has not be able to fully extract the benefit of this approach due to hurdles like lack of real attack data, lack of benchmarks for evaluating results, and difficulty in modelling complex discrete patterns.

## Phase 1:
My work guided by Dr. Faruk Kazi lies uses the second approach to model attacker pattern. My work is divided into two parts which have following implications:
1. To collect real attack patterns, we setup Cowrie Honeypot at COE-CNDS lab. The honeypot attacks as traps and collects logs of real attackers attacking the system. This has led to collection of data rich in feature set which can be used in modelling and benefit research community.
2. We have developed a semi-supervised Hidden Markov Model, Markov Chain and a generative Long Short Term Memory Approach (LSTM) for modelling this data which can accurately predict the attacker’s future action 8 out of 10 times (80% accuracy). The approach and preliminary results are documented in paper titled 'Temporal and Stochastic Modelling of Attacker Behaviour' which is published in Springer CCIS (volume no. 941) - [paper link](https://link.springer.com/chapter/10.1007/978-981-13-3582-2_3)

The end to end developed system which works on live data was presented to [Cyber Peace Foundation](https://www.cyberpeace.org/) and Economist from British Embassy. The work was also presented to IPS officer with prospects on implementing it on existing government infrastructure. The models are deployed on [DNIF](https://dnif.it/), an industry standard analytics platform.

Some photos:

Cyber Peace Foundation and Economist from British Embassy with COE-CNDS Threat Intelligence team
<p align="center">
<img src="{{site.baseurl}}/assets/img/threat/team.jpg" alt="Cyber Peace Foundation and Economist from British Embassy"/>
</p>
<br>

IPS officer Pratik Thube addressing the COE-CNDS Threat Intelligence team
<p align="center">
<img src="{{site.baseurl}}/assets/img/threat/ips3.jpeg" alt="IPS officer Pratik Thube"/>
</p>
<br>

Explaining IPS officer Pratik Thube how the developed algorithm can be used to track and predict malicious attacks in real time
<p align="center">
<img src="{{site.baseurl}}/assets/img/threat/ips_explain.jpeg" alt="Explaining work to IPS officer Pratik Thube"/>
</p>
<br>

## Phase 2:
In second phase, we incorporate these machine learning algorithms into a big data system utilizing Kafka streaming. The system can store large amounts of data and help analysts examine, observe, and detect irregularities within a network. The predictive models help predict and gear up for possible consequences caused by attacker and can issue an alert as soon as it sees an entry point for a cybersecurity attack.

In particular, we frame the projects contributions in big data architecture in the following three threads: 
- Designing and prototyping a multi-tiered big data architecture, which aims at automating the generation of cyber threat artifacts that could effectively be employed for adaptive cyber threat intelligence using abundant machine learning techniques.
- Exploiting several big data paradigms, tools and technology, which enables the integration of heterogeneous network traffic to generate consolidated artifacts. Such an architecture seamlessly and effectively integrates the cyber security and data analytics communities, in an effort to further improve the adoption of machine learning in cyber security initiatives.
- Evaluating and validating the proposed architecture under real time network and malware traffic. 

The overall System has following main components:
1. <b>Cowrie Honeypot </b>
 - The user interacts with the honeypots with the aim to explore the system. These actions are logged into the system with these information columns.
 - The data is stored in the MongoDB database at the end of the session. 
2. <b>Kafka </b>
- Producer: Each honeypot device has its own producer module. The producer is responsible for publishing the honeypot log data to the brokers. Each producer node subscribes to a cluster of Kafka brokers which automatically distributes the load among themselves. The producer constantly monitors the log produced by honeypot device, converts it to JSON format acceptable to the streamer and publishes it to an input topic. The JSON file consists of attacker details as well as the input offset of the attacker. Topics are additionally broken down into a number of partitions. The partition in which a data is placed is determined by its key. The data with the same input key will be grouped together in the same partition at the broker end. To maintain the order of the input data, we assign the unique session id of each attacker as the key to the input topic.
- Kafka Streamer: Kafka Streamer is responsible for real-time prediction of the future attack sequence. It performs a set of map and reduce operations to aggregate and compute the results. The streamer is subscribed to the input topic which is periodically updated by the kafka producer. Each kafka streamer has its own flask server which is responsible for computing the predicting via various machine learning algorithms. The first map operation maps the input stream of data into a numeric value between 0-18 and stores the result in a custom data structure named as streamList. A groupByKey() operation, then aggregates the mapped values with respect to the session Id. This is followed by a reduce operation which combines the data of each group and produces a final output. This output is in the form of a streamList data structure which consist of a list of sequence generated by each attacker sequence. This reduce operation also ensures the list does not exceed the maximum limit of aggregated data to be preserved. The streamList corresponding to each attacker sequence is stored in a KTable. This is followed by a second map phase to produce a stream of predicted output. At this stage, the streamer sends a POST request to the flask server. The body of this request is in the form of an array of attacker sequence. The server computes the prediction and sends the predicted output back to the streamer. The prediction is stored in JSON format. This map phase produces data in the form of a KStream. This KStream data is flushed back to the kafka broker via an output topic. 
- Kafka Consumer: Each honeypot device has its own consumer module. The consumer module is responsible for publishing the honeypot log data to the MongoDB for the storage. Each consumer node subscribes to a cluster of Kafka brokers which automatically distributes the load among themselves. The consumer constantly monitors the predictions made by Machine learning models, converts it to JSON format acceptable to the MongoDB and publishes it to a corresponding topic. The JSON file consists of predicted states as well as the probability of the attacker sequence.

3. <b>Machine Learning Models </b>
 - The Flask server which is responsible for the prediction and analysis of the sequence runs the machine learning models on input data from the streamer. The streamer sends a sequence of the states ranging from 0-18 each representing action taken by the user. The output of the Machine learning model is the prediction of the next state. The machine learning Model can be either Markov Chain, HMM or the LSTM Model.  
4. <b>MongoDB database </b>
 - The MongoDB database is the storage component of the system. The log files which are created through interaction can be stored and utilised to improve the accuracy of the Machine learning model by retraining the model on generated data. Also the predicted states for each sequence can be used as measure of accuracy for the Models. The mongoDB interacts with Kafka subsystem through the producers and the consumers to send and receive the data in JSON format.

5. <b> The Overall System workflow </b>
	<p align="center">
	<img src="{{site.baseurl}}/assets/img/threat/OSA.png" alt="Overall system workflow"/>
	</p>
	<br>

6. <b> Dashboard and User Interface </b>
	<p align="center">
	<img src="{{site.baseurl}}/assets/img/threat/dashboard.png" alt="Dashboard with basic analysis and prediction of next attacker action"/>
	</p>
	<br>

<b>Github repository containing codes and full report is available [here](https://github.com/soham97/Predictive-Threat-Intelligence)</b>