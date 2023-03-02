# Social-Distancing-Detection

YOLOv3 weights is to be downloaded from:
https://pjreddie.com/media/files/yolov3.weights
and copied into folder named "models"

## REQUIREMENTS
numpy => v.1.19.2 <br>
scipy => v.1.4.1 <br>
imutils => v.0.5.3 <br>
opencv => v.4.2.0.32 <br>
argparse => v.1.4.0 <br>

## INTRODUCTION
The framework uses object recognition paradigm to identify humans in multiple Image Sequences. The detection model identifies peoples using detected bounding box information. Using the Euclidean distance, the detected bounding box centroid’s pairwise distances of people are determined.
This tool has the following features:
  1. Detect Humans in the frame with yolov3
  2. Calculates the distance between every human who is detected in the frame.
  3. Shows how many people are at High, Low and Not at risk.
  
## PROPOSED METHOD
### Input:
1. Video recorded by CCTV camera or the pre-filmed video of people in a crowded area.
2. Input frames are monocular (taken from a single camera).
3. Drawn 7 points: 4 - Region of Interest (ROI), 3 - Horizontal and Vertical direction

<u> For Person Detection: </u> <br>
Yolov3.weights, Yolov3.cfg <br>
The neural network model architecture is stored in the yolov3.cfg file and the pre-trained weights of the neural network are stored in yolov3.weights.

### Output:
<b> High Risk: </b> Red Bounding Box <br>
<b> Low Risk: </b> Yellow Bounding Box <br> 
<b> No Risk: </b> Green Bounding Box <br>

## ALGORITHM
Step 1: Input real time video or pre-recorded video.
Step 2: Divide the video into number of frames. <br>
Bird's Eye view (Input):
Step 3: Use the first frame to get Region of Interest (ROI)
Step 4: Get the Bird's eye view of ROI using Perspective Transform.
Step 5: Calculate horizontal and vertical unit length from points marked in first frame. <br>
Bird's Eye View (Processing):
Step 6: Detect people in frame and get center point.
Step 7: Project detected points in Bird's eye view.
Step 8: Find distance between points using horizontal and vertical unit length. <br>
Bird's Eye View (Output):
Step 9: Display Bird's eye view (High Risk: Red, Low Risk: Yellow, No Risk: Green) <br>
Final Output:
Step 10: Display line between people who are near and risk possessed to them by drawing different color bounding boxes.

## CODE FLOW
![Screenshot from 2023-03-02 17-46-16](https://user-images.githubusercontent.com/68748665/222426330-fdc61c84-84de-4f81-8125-467d4eb6633b.png)

## BLOCK DIAGRAM
![Screenshot from 2023-03-02 17-47-14](https://user-images.githubusercontent.com/68748665/222426538-1da9d88c-458a-4fc5-b5a7-14dcc1d667f4.png)

## INPUT
![Web capture_2-3-2023_174836_](https://user-images.githubusercontent.com/68748665/222426808-86e9988c-a39c-48a4-9c0e-0199d69313d8.jpeg)

## OUTPUT
![Web capture_2-3-2023_17499_](https://user-images.githubusercontent.com/68748665/222426942-0a8ca237-77ea-4483-8b7a-2475913f110d.jpeg)

## CONCLUSION
In this way, YOLOV3 trained on COCO dataset can be used to detect pedestrians which can be further implemented to get Euclidean Distance by converting real world image into Bird’s Eye View. This distance is then used to find social distance violation which is then projected in the form of color coded bounding boxes. 
However, like every other computerized system YOLOv3 also has it’s limitations that includes counting of a person’s shadow as another pedestrian, recognizing far distant object as pedestrian and in some cases not being able to process pedestrian because of background object. 
Hence, the horizon of these errors can be narrowed down with more neural network training and feeding more accurate data into COCO dataset and YOLOv3 configuration.
