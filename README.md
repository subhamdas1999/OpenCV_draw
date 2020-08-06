# OpenCV_draw

import numpy as np

import cv2


### variables  ( 2 varibale need to setup )######

drawing = False #('True' when mouse button down, 'False' when mouse button UP )

ix=-1
xy=-1

### function  ######

def draw_rectangle(event,x,y,flags,param):
    global ix,iy,drawing
    
    if event == cv2.EVENT_LBUTTONDOWN:   # means if we have pressed the left mouse button
        drawing =a True
        ix,iy=x,y
        
    elif event == cv2.EVENT_MOUSEMOVE:
        if drawing == True:
            cv2.rectangle(img,(ix,iy),(x,y), (0,255,255), -1)
            
            
    elif event == cv2.EVENT_LBUTTONUP: # means if we have released the left mouse button
        drawing =False
        cv2.rectangle(img,(ix,iy),(x,y), (0,255,255), -1)


### showing the image  ######



### black  ######


img= np.zeros((512,512,3))

cv2.namedWindow(winname='drag_&_draw rectangle')
cv2.setMouseCallback('drag_&_draw rectangle',draw_rectangle)  #write function name after writing window name


while True:
    cv2.imshow('drag_&_draw rectangle',img)
    
    #checks for esc key
    if cv2.waitKey(1) & 0xFF == 27:  #it wait 20 minisecon
        break
cv2.destroyAllWindows()



