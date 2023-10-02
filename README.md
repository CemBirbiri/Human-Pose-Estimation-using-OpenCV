This repository consist of human pose estimation project using OpenCV. 

Human Pose estimation is a computer vision task that represents the orientation of a person in a graphical format. This technique is widely applied to predict a person’s body parts or joint position. It is one of the most exciting areas of research in computer vision that has gained a lot of traction because of its abundance of applications that can benefit from such a technology.

In this project, human pose estimation of people in a video clip was applied to draw bounding boxes of body and face, and lines for legs and arms. A JSON file were created using the [OpenPose algorithm](https://cmu-perceptual-computing-lab.github.io/openpose/web/html/doc/). OpenPose has represented the first real-time multi-person system to jointly detect human body, hand, facial, and foot keypoints (in total 135 keypoints) on single images. It returns a JSON file where the coordinates of face and body parts are given. Using these coordinates one can draw bounding boxes of the face and body as well as lines for legs and arms.

The following steps were applied for human pose estimation.

1. Divide the given video into frames using [OpenCV](https://opencv.org/).
2. Read the JSON file coming from the [OpenPose algorithm](https://cmu-perceptual-computing-lab.github.io/openpose/web/html/doc/) algorithm, and detect the coordinates of face, body, arms and legs.
3. Using the coordinates of body parts, draw bounding boxes for the face and body, lines for arms and legs for all the frames.
4. Create an output video using the final frames.

You can find the Jupyter Notebook of the project on XXX. I will explain all the steps below.

# Human Pose Estimation using OpenCV


### 1- Divide the video into frames using OpenCV

I used the [cv2.VideoCapture(video_path)](https://docs.opencv.org/3.4/d8/dfe/classcv_1_1VideoCapture.html) to frame the video. There are in totla 1864 frames and you can see some of them below.

<img width="397" alt="Screenshot 2023-10-02 at 12 21 18" src="https://github.com/CemBirbiri/Human-Pose-Estimation-using-OpenCV/assets/46814542/6e07e574-1e36-48d9-b62f-0d672bc5c8c7">

### 2- Draw Bounding box of Face

Before implemeting a generic for-loop to apply pose estimation algorithm to each frame, I would like to show you how to use body parts's coordinates to draw bounding boxes.

- Read the JSON file and extract the **face key points**. There are a total of 70 keypoints for the face.
- Find the center key point of the face(key point #33).
- Find the endmost points on the left and right to find the width of the bounding box (keypoints #16 and #0)
- Find the endmost points on top and bottom to find the height of the bounding box (keypoints #24 and #8).
- Plot the bounding box of the face.

<img width="668" alt="Screenshot 2023-10-02 at 12 38 47" src="https://github.com/CemBirbiri/Human-Pose-Estimation-using-OpenCV/assets/46814542/780200c9-d2fc-4965-add9-124db36d4e66">


### 3- Draw Bounding box of Body


- Read the JSON file and extract the **body key points**. There are a total of 25 keypoints for the face.
- Find the center key point of the body.
- Finf the height of the body: The distance between the y-coordinates of the endmost top(#1) and bottom(#8) points.
- Find the width of the body: The distance between the x-coordinates of the endmost right(#1) and endmost left(#5) points.
- Plot the bounding box of the body.

<img width="808" alt="Screenshot 2023-10-02 at 12 38 31" src="https://github.com/CemBirbiri/Human-Pose-Estimation-using-OpenCV/assets/46814542/d7c9b224-259f-4a5c-a6ca-e90f6a544df6">


