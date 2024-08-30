# Solar-Plates-automated-positioning-system


## Project Overview

The **Solar Plates Automated Positioning System** is a project aimed at optimizing the efficiency of solar energy capture by continuously adjusting the orientation of a solar panel to follow the sun's path using Light-Dependent Resistor (LDR) sensors and Arduino Uno control. This system enhances overall energy generation from solar panels, making solar energy a more practical and sustainable option.

## Group Details

- **Institution:** National Institute of Technology, Agartala
- **Course:** Industrial Instrumentation Project
- **Group:** 04
- **Contributors:**
  - 21UEI016 - Ankit Kumar
  - 21UEI017 - Aditya Kanu
  - 21UEI018 - Aten Debbarma
  - 21UEI019 - Pankaj Kumar Das
  - 21UEI020 - Ankit Kumar
- **Guided by:** Dr. Rupam Gupta Roy
- **Technical Assistants:** Kailash Pratim Phukan, Suraj Das

## Table of Contents

1. [Aim of the Project](#aim-of-the-project)
2. [Objective of the Project](#objective-of-the-project)
3. [Components Required](#components-required)
4. [Introduction](#introduction)
5. [Theory](#theory)
6. [Working of the Project](#working-of-the-project)
7. [Circuit Diagram](#circuit-diagram)
8. [Software Development](#software-development)
9. [Results](#results)
10. [Conclusion](#conclusion)
11. [Future Enhancements](#future-enhancements)
12. [References](#references)

## Aim of the Project

To design and implement a Sun Tracking Solar Panel System that optimizes the efficiency of solar energy capture by continuously adjusting the orientation of a solar panel to follow the sun's path using Light-Dependent Resistor (LDR) sensors and Arduino Uno control, thereby increasing the overall energy generation from solar panels.

## Objective of the Project

- Design and construct an Arduino-based Solar Tracker using Light-Dependent Resistor (LDR) sensors and a Servo Motor.
- Enhance solar panel efficiency by ensuring maximum light intensity consistently hits the solar panel surface.
- Create a single-axis solar tracking system capable of precisely following the sun's movement throughout the day.

## Components Required

| Sl.No | Component’s Name               | Description       | Quantity |
|-------|--------------------------------|-------------------|----------|
| 01    | Arduino Uno Board              | -                 | 01       |
| 02    | Servo Motor                    | SG90              | 01       |
| 03    | Resistors                      | 10KΩ              | 02       |
| 04    | LDR (Light Dependent Resistor) | -                 | 02       |
| 05    | Breadboard                     | -                 | 01       |
| 06    | Connecting Wires               | Jumper wires      | As req.  |

## Introduction

Solar energy is a clean and renewable source of power. To harness solar energy effectively, solar panels need to be aligned with the sun's position to maximize energy conversion. The Sun Tracking Solar Panel System aims to automatically adjust the orientation of solar panels to follow the sun's path, optimizing energy capture. Our project centers on the development of a single-axis solar tracking system, where the entire solar panel seamlessly follows the sun's trajectory from east to west throughout the day.

## Theory

Typically, a solar tracking system adjusts the face of the solar panel or reflective surfaces to follow the movement of the Sun. The movement of solar trackers increases the solar energy output by up to 40% compared to standard panels. Based on their motion, solar trackers can be classified as:
1. Single axis trackers
2. Dual axis trackers

In this project, we built a prototype of a single-axis tracker with a horizontal axis of rotation. This tracker is able to track the daily movement of the sun from morning to evening. We used two LDR sensors to sense the position of the sun based on the difference in light intensity on these LDRs, with an Arduino Uno as the controller, which controls the position of the servo motor with respect to the position of the sun.

## Working of the Project

The Sun Tracking Solar Panel System operates on the principle of dynamic solar panel orientation to maximize exposure to sunlight. Two Light Dependent Resistors (LDRs), LDR1 and LDR2, are strategically placed on the solar panel itself. The system continually monitors the light intensity received by these sensors.

- **LDR Connections and Functions:**
  - Two LDRs are placed on the solar panel assembly, acting as light sensors that detect variations in light intensity caused by the sun's movement.
  - The varying resistance of the LDR due to changing light conditions affects the voltage at the junction of the LDR and a fixed resistor.
  - The analog output of each LDR is connected to analog input pins of the Arduino, which reads the analog values to determine the relative intensity of light.

- **Arduino Connections and Functions:**
  - The Arduino reads the analog values from the LDRs and processes this information to calculate the sun's position relative to the solar panel.
  - Depending on whether one LDR is receiving more light than the other, the system sends a signal to the servo motor, adjusting the solar panel's orientation.

- **Servo Motor Connections and Functions:**
  - The servo motor is connected to the Arduino using digital pins and is controlled via Pulse Width Modulation (PWM) signals.
  - As the Arduino receives data from the LDRs, it calculates the required angle of adjustment based on the sun's position and sends the appropriate PWM signal to the servo motor.

## Circuit Diagram

(Include a circuit diagram here to visually represent the connections and setup.)

## Software Development

The code for the Sun Tracking Solar Panel System is written in C/C++ and uploaded to the Arduino Uno using the Arduino IDE.

```cpp
#include <Servo.h>
#define LDR1 A0
#define LDR2 A1
Servo servo;

void setup() {
  servo.attach(9);
  pinMode(LDR1, INPUT);
  pinMode(LDR2, INPUT);
}

void loop() {
  int ldr1 = analogRead(LDR1);
  int ldr2 = analogRead(LDR2);
  if (ldr1 > ldr2) {
    servo.write(servo.read() + 1);
  } else if (ldr1 < ldr2) {
    servo.write(servo.read() - 1);
  }
  delay(15);
}
```


## Results

The Sun Tracking Solar Panel System successfully tracked the sun's movement throughout the day, optimizing the solar panel's orientation. This led to a significant increase in energy efficiency compared to a fixed solar panel system, demonstrating the effectiveness of the design in enhancing solar energy capture.

## Conclusion

The Sun Tracking Solar Panel System effectively improves solar panel efficiency by using LDR sensors and an Arduino Uno to continuously align the panel with the sun’s path. This project showcases the potential for enhancing renewable energy systems, making solar power a more viable and sustainable option for the future.

## Future Enhancements

To further improve the Solar Tracking System, consider the following enhancements:

- **Dual-Axis Tracking:** Implement a dual-axis tracking system to further increase energy capture by following the sun's path both horizontally and vertically.
- **Remote Monitoring:** Integrate IoT capabilities to enable remote monitoring and control of the solar tracker, allowing users to track performance and make adjustments from anywhere.
- **Weather Adaptation:** Incorporate weather sensors to automatically adjust the tracking behavior in response to cloud cover, rain, or other environmental conditions, optimizing energy capture under varying conditions.
- **Advanced Algorithms:** Utilize solar tracking algorithms that take into account geographical data such as latitude and longitude to improve the accuracy and efficiency of the tracking system.
- **Energy Storage Optimization:** Improve the efficiency of the battery management system to better store and utilize the energy captured by the solar panels.
- **Feedback Control System:** Implement a feedback control system to continuously fine-tune the tracking process, ensuring that the solar panel remains optimally aligned with the sun at all times.


## References

1. [Solar Trackers - Types and Advantages](https://www.solarfeeds.com/mag/solar-trackers-types-and-its-advantages-and-disadvantages/)
2. [Arduino-Based Solar Tracker Using LDR & Servo Motor](https://how2electronics.com/arduino-based-solar-tracker-using-ldr-servo-motor/)
3. [Sun Tracking System Research Paper](https://iopscience.iop.org/article/10.1088/1757-899X/767/1/012052/pdf)
4. [Introduction to Solar Trackers](https://www.linkedin.com/pulse/introduction-solar-trackers-nick-lusson/)
5. [GitHub Repository for Sun Tracking Solar Panel](https://github.com/adityakanu/Sun-Tracking-Solar-Panel)
