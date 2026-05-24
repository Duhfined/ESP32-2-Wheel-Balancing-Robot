# Technical

This sections of the Research folder aims to explore the software and physical aspect of creating the robot. It looks at what type of design, layout, or code is possible for the robot to work.

## MPU6050 Calibration and Setup

To step up properly the MPU6050, we need it to communicate with I2C first (Pin 8, 9). The calibration is done through an Arduino IDE libaray called "MPU6050_Light" by rfetick which automatically callibrates the sensor with this line of code:

```
mpu.calcOffsets();
Serial.println("Calibration done!\n");
```

