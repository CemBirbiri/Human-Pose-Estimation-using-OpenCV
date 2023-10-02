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

- Write a python program that will


### 1. Generate an output video with (as for example in Fig. 1, suggested tool/library usage: ffmpeg, opencv):

bounding boxes around the head (facial organs not including neck) and upper body (neck to hip)
lines that show the articulation of the limbs (arms from the shoulder to elbow, elbow to wrist, legs from hip to knee, knee to ankle).

<img width="737" alt="Screenshot 2023-10-02 at 12 08 40" src="https://github.com/CemBirbiri/Human-Pose-Estimation-using-OpenCV/assets/46814542/b442435b-9255-4c8e-be73-e2977f576ffa">



### 2.   Output the information as tabular data in a CSV file. Each row should use comma
delimiters to separate values for :


  *  (a) **Frame and person IDs:** 'frame_ID','person_ID',
  *  (b) **Head bounding box center coordinates, width, and height:** 'head_center_x',
'head_center_y', 'head_width', 'head_height',
  *  (c) **Upper body bounding box center coordinates, width, and height:**
'body_center_x', 'body_center_y', 'body_width', 'body_height'
  *  (d) **Left and right shoulder coordinates with a unit vector (i.e. length of vector is 1) that points towards elbow and length parameter, and unit vector that points from elbow
towards wrist with length parameter:** 'left_shoulder_x', 'left_shoulder_y',
'left_shoulder_vec_x', 'left_shoulder_vec_y', 'left_upper_arm_length','left_elbow_vec_x',
'left_elbow_vec_y', 'left_lower_arm_length', 'right_shoulder_x',
'right_shoulder_y','right_shoulder_vec_x', 'right_shoulder_vec_y',
'right_upper_arm_length','right_elbow_vec_x', 'right_elbow_vec_y',
'right_lower_arm_length',
  *  (e) **Similarly to d. and e., for the left/right hip to knee, and the knee to ankle:**
'left_hip_x', 'left_hip_y','left_hip_vec_x', 'left_hip_vec_y',
'left_upper_leg_length','left_knee_vec_x', 'left_knee_vec_y',
'left_lower_leg_length','right_hip_x', 'right_hip_y','right_hip_vec_x', 'right_hip_vec_y',
'right_upper_leg_length','right_knee_vec_x', 'right_knee_vec_y', 'right_lower_leg_length'


If a value is missing, it should be set to -1.

- comment and document your code so that it is easily reusable
- your code should be as generic as possible to deal with all similarly named and formatted
video-json file pairs


