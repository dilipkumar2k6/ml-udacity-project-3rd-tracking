# Writeup: Track 3D-Objects Over Time

Please use this starter template to answer the following questions:

## 1. Write a short recap of the four tracking steps and what you implemented there (filter, track management, association, camera fusion). Which results did you achieve? 
1. Extended Kalman Filter (EKF)
Implemented a complete Kalman filter with 6 dimensions
- 3 dimensions for the position (x, y, z) and 
- 3 dimensions for the velocity (vx, vy, vz). 
This is a great achievement because it is the most important part of a tracking system with sensor fusion support.

2. Track Management
Programmed a module to create new tracks, delete old tracks, and update the states of current tracks, based on the information obtained by the measurements. Used a dictionary whose keys are the frames and whose values are lists that accumulate the presence or absence of camera measurements and lidar measurements.

3. Data Association
The algorithm to associate tracks with measurements matches the nearest pair of track and measurement in the space formed by the Mahalanobis Distance (MHD), which is a space deformed by the statistical expectations of positions and velocities.

4. Camera-Lidar Sensor Fusion
This is the final step to complete the whole sensor fusion system. Coordinates from 2 different sensors with different geometries are transformed into vehicle coordinates by using the homogeneous transformation matrices. In like manner, vehicle coordinates are transformed into the corresponding sensor coordinates in order to compute hx and the EKF's Jacobian.
### Which part of the project was most difficult for you to complete, and why?
The most difficult part of the project was to fully understand the overall structure of the project. In addition to completing all the TODOs, I also needed to read the source code of all the Python files in the whole project. Exercises I had done before was very helpful though. I had to go through these exercises to refer the concepts. 

## 2. Do you see any benefits in camera-lidar fusion compared to lidar-only tracking (in theory and in your concrete results)? 
A significant improvement in the accuracy was observed when implemented Step 4, which fuses lidar measurements with camera measurements. Resolving the ambiguities of the video in Step 4 would be very difficult without camera measurements.

Camera measurements are ambiguous in the lines of ray tracing. Throughout these lines, any depth is valid and ambiguous. This ambiguity is resolved by using lidar measurements which have accurate depth information. Moreover, in the project there were big gaps of false negatives, lack of some lidar measurements. So, the fusion of cameras and lidars compensate their weaknesses.

## 3. Which challenges will a sensor fusion system face in real-life scenarios? Did you see any of these challenges in the project?
Cameras are less accurate at night and at estimating distances. Hence, sensor fusion systems must deal with these inaccuracies. Fortunately, the EKF has the mathematical foundations to deal with noisy measurements properly.

Yes, I saw in the project that camera measurements were less accurate than lidar measurements. Fortunately, theses cameras recorded videos in the day, not in the night, which would make this project harder.

## 4. Can you think of ways to improve your tracking results in the future?
There are lot of code to understand and then make changes. Given timeline is very short and also course didn't teach all the components. It made very hard for me to understand and took lot of time. 

# Results
Sensor Fusion and Object Tracking using Resnet for each steps.
## 0 - Withoug making any changes in TODOs
![](assets/Step%20-%200%20-%20Without%20Making%20Any%20change%20results.png)

![](assets/Step%20-%200%20-%20Without%20Making%20Any%20change%20RMSE.png)
## 1 - After making changes for Extended Kalman Filter (EKF)
![](assets/Step%20-%201%20-%20Single%20target%20tracking%20results.png)

![](assets/Step%20-%201%20-%20Single%20target%20tracking%20RMSE.png)
## 2 - After making changes for Track Management
![](assets/Step%20-%202%20-%20Single%20target%20tracking%20results.png)

![](assets/Step%20-%202%20-%20Single%20target%20tracking%20RMSE.png)
## 3 - After making changes for Data Association
![](assets/Step%20-%203%20-%20Multi%20target%20tracking%20result.png)

![]('assets/Step%20-%203%20-%20Multi%20target%20tracking%20RMSE.png')
## 2 - After making changes for Camera-Lidar Sensor Fusion
![]('assets/Step%20-%204%20-%20Multi%20target%20tracking%20result.png')

![]('assets/Step%20-%204%20-%20Multi%20target%20tracking%20RMSE.png')
