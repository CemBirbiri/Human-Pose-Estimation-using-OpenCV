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

Our task is to:

- Write a python program that will generate an output video with (as for example in Fig. 1, suggested tool/library usage: ffmpeg, opencv):

bounding boxes around the head (facial organs not including neck) and upper body (neck to hip)
lines that show the articulation of the limbs (arms from the shoulder to elbow, elbow to wrist, legs from hip to knee, knee to ankle).
<img width="737" alt="Screenshot 2023-10-02 at 12 08 40" src="https://github.com/CemBirbiri/Human-Pose-Estimation-using-OpenCV/assets/46814542/b442435b-9255-4c8e-be73-e2977f576ffa">



