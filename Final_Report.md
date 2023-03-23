# Final Report

## Team Members
* Nathaniel Barnaby - ECE
* Yang-Jie Qin - ECE
* Cheuk Hin Bryan Cheng - MAE
* Patrick Nguyen - MAE

## Project Overview


## Gantt Chart


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


## Electronic Wiring Schematic

## Final Set Up
![Bird's Eye View](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/birds_eye.jpg)
Bird's Eye View

![Left View](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/left.jpg)
Left View

![Right View](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/right.jpg)
Right View

### Software

'''Python

from __future__ import print_function
import qwiic_icm20948
import time
import sys

def runExample():

    IMU = qwiic_icm20948.QwiicIcm20948()
    print(IMU)

    if IMU.connected == False:
        print("The Qwiic ICM20948 device isn't connected to the system.", \
            file=sys.stderr)
        return

    IMU.begin()

    while True:
        if IMU.dataReady():
            IMU.getAgmt() # read all axis and temp from sensor, note this also updates all instance variables
            print(\
             '{: 06d}'.format(IMU.axRaw)\
            , '\t', '{: 06d}'.format(IMU.ayRaw)\
            , '\t', '{: 06d}'.format(IMU.azRaw)\
            , '\t', '{: 06d}'.format(IMU.gxRaw)\
            , '\t', '{: 06d}'.format(IMU.gyRaw)\
            , '\t', '{: 06d}'.format(IMU.gzRaw)\
            , '\t', '{: 06d}'.format(IMU.mxRaw)\
            , '\t', '{: 06d}'.format(IMU.myRaw)\
            , '\t', '{: 06d}'.format(IMU.mzRaw)\
            )
            time.sleep(0.03)
        else:
            print("Waiting for data")
            time.sleep(0.5)

if __name__ == '__main__':
    try:
        runExample()
    except (KeyboardInterrupt, SystemExit) as exErr:
        print("\nEnding Example 1")
        sys.exit(0)
'''

### Packages and Drivers

### Algorithms

### Schematics

## Milestones


## Potential Future Work/Unaccomplished Goals


### Hardware Design


### Software Design

## Progress Reports and Final Presentations


## Acknowledgments
Professor Jack Silberman, TA Kishore Nukala, Moises Lopez-Mendoza, Design and Innovation Building, all of our wonderful classmates