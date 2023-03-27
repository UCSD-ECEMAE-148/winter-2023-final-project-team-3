# Final Report for Team 3 (ECE/MAE 148)

## Team Members
* Nathaniel Barnaby - ECE
* Yang-Jie Qin - ECE
* Cheuk Hin Bryan Cheng - MAE
* Patrick Nguyen - MAE

## Project Overview
* Our initial final project was a combination of the usage of an IMU and GNSS to implement position tracking. An IMU is an inertial measurement unit, composing of gyros, accelerometers, and more sensors to track the movement of something. With these sensors, the car's location can be estimated off of a general initial GPS location with the addition to its movement measured by its speed, acceleration, turning, etc. This ended up being too complex for our team which resulted in little progress. We were then assigned new mini tasks which consists of using 2 of the sensors provided in our kits. The assignment was to use The OAK-D camera znd the lidar separately to measure depth of both a small (0.15m) object and a larger (0.5m) object at different distances. We ended up comparing results of both objects at distances of 0.5, 1, 2, 3, and 4 meters. We would then compare the outputed values from the sensores to what the actual correspond measurment. A comparison between the accuracy of depth finding between the Oak-D camera and lidar would also be necesasry. A second task was assigned which was to output a face recognition system out of the OAK-D camera. 

## Results
* For the depth finding assingment, both the camera and lidar were succesfully able to measure depth for the small and large object at the different ranges. For the camera, it was relatively accurate with margins of 0.1m for both the large and small object. The main issue we had with this feature is that further the object is from the camera, the harder it is to locate it on the cameras vision due to the colored depth ranges. This was relatively accurate. As for the lidar, it was also relatively accurate but we did encounter some difficulties. The further we got from the lidar, the less accurate our distances were. We believe this was due to our error in the calculations that produce the depth. With more time this could be calibrated to be spot on. Another issue we had was the speed of the lidar, because of this, we limited the range of the lidar to only be a few degrees rather than 360 degrees. With limiting our range, we sometimes had issues with keeping the objects within the range of the lidar so it took multiple attempts to get a distance. That being said, with figuring out how to get the lidar to work faster and further adjusting the calculations of distance, we believe the lidar is more accurate than the camera. They each have their pros and cons, the camera is good for rough but fast estimates where as the lidar is better for more precise measurements. 
* DepthAI Distance Measurement with ~0.5 m^2 Object Video Link: https://youtube.com/shorts/I1zaVxE-bjM?feature=share
* DepthAI Distance Measurement with 0.15 m^2 Box Video Link: https://youtube.com/shorts/GPADi4bS-fw?feature=share

* LiDAR Distance Measurement with ~0.5 m^2 Object Video Link: https://youtu.be/Ee81_VBHxKI
* LiDAR Distance Measurement with 0.15 m^2 Box Video Link: https://youtu.be/ARffTMx1PJ0

* As for the camera face recognition, we were succesfully able to output video display which recognizes faces. This is a relatively fast responding system. It outputs the number of faces it recognizes which we tested from 0-3 faces real time. There is some error within the system as it can be innacurate thinking other shiny objects and or parts of a face are another face. It is also not limited to stationary faces as it recognizes people moving too. 
* Face Recognition Video Link: https://youtu.be/nUz8OR_zHPA

## Gantt Chart
![Gantt](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/Gantt.png)

## Hardware: Mechanical Design

![Camera/flashlight Mount](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/camera_flashlight_mount.png)\
Camera/flashlight Mount

![Electronics Tray](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/electronics_tray.png)\
Electronics Tray

![Front/rear Electronics Plate Offset](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/front_rear_electronics_plate_offset.png)\
Front/rear Electronics Plate Offset

![GPS Mount](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/gps_mount.png)\
GPS Mount

![IMU Mount](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/imu_mount.png)\
IMU Mount

![Jetson Case Key Mount](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/jetson_case_key_mount.png)\
Jetson Case Key Mount

![Jetson Nano Main Case](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/jetson_nano_main_case.png)\
Jetson Nano Main Case

![Lidar Tower](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/lidar_tower.png)\
Lidar Tower

![Servo Voltage Converter](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/serve_voltage_converter.png)\
Servo Voltage Converter

![Vesc Power Distributor](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/vesc_power_distributor.png)\
Vesc Power Distributor

## Previous Designs


## Electronic Components
![Jetson Nano](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/jetson_nano.jpg)\
Jetson Nano

![OAK-D Camera](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/oak_d_lite_en.png)\
OAK-D Camera

![Lidar LD06](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/Lidar_LD06.jpg)\
Lidar LD06

## Electronic Wiring Schematic
![Electronic Wiring Schematic](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/electronic_schematic.png)

## Final Set Up
![Bird's Eye View](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/birds_eye.jpg)
Bird's Eye View

![Left View](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/left.jpg)
Left View

![Right View](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/right.jpg)
Right View


### Packages and Drivers
* cv2 (OpenCV)
* depthai (DepthAI)
* numpy
* math
* binascii
### Algorithms

### Schematics

## Milestones
* Face Recognition using DepthAI - Detects faces through a webcam and displays a count in the terminal
* Distance Measurement using DepthAI - Using the disparity between the left and right cameras of the OAKD, distance can be calculated. This was averaged over an area to give an estimated distance of an object.
* Distance Measurement using LiDAR - Using a LiDAR is is relatively simple to detect distances in a 360 degree range. By averaging distances over a very small range (0.4 degrees) we determined the distance of an object.

## Takeaways - LiDAR vs DepthAI
* LiDAR needs to be handcalibrated which caused a small amount of error for us at all distances, but this error seemed linear or almost static.
* DepthAI provided very accurate distances close to the camera but getting further away (3+ meters) the error seemed to begin growing exponentially.
* LiDAR appears to be the better option in most scenarios due to the smaller error, but some merit should be given to DepthAI for it's good performance at small distances.
* The error for small and large objects at different distances are shown below:



## Potential Future Work/Unaccomplished Goals
* Recognizing and labeling specific faces

## Presentations
Final Project Proposal: https://docs.google.com/presentation/d/1vLvXRnHzHm6p_IpEQy8KJgz--vOFd6M9xa7Q-qHD2Ls/edit?usp=sharing
Final Presentation: https://docs.google.com/presentation/d/17J6LZ2QZ177BDr7g3x7ZcxHlyUQ-m4LtXGy9BRernRI/edit?usp=sharing

## Acknowledgments
Professor Jack Silberman, TA Kishore Nukala, Moises Lopez-Mendoza, Design and Innovation Building, all of our wonderful classmates
