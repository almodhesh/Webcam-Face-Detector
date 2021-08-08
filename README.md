# Webcam-Face-Detector
# Buliding_AI_Project
Buliding AI Project
<!-- This is the markdown template for the final project of the Building AI course, 
created by Reaktor Innovations and University of Helsinki. 
Copy the template, paste it to your GitHub README and edit! -->

# Building AI for FaceDetector

this project to build programe to detec the faces in live webcam by using python

## Summary

this project to build programe to detec the faces in live webcam by using python


## Background

we will use in this project opencv and random library  



## How is it used?

Describe the process of using the solution. In what kind situations is the solution needed (environment, time, etc.)? Who are the users, what kinds of needs should be taken into account?

Images will make your README look nice!
Once you upload an image to your repository, you can link link to it like this (replace the URL with file path, if you've uploaded an image to Github.)
![Cat](https://upload.wikimedia.org/wikipedia/commons/d/db/Nor%27easter_1967-03-22_weather_map.jpg)




# first install python cv 
 #pip install opencv-python (windows) 
# pip install python-opencv (linux)

import cv2
from random import randrange

# load some pre-trained data on face frontals from opencv (haar cascade algorithm ) 
trained_face_data = cv2.CascadeClassifier('haarcascade_frontalface_default.xml')

# choose an image to detect faces in 
#img = cv2.imread('RDJ.png')
#img = cv2.imread('RDJ1.png')

# To capture video from webcam.
webcam = cv2.VideoCapture(0)

# Iterate forever over frames
while True:
    # Read the current frame
    successful_frame_read, frame = webcam.read()
    
    #Must convert to the grayscale
    grayscale_img = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
    
    #Detect Faces
    face_coordinates = trained_face_data.detectMultiScale(grayscale_img)
    
      
    # Draw rectangles around the faces
    for (x, y, w, h) in face_coordinates:
        cv2.rectangle(frame,(x,y), (x+w, y+h),(randrange(256),randrange(256),randrange(256)),2)
    
    cv2.imshow('Clever Programmer Face Detector', frame)
    key = cv2.waitKey(1)
    
    ## Stop if Q key is pressed
    if key==81 or key==113:
        break
### Release the VideoCapture Object
webcam.release()

## Data sources and AI methods
Where does your data come from? Do you collect it yourself or do you use data collected by someone else?
If you need to use links, here's an example:
[Twitter API](https://developer.twitter.com/en/docs)

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |

## Challenges

What does your project _not_ solve? Which limitations and ethical considerations should be taken into account when deploying a solution like this?

## What next?

How could your project grow and become something even more? What kind of skills, what kind of assistance would you  need to move on? 


## Acknowledgments

* list here the sources of inspiration 
* do not use code, images, data etc. from others without permission
* when you have permission to use other people's materials, always mention the original creator and the open source / Creative Commons licence they've used
  <br>For example: [Sleeping Cat on Her Back by Umberto Salvagnin](https://commons.wikimedia.org/wiki/File:Sleeping_cat_on_her_back.jpg#filelinks) / [CC BY 2.0](https://creativecommons.org/licenses/by/2.0)
* etc

-----------------------------
