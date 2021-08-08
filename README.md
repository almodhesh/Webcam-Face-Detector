# Webcam-Face-Detector

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
