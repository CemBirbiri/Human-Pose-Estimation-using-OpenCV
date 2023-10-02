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


### 1- Divide the video into frames using OpenCV.

cv2.VideoCapture(video_path) is used to frame the video.

```
import numpy as np
import cv2
from matplotlib import pyplot as plt
import json


def extract_frames(video_path):
  print('Extracting video frames...')
  #1. Extract video frames save them as .jpg format
  #Arguments:
    # video_path: file path of the video
  #Return: frames_jpg: list of video frames in .jpg format

  #Read the video using OpenCV
  capture = cv2.VideoCapture(video_path)
  frameNr = 0
  #create a list to save the frames
  frames_jpg = []
  while (True):
    success, image = capture.read()
    if success:
      #Save the jpg image in a list
      frames_jpg.append(image)
    else:
      break
    frameNr = frameNr+1
    #print(frameNr)
  capture.release()
  return frames_jpg

#path of the example video
video_path = "/content/drive/MyDrive/Prof-Lucile-Sassatelli-project/clip_05.mp4"
video_frames_jpg = extract_frames(video_path)
}
```
