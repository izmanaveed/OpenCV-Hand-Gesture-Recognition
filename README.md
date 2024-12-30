# OpenCV-Hand-Gesture-Recognition

The aim of this project is to identify single and multiple hands through skeletonization.

## Methodology
### Single hand gesture recognition
![image](https://github.com/user-attachments/assets/dab373ec-80f9-4e99-a81d-4f7f3d29d481)
#### Image thresholding
For every pixel, the same threshold value is applied. If the pixel value is smaller than the threshold, it is set to 0, otherwise it is set to a maximum value.

#### Convexity Defects
The function _cv2.convexityDefects()_ for finding the convexity defects of a contour. This takes as input the contour and its corresponding hull indices and returns an array containing the convexity defects as output. The output contains an array where each row contains 4 values [start point, endpoint, farthest point, approximate distance to the farthest point].
First, we find the contours for the hand using the concept of skeletonization, then we find the convex hull for the contour. Then we find the convexity defects and identify number of fingers.

![image](https://github.com/user-attachments/assets/57ebe59d-4164-4f0c-862e-33b53c217e94)

### Multiple hand recognition
![image](https://github.com/user-attachments/assets/6f3e4825-be0e-4091-88ce-a30ff7fe275b)
#### Media Pipe framework
Implementation for the second part of the project makes use of Media Pipe. MediaPipe Hands is a high-fidelity hand and finger tracking solution. It employs machine learning (ML) to infer 21 3D landmarks of a hand from just a single frame. Current state-of-the-art approach methods rely primarily on powerful desktop environments for inferencing, whereas this method outperforms other methods and achieves very good results in real-time.
![image](https://github.com/user-attachments/assets/f89ee7c5-b11b-4cd7-b714-487fd25c1378)

#### Hand Landmark Model
Hand landmark model performs precise key point localization of 21 3D hand-knuckle coordinates inside the detected hand regions via regression, that is direct coordinate prediction. The model learns a consistent internal hand pose representation and is robust even to partially visible hands and self-occlusions.

#### Applying media pipe hand pose
The first two important metrics associated are _min_detection_confidence_ and _min_tracking_confidence_. When we first use the media pip hand model, it is going to detect our hand and then track it. We set min_detection_confidence to be 80% accurate for first detection and min_tracking_confidence as 50% accuracy for tracking after the first detection. Setting it to a higher value can increase robustness of the solution, at the expense of a higher latency. We can set the number of hands that need to be recognized using max_num_hands.
![image](https://github.com/user-attachments/assets/5eb5c1d5-c97c-4314-9b2d-55b3c7f3f1b5)

