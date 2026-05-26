# Hardware

This section of the Research folder aims to focus on the hardware capabilities of the robot. It focuses on the pros and cons of multiple different options.


## Components Required:

1. MCU (1)
2. Motors (2)
3. Motor Driver (1)
4. IMU (1)
5. Wheels (2)
6. Power Supply (2)
7. Buck Converter (1)
8. Cardboard (TBD)

## Tools Required:

1. Exacto-Knife (1)
3. Hot GLue Gun (1)
4. PC (1)
5. Soldering Iron/Kit


## Component Spesifications:

* **ESP32:** Main microcontroller responsible for handling motor and IMU information
* **GEARED DC Motor 3-6V 1:48 ratio:** Smaller gear ratio means more faster and smaller movemenets, optimal for micro adjestments
* **TB6612FNG Motor Driver (Previously the L298N Motor Drive Controller Board):** A motor driver is needed to ensure the high voltage motors are supplied with enough. It also provides precise control over the motors. Operates at 3.3V logic, more suited and efficent for my ESP32 setup than the L298N,
* **MPU6050:** It's a 3 axis axel and gyroscope. This is needed to detect the state of the robot, whether it's tilting forward or backwards.
* **Wheel:** 65mm wheels are used.
* **2 x 18650 2000 mAH 3.7V Batteries:** Provides roughly 7.4V enough to be stepped down but also stable enough to power the DC motors. The whole circuit is connected in parallel which means both paths draw 7.4V and their own current.
* **LM2596S:** Buck converter module used to step down voltage to 5V for the 3.3v mcu. The freenove comes with an onboard voltage regular which can be fed directly into the 5V pin. The board itself operates at 3.3V along with every other GPIO pin on the ESP.


## Connections:

### TB6612FNG:
| TB6612FNG Pin | ESP32 Pin | Function |
| :--- | :--- | :--- |
| **STBY** | GPIO 4 | Standby (Set HIGH to run) |
| **AIN1** | GPIO 5 | Motor A Direction 1 |
| **AIN2** | GPIO 6 | Motor A Direction 2 (Replaces GPIO 12) |
| **PWMA** | GPIO 7| Motor A Speed |
| **BIN1** | GPIO 10 | Motor B Direction 1 |
| **BIN2** | GPIO 11 | Motor B Direction 2 |
| **PWMB** | GPIO 12 | Motor B Speed |
| **VCC**  | 3.3V    | Logic Power |
| **GND**  | GND     | Common Ground |
| **VM**   | Battery + | Motor Power |

### MPU-6050:
| MPU-6050 Pin | ESP32 Pin | 
| :--- | :--- |
| **VCC** | 3.3V |
| **GND** | GND |
| **SDA** | GPIO 8 |
| **SCL** | GPIO 9 |

### LM2596S :

| LM2596S Pin | Connection Pin |
| :--- | :--- |
| **IN+** | TB6612FNG VM |
| **IN-** | TB6612FNG GND |
| **OUT+** | ESP32 5V |
| **OUT-** | ESP32 GND|






