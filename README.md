Human Pose estimation is a computer vision task that represents the orientation of a person in a graphical format. This technique is widely applied to predict a person’s body parts or joint position. It is one of the most exciting areas of research in computer vision that has gained a lot of traction because of its abundance of applications that can benefit from such a technology.

In this project, human pose estimation of people in a video clip was applied to draw bounding boxes of body and face and lines for legs and arms. A JSON file was created using the [OpenPose algorithm](https://cmu-perceptual-computing-lab.github.io/openpose/web/html/doc/). OpenPose has represented the first real-time multi-person system to jointly detect human body, hand, facial, and foot key points (in total 135 key points) on single images. It returns a JSON file where the coordinates of the face and body parts are given. Using these coordinates one can draw bounding boxes of the face and body as well as lines for legs and arms.

The following steps were applied for human pose estimation.

1. Divide the given video into frames using [OpenCV](https://opencv.org/).
2. Read the JSON file coming from the [OpenPose algorithm](https://cmu-perceptual-computing-lab.github.io/openpose/web/html/doc/) algorithm, and detect the coordinates of the face, body, arms, and legs.
3. Using the coordinates of body parts, draw bounding boxes for the face and body, and lines for arms and legs for all the frames.
4. Create an output video using the final frames.

You can find the Jupyter Notebook of the project on [HPE-using-OpenCV.ipynb](https://github.com/CemBirbiri/Human-Pose-Estimation-using-OpenCV/blob/main/HPE-using-OpenCV.ipynb). I will explain all the steps below.

# Human Pose Estimation using OpenCV


### 1- Divide the video into frames using OpenCV

I used the [cv2.VideoCapture(video_path)](https://docs.opencv.org/3.4/d8/dfe/classcv_1_1VideoCapture.html) to frame the video. There are in total 1864 frames and you can see some of them below.

<img width="397" alt="Screenshot 2023-10-02 at 12 21 18" src="https://github.com/CemBirbiri/Human-Pose-Estimation-using-OpenCV/assets/46814542/6e07e574-1e36-48d9-b62f-0d672bc5c8c7">

### 2- Draw the Bounding box of the Face

Before implementing a generic for-loop to apply a pose estimation algorithm to each frame, I would like to show you how to use body parts's coordinates to draw bounding boxes.

- Read the JSON file and extract the **face key points**. There are a total of 70 key points for the face.
- Find the center key point of the face(key point #33).
- Find the endmost points on the left and right to find the width of the bounding box (key points #16 and #0)
- Find the endmost points on top and bottom to find the height of the bounding box (key points #24 and #8).
- Draw the bounding box of the face using [cv2.circle()](https://docs.opencv.org/4.x/dc/da5/tutorial_py_drawing_functions.html) function.

<img width="668" alt="Screenshot 2023-10-02 at 12 38 47" src="https://github.com/CemBirbiri/Human-Pose-Estimation-using-OpenCV/assets/46814542/780200c9-d2fc-4965-add9-124db36d4e66">


### 3- Draw the Bounding box of the Body


- Read the JSON file and extract the **body key points**. There are a total of 25 key points for the face.
- Find the center key point of the body.
- Find the height of the body: The distance between the y-coordinates of the endmost top(#1) and bottom(#8) points.
- Find the width of the body: The distance between the x-coordinates of the endmost right(#1) and endmost left(#5) points.
- Draw the bounding box of the body using [cv2.circle()](https://docs.opencv.org/4.x/dc/da5/tutorial_py_drawing_functions.html) function.

<img width="808" alt="Screenshot 2023-10-02 at 12 38 31" src="https://github.com/CemBirbiri/Human-Pose-Estimation-using-OpenCV/assets/46814542/d7c9b224-259f-4a5c-a6ca-e90f6a544df6">

### 4- Draw Lines for Arms and Legs

- Get the index of body parts and calculate the x and y coordinates.
- Draw the lines for the legs and arms using [cv2.line()](https://docs.opencv.org/4.x/dc/da5/tutorial_py_drawing_functions.html) function.

<img width="688" alt="Screenshot 2023-10-02 at 12 46 08" src="https://github.com/CemBirbiri/Human-Pose-Estimation-using-OpenCV/assets/46814542/eb57a227-c79d-40bf-b037-edf809430c81">

### 5- Create a Pipeline that does all the previous steps to each video frame

- Read all the frames one by one and draw bounding boxes & lines.
- Create a new video from the final frames.

The video before human-pose estimation:

https://github.com/CemBirbiri/Human-Pose-Estimation-using-OpenCV/assets/46814542/83573816-004e-422a-91a5-cca0db349a13


The video after human-pose estimation:


https://github.com/CemBirbiri/Human-Pose-Estimation-using-OpenCV/assets/46814542/143a99de-13c9-4efb-8013-22fbdf9552bd





# Conslusion
In this work, I implemented an end-to-end pipeline for a human pose estimation task. First, the video is divided into frames, then for each frame, the bounding boxes of face and body & lines of arms and legs are drawn using OpenCV. At the end, a new video is created using the final frames.
