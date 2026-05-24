# Technical

This sections of the Research folder aims to explore the software and physical aspect of creating the robot. It looks at what type of design, layout, or code is possible for the robot to work.

## MPU6050 Calibration and Setup

To step up properly the MPU6050, we need it to communicate with I2C first (Pin 8, 9). The calibration is done through an Arduino IDE libaray called "MPU6050_Light" by rfetick which automatically callibrates the sensor with this line of code:

```
mpu.calcOffsets();
Serial.println("Calibration done!\n");
```
Given my values came back with +-1 degree within 0 while lying flat, sensor values and calibration seemed normal. The only downside to this, was that the values took time to reach +- 1 within 0- that is not acceptable with a robot that needs accurate information straight away.

To combat this, we can use the built in Offset Commands to find these values:

```
 Serial.print("mpu.setGyroOffsets("); //Calculates Offsets For Gyro
  Serial.print(mpu.getGyroXoffset()); Serial.print(", ");
  Serial.print(mpu.getGyroYoffset()); Serial.print(", ");
  Serial.print(mpu.getGyroZoffset()); Serial.println(");"); // Prints outcomes

  Serial.print("mpu.setAccOffsets("); // Calclulates Offtsets For Accel
  Serial.print(mpu.getAccXoffset()); Serial.print(", ");
  Serial.print(mpu.getAccYoffset()); Serial.print(", ");
  Serial.print(mpu.getAccZoffset()); Serial.println(");"); // Prints outcomes
```

