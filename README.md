# Automated Analysis of Tennis Player Performance in a rally using AI.


 In the competitive world of tennis, precise performance metrics such as player speed, ball shot speed, and shot count are crucial for training and improvement. Currently, coaches and analysts manually track these metrics, which is time-consuming and prone to errors. Automating this process using video analysis could provide accurate and real-time data, enhancing training efficiency and player performance.


![8skofx](https://github.com/saivarshitnune/Tennis-Analyzer/assets/121888709/64e217b6-2cf1-4396-b03c-ebe45c71d507)


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

     ![8skomq](https://github.com/saivarshitnune/Tennis-Analyzer/assets/121888709/175d07aa-71ae-4ce2-9eef-52a6c61ccb23)


  2. As we have got court key points now detect and track the players using YOLOV8. Post completion of detection and tracking the players we need 
     to filter the players finding minimum distance between players and keypoints. Finally we can sort the distances and filter the players who 
     are actually playing in the court. 

     ![Screenshot (166)](https://github.com/saivarshitnune/Tennis-Analyzer/assets/121888709/a700b86a-464e-4e9d-aaf9-00d83822d247)

 3. Train the tennis balls with YOLO V5 model and load the best weights to detect and track the tennis ball accurately in each frame in our input 
    video and also need to interpolate the missing ball positions by converting the ball positions into a dataframe.
    
    ![Screenshot (168)](https://github.com/saivarshitnune/Tennis-Analyzer/assets/121888709/75ebfabc-2934-4a4a-bb53-3bcbfa18b66c)


 5. Create a function to draw the mini court in order to find the speed of the ball and players in each frame by extracting the positions of ball and players.

    ![Screenshot (169)](https://github.com/saivarshitnune/Tennis-Analyzer/assets/121888709/8c3bc82d-1e98-4d8b-b549-66dcf1ec9036)

 6. Define player statistics data and ball detection shots to find the players averge shot speed , players total shot speed and no of shots by 
    each player.
    
# Output 
Here is a screenshot from one of the frame of output video:
![image](https://github.com/saivarshitnune/Tennis-Analyzer/assets/121888709/a52943ab-0e31-4130-83ac-223cc4f1ed00)


# Models Used
1) YOLOV8 for player detection
2) Fine Tuned YOLOV5 for tennis ball detection
3) Court Key point extraction using ResNet50 Pretrained model


# Conclusion:-
 The project demonstrates a significant step forward in the realm of sports analytics, showcasing the potential of AI to transform how performance data is captured and analyzed. By automating these processes, coaches and analysts can focus more on strategy and improvement rather than on time-consuming manual tracking. This not only increases accuracy but also allows for real-time insights, paving the way for more effective training regimens and better player development.
