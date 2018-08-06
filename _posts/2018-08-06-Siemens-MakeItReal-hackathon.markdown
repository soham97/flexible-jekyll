---
published: true
layout: post
title: Siemens MakeITReal Hackathon
date: 2018-08-06 00:00:00 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: software.jpg # Add image post (optional)
tags: [hackathon, software, machinelearning] # add tag
---
## Hackathon details
Siemens MakeItReal hackathon conducted by hackerearth was an amazing experience for me. The hackathon challenged participants to develop a prototype under themes of mobility, healthcare, building technologies, digital factories, energy management. It consisted of two phases online and then an offline prototype building round at Bangalore. You can check it out further at [competition](https://www.hackerearth.com/sprints/makeitreal/).

## Idea inspiration
Being a Siemens intern who had just dipped his feet in machine learning, I could first hand experience the problem of machine downtime and what it was costing Siemens. With appropriate sensor network, calculating the breakdown time of machine seemed plausible to me (didn't know at that time it was called RUL). The ROI on the idea was also large, and would help every manufacturing plant. Having big goals in mind, the only thing left was just making the idea work ;)

How will it directly affect the industry?
-- Downtime of machine reduced.
-- Maintenance cost and extra labour costs which would be otherwise required eliminated.
• Precious time of supervisors and officers saved, which can be utilized in other creative purposes
beneficial to the company.
• The above points contribute in increasing the efficiency and throughput of factory.

## Lets get technical
### --System architecture and data flow:
The entire system was mainly constructed in python with additional use of publicly available libraries. The prototype we built consisted of following parts:-

1. Sensor network which measures various parameters at every instance. 
2. Raspberry pi which acted as a data extraction unit took data from sensors and converted it into a feature vector. This reduced and improved feature vector will be uploaded to database. 
3. Fog computing is also included in the system to take critical decision locally without contacting the server 
4. The features from database are used to train LSTM based machine learning model. The final output gives indication of the RUL of the machine. 
5. The final output is then uploaded to database from where it is displayed on website and android application.

### -- Framing the problem statement for model development
1. The problem statement was framed as given the current and previous n steps of k sensor data predict the remaining useful life of the machine. The rul can directly be predicted by framinig it as a regression problem.
2. The second approach was as a classification problem. Given the initial assumption rather than predicting the RUL, classify whether the machine will fail in next n1,n2,...nm hours where m ranges from 2 to 36. Hence this becomes a multi-class problem and not binary.

### -- Dataset and preprocessing
The most important step was the successful prediction of algorithm on large noisy data. Hence we choose to use an external dataset to display the effectiveness of the algorithm even after building the data pipeline. NASA’s popular C-MAPSS turbofan engine dataset which has inherent characteristics like high variance due to sensor noise, effects of operating conditions, and presence of multiple simultaneous fault modes, which generalizes well to other prognostic applications was chosen. The dataset was preprocessed using normalization and using kalhman filter to remove the noise present. The <u>kalhman</u> filter employed on sensors readings had a large positive impact on its predicitve power i.e rmse for regression and accuracy for classification.

### -- Machine learning model
The model consisted of two stacked LSTM layers followed by a neuron for multi-class classification and relu activation layer for regression task. The cell outputs of first LSTM where fed to the second LSTM which feed its output to either to a neuron or relu layer. A dropout of 40% was used to prevent overfitting. RMSprop was used as optimizer and the model was trained with a learning rate of 0.001 and batch size of 200. Given a time frame of 24 hours, Keras was ideal choice to develop the model. 

### -- Model results


### -- Visualized
The results were visualised using an android application and a web app. Initially we thought of displaying it on HMI, but as control rooms are not near machines in factory plus the additional benefits of portablitiy of android phone made us develop both of the solutions.

<!-- ![I and My friends]({{site.baseurl}}/assets/_images/pm1.png) -->
<p align="center">
<img src="../_images/pm1.png">                                                                    
</p>

## Hackathon results
The idea was shortlisted in online round and in the offline prototyping round (in Bangalore) we were ranked at 4th position out of 25 teams.