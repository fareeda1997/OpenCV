# OpenCV


import cv2
faceCascade = cv2.CascadeClassifier('Cascades/haarcascades/HAARCASCADE_FRONTALFACE_DEFAULT.xml')


eye_cascade = cv2.CascadeClassifier('Cascades/haarcascades/HAARCASCADE_EYE.xml')


cap = cv2.VideoCapture(0)

cap.set(3,640) # set Width

cap.set(4,480) # set Height





while True:

    ret, img = cap.read()
    
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    
    faces = faceCascade.detectMultiScale(
    
        gray,
        
        scaleFactor=1.2,
        
        minNeighbors=5,
        
        minSize=(20, 20)
    )



for (x,y,w,h) in faces:


    cv2.rectangle(img,(x,y),(x+w,y+h),(255,0,0),2)
    
    roi_gray = gray[y:y+h, x:x+w]
    
    roi_color = img[y:y+h, x:x+w]




 for (ex, ey, ew, eh) in eyes:
 
        # draw a green rectangle around the eyes
        
        cv2.rectangle(roi_color, (ex, ey), (ex + ew, ey + eh), (0, 255, 0), 2)
        




k = cv2.waitKey(30) & 0xff

    if k == 27:  
    
        break
        
    # put a text above the top - right corner of the face rectangle
    
    cv2.putText(img, msg, (x + 5, y - 5), cv2.FONT_HERSHEY_PLAIN, 1, (255, 255, 255), 2)
    
    cv2.imshow('Face Detection -FANA', img)
