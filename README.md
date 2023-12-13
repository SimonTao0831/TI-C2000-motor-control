# TI C2000 Launchpad with Simulink
## Introduction
This project aims to explore Model Based Design (MBD) to accelerate the project development speed. 
TI C2000 Launchpad was used with Simulink to control DC motors.
Some simple experiments were conducted.

Demo:

![Sinusoidal position signal following](/doc/demo_video.gif)

Click following picture to watch video:

[![Link to my YouTube video!](/doc/video_picture.png)](https://www.youtube.com/watch?v=X1G_Mc1O-xw)

## Preparation
Hardware platform: 
[LAUNCHXL-F28027](https://www.ti.com/tool/LAUNCHXL-F28027)

Software:
Matlab (2017a and above versions)

Required Matlab packages:
1. Simulink
2. Embedded Coder
3. MATLAB Coder
4. Simulink Coder
5. Embedded Coder Support Package for Texas Instruments C2000 Processors
- Select Processor Family: TI Piccolo F2802x (based on your hardware)
- Install Third-Party Software
- Install Third-Party Software

## Hardware

### Hardware Setup

![Hardware Setup](/doc/Picture3.png)

LAUNCHXL-F28027 image source: https://www.ti.com/lit/ml/sprz376/sprz376.pdf?ts=1702445097824&ref_url=https%253A%252F%252Fwww.ti.com%252Ftool%252FLAUNCHXL-F28027
TB6612 image source: https://www.sparkfun.com/products/14451

### Experimental platform

<img src="/doc/Picture1.png" width="400">

- Battery: 12V, power the motor
- DC motor with encoder
- Control board: LAUNCHXL-F28027 + TB6612 module + Breakout board

The breakout board was designed by Altium Designer, all design files are in Lpad_28027_connect_Project _v1.1 folder.

## Simulink

### DC motor PID speed control

![Simulink](/doc/Picture2.png)

- Desired Velocity (rpm)
- Actual Velocity:
The eCAP module outputs pulse interval time. Divide the distance by the time to get the actual velocity.
- PID controller:
Incremental PID module.
- PWM module:
Change the power voltage of the DC motor.
- Direction

GPIO0 and CPIO1 are used to control the rotation direction.

The related code 'dc_motor_pid_control' is in the main directory.

### Results

Suitable PID parameters:

<img src="/doc/Result1.png" width="400">

D parameter turns higher:

<img src="/doc/Result2.png" width="400">

I parameter turns lower:

<img src="/doc/Result3.png" width="400">

P parameter turns Higher:

<img src="/doc/Result4.png" width="400">
