---
published: true
layout: post
title: Acoustic Localization and Classification of Sound Sources for Autonomous Vehicles
date: 2019-12-10 00:00:00 +0300
description: My MLSP course team project
img: mlsp/poster.pptx.png # Add image post (optional)
tags: [CMU, MLSP, project, course project, ML, SP] # add tag
---
18797 (Machine Learning & Signal Processing) is a PhD level course and has a semester long project. The requirement of the project is that it should build upon the signal processing and machine learning techniques with strict impositions that 'no neural networks allowed'. Though that seemed annoying at first, as it was clear that we couldn't achieve SOTA without Neural network. But in hindsight, that really helped us by forcing all teams to come up with interpretable novel methods that have both theory and intuition to support them rather than simply throwing more data.

<b> Theme </b>:
The audio-based perception system of an autonomous vehicle (AV) is as important as the vision-based perception for discerning its environment. This allows an AV to classify the type of audio signal and locate the sound source by auditory input alone. With these capabilities, it can complement existing vision-based perception and pave the way for multi-modal operation where differing sensors such as LIDAR/RADAR work together alongside sound to paint a fuller image of the surroundings. 

This problem is an important want to tackle - we want that autonomous vehicles be resilient and able to handle a dynamic environment. Just as human drivers use both sight and sound to gauge the surroundings, we intend the same for AVs. For instance, an AV that relies on LIDAR to detect a nearby vehicle can inform itself to make a better decision if it could hear a siren; that way, it would know that the vehicle is special (be it a fire truck, police car or ambulance) and would aim to give way. Audio detection can help detect the presence of nearby trains far more reliably than LIDAR or rail crossing signs that may or may not exist. These are just some real-world examples where having audio as a new sense can bolster the reliability and performance of AVs.

Our project seeks to take steps toward tackling this impetus, applying machine learning techniques to help classify the sounds of objects in the vicinity of a car, as well as localize them.

The novel contributions of the project are:
1. Designing an end to end source separation, localisation and classification system using Approx Multi-channel NMF for source seperation, TDOA for source localisation and extracting 34 features for each sound frame coupled with ML classifiers to classify sounds into appropriate classes.
2. Developing an Multichannel NMF approximation which has substantially lower training time than traditional Multichannel NMF yet captures the trends in H matrix correctly (the report provides the comparison between them using norm as metric).

<b> Project report (click on image to view the full report): </b>
<a href="{{site.baseurl}}/assets/img/mlsp/Project_report.pdf" class="image fit"><img src="{{site.baseurl}}/assets/img/mlsp/report.png" alt=""></a>

<b> Poster: </b>
<p align="center">
<img src="{{site.baseurl}}/assets/img/mlsp/poster.pptx.png" alt="Poster"
width="100%"/>
</p>
<br>

<b> My team and I: </b>
<p align="center">
<img src="{{site.baseurl}}/assets/img/mlsp/poster_group.png" alt="My team and I"
width="100%"/>
</p>
<br>