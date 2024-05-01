# AI-Gym-Project-Dumbbell-Counter-
1. Set up MediaPipe for Python
 2. Estimate poses using your Webcam and OpenCV 
3. Extract join coordinates from the detected pose 
4. Calculate angles between joints using Numpy and Trigonometry 
5. Building an AI Powered Gym Tracker to count your reps
 
How we doing our project:
Step1: Installing mediapipe
Step2: Make detection using the webcam on the machine
Step3: Calculating the joint angles and applying curl logic
 
1 Install and import Dependencies:
The very first step in our project is to install and import dependencies which is the basic requirement for starting our project. 
We have install mediapipe and OpenCV in your python.
This action is achieved by writing the command:-
pip install Mediapipe
pip install OpenCV 
pip install numpy
 
After installing the module we will now import the dependencies by writing these code in the python file i.e
Import cv2
Import mediapipe as mp
Import numpy as np
 
OpenCV-Python is a library of Python bindings designed to solve computer vision problems. 
 
cv2. rectangle() method is used to draw a rectangle on any image. end_point: It is the ending coordinates of rectangle. The coordinates are represented as tuples of two values i.e. (X coordinate value, Y coordinate value). color: It is the color of border line of rectangle to be drawn.
 
Cap.release(): This function is used to release the  real time camera 
Cv2.destroyAllwindows(): It  is used in destroying all the open windows .
Cv2.waitkey(): It allows you to wait for a specific time in milliseconds until you press any button on the keyword.
 
Cv2.putText(): cv2. putText() method is used to draw a text string on any image. ... org: It is the coordinates of the bottom-left corner of the text string in the image. The coordinates are represented as tuples of two values i.e. (X coordinate value, Y coordinate value).
 
Cv2.FONT_HERSHEY_SIMPLEX:
Some of font types are FONT_HERSHEY_SIMPLEX, FONT_HERSHEY_PLAIN, , etc. fontScale: Font scale factor that is multiplied by the font-specific base size. color: It is the color of text string to be drawn. For BGR, we pass a tuple. eg: (255, 0, 0) for blue color.
 
Cv2.imshow():  cv2. imshow() method is used to display an image in a window. The window automatically fits to the image size. ... window_name: A string representing the name of the window in which image to be displayed.
 
Cv2.videocapture(): 
. This will return video from the first webcam on your computer.
 
Numpy:
NumPy is a module for Python. The name is an acronym for "Numeric Python" or "Numerical Python"
Furthermore, NumPy enriches the programming language Python with powerful data structures, implementing multi-dimensional arrays and matrices. These data structures guarantee efficient calculations with matrices and arrays. The implementation is even aiming at huge matrices and arrays, better know under the heading of "big data". Besides that the module supplies a large library of high-level mathematical functions to operate on these matrices and arrays.
 
NumPy is based on two earlier Python modules dealing with arrays. One of these is Numeric. Numeric is like NumPy a Python module for high-performance, numeric computing, but it is obsolete nowadays. Another predecessor of NumPy is Numarray, which is a complete rewrite of Numeric but is deprecated as well. NumPy is a merger of those two, i.e. it is build on the code of Numeric and the features of Numarray.
 
Mediapipe:
MediaPipe is a cross-platform framework for building multimodal applied machine learning pipelines. MediaPipe is a framework for building multimodal (eg. video, audio, any time series data), cross platform (i.e Android, iOS, web, edge devices) applied ML pipelines.
 
1(a) Video feed capture
After this we will write a feed which will capture a real-time video feed from our web-camera. Once we get our feed then we apply our pose estimation, angle calculating on it.


![image](https://github.com/shivamjha377/AI-Gym-Project-Dumbbell-Counter-/assets/57248088/9bdccce4-7816-40f2-adc4-1d915ac596ec)


 
In this feed we use cv2.videocapture(0) which opens the camera of our laptop. Then we used the while loop till the camera is opened by using cap.read() function. After this we use cv2.imshow() for  showing the showing and visualizing the webcam image.

 
 

2.Make detections:
In this section of code we write the code which is used for detecting the different poses in the body.
In this we have used:
A) min_detection_confidence: It is used for reading the detections in the webcam.
B) min_tracing_confidence: It is used for mainting the state of the webcam.
Now we recolor our image by converting the image form bgr to rgb by using the  cv2.cvtColor().

![image](https://github.com/shivamjha377/AI-Gym-Project-Dumbbell-Counter-/assets/57248088/82872974-b399-48ef-86da-f6d0b2cf6e1b)
 

At first we write the flag false then we detect the model and store the detection in the result variable after this we write the flag as true and at last we again convert our image back to bgr as we are going to re-render it by using openCV.
 
In this section we are also changing the colour of our detection lines by using  . 
Also we are changing the color of different dots in this pose model by using mp_drawing.draw_landmarks() functions.
 
3.Deteminig joints: This section is used for detecting the different joints in our body and are used to find Where our elbow is?, where our wrist is? , where our finger is? Etc within our body.
In this we have used the try and except blocks which is used to declare the finding of the landmarks.

![image](https://github.com/shivamjha377/AI-Gym-Project-Dumbbell-Counter-/assets/57248088/3742d70e-f158-47fe-a50f-de10bc16d57c)
 
We have used try and except blocks because there may be the cases when we cannot able to detect the landmarks so in that case we simply pass using the 'pass' statement.
 
We can also find the different joints landmarks on our output  screen by using this code which tells the mapping of the code.
For lndmark in mp_pose.Poselandmarks():
Print(lndmark) 
In this sections we extracts the different pose landmarks.
 
 

4.Calcultate angles: It uses the data of above section to calculate the angles of our arms. In this project we just specify the angle of our left hand only. It is used to calculate the angles between any three points using the trignometry. 

![image](https://github.com/shivamjha377/AI-Gym-Project-Dumbbell-Counter-/assets/57248088/aa4ed0f9-6866-488e-8699-01e77d47beec)

We use to calculate the angle for our left hand by detecting the point on left shoulder, left elbow and left wrist.


![image](https://github.com/shivamjha377/AI-Gym-Project-Dumbbell-Counter-/assets/57248088/158a3f42-ae27-4e6a-8947-f6a5fc97cb32)
We will use certain trignometry functions for finding the angles.
In this we will use our numpy model which is used in mathematical functions. Here we will use trignometric functions operations in order to find the left hand angle.
We have declared a function calculate_angles(a,b,c) where a,b,c are the first, mid and last point and at first we convert the angle into the radian then we covert it into the angle and the maximum limit of  the
The moving the hand is 180 degrees.
We will create three variables shoulder, elbow and wrist ..  
Radians(): 
The radians() method converts angle x from degrees to radians
Angle(): 
numpy.angle() function is used when we want to compute the angle of the complex argument. A complex number is represented by “ x + yi ” where x and y are real number and i= (-1)^1/2. The angle is calculated by the formula tan-1(x/y).
Syntax : numpy.angle(z, deg=0)


5.curl counter
In this module we have written the code which will able to use above calculate sections code for counting the curls of our dumbell. 
![image](https://github.com/shivamjha377/AI-Gym-Project-Dumbbell-Counter-/assets/57248088/63f184bd-2817-466f-8f10-165a63b9e9cb)

It will count the dumbell up and down movement and based on the action of up and down it will increase the count operation.

![image](https://github.com/shivamjha377/AI-Gym-Project-Dumbbell-Counter-/assets/57248088/60645ccb-0eb7-4ba2-bc5c-ff471ba665a2)
In this method we visulaize our angle_calculator() so we can see in our real time camera feed
 
       
