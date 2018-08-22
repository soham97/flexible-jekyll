---
published: true
layout: post
title: Siemens MakeITReal Hackathon
date: 2018-08-06 00:00:00 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: siemens/siemens.jpg # Add image post (optional)
tags: [hackathon, software, machinelearning, Siemens] # add tag
---
## Hackathon details
Siemens MakeItReal hackathon conducted by Hackerearth was an amazing experience for me. The hackathon challenged participants to develop a prototype under themes of mobility, healthcare, building technologies, digital factories, energy management. It consisted of two phases online and then an offline prototype building round at Bangalore. You can check it out further at [competition](https://www.hackerearth.com/sprints/makeitreal/).

## Idea inspiration
Being a Siemens intern who had just dipped his feet in machine learning, I could first-hand experience the problem of machine downtime and what it was costing Siemens. With appropriate sensor network, calculating the breakdown time of machine seemed plausible to me (didn't know at that time it was called RUL). The ROI on the idea was also large, and would help every manufacturing plant.

How will it directly affect the industry?<br>
• Downtime of machine reduced
<br>
• Maintenance cost and extra labour costs which would be otherwise required eliminated
<br>
• Precious time of supervisors and officers saved, which can be utilized in other creative purposes beneficial to the company
<br>
• The above points contribute in increasing the efficiency and throughput of factory

## Let's get technical
### --System architecture and data flow:
The entire system was mainly constructed in python with additional use of publicly available libraries. The prototype we built consisted of following parts: -

1. Sensor network which measures various parameters at every instance. 
2. Raspberry pi which acted as a data extraction unit took data from sensors and converted it into a feature vector. This reduced and improved feature vector will be uploaded to database. 
3. Fog computing is also included in the system to take critical decision locally without contacting the server 
4. The features from database are used to train LSTM based machine learning model. The final output gives indication of the RUL of the machine. 
5. The final output is then uploaded to database from where it is displayed on website and android application.

### -- Framing the problem statement for model development
1. The problem statement was framed as given the current and previous n steps of k sensor data predict the remaining useful life of the machine. The RUL can directly be predicted by framing it as a regression problem.
2. The second approach was as a classification problem. Given the initial assumption rather than predicting the RUL, classify whether the machine will fail in next n1, n2,...nm hours where m ranges from 2 to 36. Hence this becomes a multi-class problem and not binary.

### -- Dataset and pre-processing
The most important step was the successful prediction of algorithm on large noisy data. Hence we choose to use an external dataset to display the effectiveness of the algorithm even after building the data pipeline. NASA’s popular C-MAPSS turbofan engine dataset which has inherent characteristics like high variance due to sensor noise, effects of operating conditions, and presence of multiple simultaneous fault modes, which generalizes well to other prognostic applications was chosen. The CMPASS consisted of 4 datasets each with increasing noise. The dataset was pre-processed using normalization and using Kalman filter to remove the noise present. The <u>Kalman</u> filter employed on sensors readings had a large positive impact on its predicitve power i.e rmse for regression and accuracy for classification.

### -- Machine learning model
The model consisted of two stacked LSTM layers followed by a neuron for multi-class classification and relu activation layer for regression task. The cell outputs of first LSTM where fed to the second LSTM which feed its output to either to a neuron or relu layer. A dropout of 40% was used to prevent overfitting. RMSprop was used as optimizer and the model was trained with a learning rate of 0.001 and batch size of 200. Given a time frame of 24 hours, Keras was ideal choice to develop the model. 

### -- Model results
Taking sequence length for learning and prediction as 50, we were getting accuracy of range of about 98 to 89 percent for binary classification, 95 to 88 percent for multiclass classification and mean-squared-error range of 245 to 461. (The results were given in range due to the presence of 4 datasets in increasing complexity)

![loss]({{site.baseurl}}/assets/img/siemens/loss.png){:height="200px" width="300px"}
![mse]({{site.baseurl}}/assets/img/siemens/mse.png){:height="200px" width="300px}
![prediction]({{site.baseurl}}/assets/img/siemens/prediction.png){:height="200px" width="300px"}


### -- Visualized
The results were visualised using an android application and a web app. Initially we thought of displaying it on HMI, but as control rooms are not near machines in factory plus the additional benefits of portablitiy of android phone made us develop both of the solutions.

![Web application]({{site.baseurl}}/assets/img/siemens/web.jpg){:height="400px" width="700px"}
![Android application]({{site.baseurl}}/assets/img/siemens/android.png){:height="400px" width="200px}
<br>
Though this could have been a better dashboard, given the limited time this is what we could come up with.
<br>

## Hackathon results
![presenting the idea]({{site.baseurl}}/assets/img/siemens/present.jpg)
<br>
The idea was shortlisted in online round. In offline round (Bangalore) after evaluation by judges, our team was further shortlisted in top 5 teams. The top 5 teams had the honour to present their idea and solution to the entire audience with a question round in the end. After such scrutinising process, we were awarded <b>4th prize</b> in the competition. Thanks and congrats to my teammates Rahul and Ruturaj (from left to right in above image) without whom this wouldn't have been possible and as much fun.

#### In all it was a great experience, met a lot of talented students, built something functional within deadline, explored Bangalore and had fun.