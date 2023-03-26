# Final Report

## Team Members
* Nathaniel Barnaby - ECE
* Yang-Jie Qin - ECE
* Cheuk Hin Bryan Cheng - MAE
* Patrick Nguyen - MAE

## Project Overview


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


## Electronic Wiring Schematic

## Final Set Up
![Bird's Eye View](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/birds_eye.jpg)
Bird's Eye View

![Left View](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/left.jpg)
Left View

![Right View](https://github.com/UCSD-ECEMAE-148/winter-2023-final-project-team-3/blob/main/images/right.jpg)
Right View

### Software

```python

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
```

```python
def __init__(self, addr=0x69, poll_delay=0.0166, sensor=SENSOR_MPU6050, dlp_setting=DLP_SETTING_DISABLED):
        self.sensortype = sensor
        if self.sensortype == SENSOR_ICM20948:
            from icm20948 import ICM20948
#            self.sensor = ICM20948(addr)
            self.sensor = ICM20948(
                address_ak=AK8963_ADDRESS,
                address_mpu_master=addr,  # In 0x68 Address
                address_mpu_slave=None,
                bus=1,
                gfs=GFS_1000,
                afs=AFS_4G,
                mfs=AK8963_BIT_16,
                mode=AK8963_MODE_C100HZ)
            if(dlp_setting > 0):
                self.sensor.bus.write_byte_data(self.sensor.address, CONFIG_REGISTER, dlp_setting)

        elif self.sensortype == SENSOR_MPU6050:
            from mpu6050 import mpu6050 as MPU6050
            self.sensor = MPU6050(addr)
        
            if(dlp_setting > 0):
                self.sensor.bus.write_byte_data(self.sensor.address, CONFIG_REGISTER, dlp_setting)
        
        else:
            from mpu9250_jmdev.registers import AK8963_ADDRESS, GFS_1000, AFS_4G, AK8963_BIT_16, AK8963_MODE_C100HZ
            from mpu9250_jmdev.mpu_9250 import MPU9250

            self.sensor = MPU9250(
                address_ak=AK8963_ADDRESS,
                address_mpu_master=addr,  # In 0x68 Address
                address_mpu_slave=None,
                bus=1,
                gfs=GFS_1000,
                afs=AFS_4G,
                mfs=AK8963_BIT_16,
                mode=AK8963_MODE_C100HZ)
            
            if(dlp_setting > 0):
                self.sensor.writeSlave(CONFIG_REGISTER, dlp_setting)
            self.sensor.calibrateMPU6500()
            self.sensor.configure()
```

### Packages and Drivers
cv2
### Algorithms

### Schematics

## Milestones

## Potential Future Work/Unaccomplished Goals

## Presentations
Final Project Proposal: https://docs.google.com/presentation/d/1vLvXRnHzHm6p_IpEQy8KJgz--vOFd6M9xa7Q-qHD2Ls/edit?usp=sharing
Final Presentation: https://docs.google.com/presentation/d/17J6LZ2QZ177BDr7g3x7ZcxHlyUQ-m4LtXGy9BRernRI/edit?usp=sharing

## Acknowledgments
Professor Jack Silberman, TA Kishore Nukala, Moises Lopez-Mendoza, Design and Innovation Building, all of our wonderful classmates
