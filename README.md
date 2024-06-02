# Automated Analysis of Tennis Player Performance in a rally using AI.


 In the competitive world of tennis, precise performance metrics such as player speed, ball shot speed, and shot count are crucial for training and improvement. Currently, coaches and analysts manually track these metrics, which is time-consuming and prone to errors. Automating this process using video analysis could provide accurate and real-time data, enhancing training efficiency and player performance.

![tenor](https://github.com/saivarshitnune/Tennis-Analyzer/assets/121888709/73a8b6e0-447b-49c8-a8f9-22ea12ea4795)


# Approach : 
1. Develop a system to accurately measure the speed of tennis players during a match from a video.
2. Implement a method to determine the speed of the tennis ball immediately after it is hit by the player.
3. Create an algorithm to automatically count the number of shots taken by each player during the video.

# limitations :
1. Player Identification and Tracking
2. Ball Detection and Tracking
3. Speed Calculation of Player and Ball
4. Shot Detection


# Work around :
1. Player can be identified and tracked using YOLO V8 but need to filter the players who are playing the match and the extra players using tennis court key points.

2. By applying the YOLOV8 model on the input video ball is not detected in each frame. In order to solve the problem need to train on the tennis balls dataset using YOLO 

3. Speed of the ball can be calculated by distance covered by ball in metres to the ball shot time in seconds. In order to calculate the distance covered by the ball we need to get the ball mini court detections, calculate the width of mini court and double line width of the court.

4. Speed of the player can be calculated by distance covered by player in metres to the ball shot time in seconds. In order to calculate the distance covered by the player we need to get the player mini court detections , calculate the width of mini court and double line width of the court
5) Need to write a function to find the ball shot frame detections using ball positions

# Solution : 
  1. Train the Tennis court key points using CNN (ResNet50) and load the best weights to extract court key points , court line detector.
     
# Output Videos
Here is a screenshot from one of the frame of output video:
![image](https://github.com/saivarshitnune/Tennis-Analyzer/assets/121888709/a52943ab-0e31-4130-83ac-223cc4f1ed00)


# Models Used
1) YOLO v8 for player detection
2) Fine Tuned YOLO v5 for tennis ball detection
3) Court Key point extraction using ResNet50 Pretrained model

# Requirements
1) python3.8
2) ultralytics
3) pytroch
4) pandas
5) numpy
 6) opencv
