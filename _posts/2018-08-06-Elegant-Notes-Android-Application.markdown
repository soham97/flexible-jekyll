---
published: true
layout: post
title: Elegant Notes App (Android)
date: 2018-08-06 00:00:00 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: notes/notes1.png # Add image post (optional)
tags: [android, app, notes, software] # add tag
---
## What was the motivation behind it?
In my junior year of engineering I wanted to make a scalable product that people would love to use. I also had a secondary motive of obtaining some side cash from it (This kind of idea had provided me side cash in high school by creating software tutorials on YouTube). Knowing myself, it didn't surprise me when I choose to build a software application, specifically an Android Application. The Aim of the project was three fold:
1. I wanted an application that satisfied my unique specifications in functionality as well as design
2. Visualising is the first step of expressing your ideas. By knowing how to make an android application I would be quickly able to present my ideas in comprehendible manner to a general public
3. Around that time I had deviated from C++ to Java and wanted something concrete (even if it is basic) to get deeper into Java

So little did I know that this skill was also going to help me in first internship.

## The app and what’s so special about it?

The application that I created was a Notes app. Its cardinal function was simply scribbling down notes. Its other features included:
1. Notes were sortable and viewable according to oldest, recent and favourites.
2. Provided extra accident delete protection by providing bin where deleted notes go and can be restored. 
3. Added search functionality for easy search of notes by title
4. Backed up by google drive where you can upload the notes database and later restore when needed
5. The colour of each note can be chosen, to indicate the urgency or theme of the task
6. In each note one can add images or take photos, record, and save audio clip and other utilitarian extras
7. Ability to share each note on variety of platforms which includes WhatsApp, Mail, messages etc
8. Had different grid layouts to view the notes in a bird’s view form or a detailed form

<b>The main deal:</b>The main features that I personally wanted in my notes app was feature number 4. A notepad for me is a place to scribble personal notes and epiphanies as well as an organized way for getting things done and increase productivity. This required me to have seperate work notebook (containing projects and internship notes), a college notebook (containing university pertaning notes), and a personal notebook, all of which should be universally accessed by single account and easy switching between them should be possible.

<b>The solution:</b> Google login and Drive API was the backbone of making this possible. The notes app creates multiple sqlite databases depending upon your required divisions, for example: work notebook, personal notebook. These databases are maintained in the users drive storage, by his permission. Then the user can switch between his notebook by simply loading the other databases from his drive. Saving of information, preventing accidental overwritting and other nitty-gritty details are managed by the notes app itself.

The design philosophy that the app followed was Model-View-Controller. It took me solid 3 months to taking it from idea to a fully functional developable application.

## The developing and learning experience:

It provided me experience in designing an application based on Model-View-Controlled pattern. Apart from learning Java intricacies and android development, got deep into the nitty-gritty details of SQLite, drive-API for making the separate databases work seamlessly. Faced numerous problems while optimising the app to display images from each notes, audio saving and contention problems, to restoring to bitmaps. 

Some images of the application:
<br>
![1]({{site.baseurl}}/assets/img/notes/notes1.png){:height="560px" width="300px"}
![1]({{site.baseurl}}/assets/img/notes/notes2.png){:height="560px" width="300px"}
![1]({{site.baseurl}}/assets/img/notes/notes3.png){:height="560px" width="300px"}

<br>
#### Moreover learning to develop functional android apps helped me in numerous hackathons for presenting and visualising the results. I still use my notes app as my daily scribbler, with 700+ notes made and still going strong, it’s going to remain my daily driver for years to come :)
