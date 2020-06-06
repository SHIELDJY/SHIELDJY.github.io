---
layout: project
title: Projects
permalink: /projects/
---

## Competitions

### National College Smart Car Competition

*15 Oct, 2017 - 25 Jul, 2018*

*8 Jun, 2019 - 25 Jul, 2020*

#### Brief: 

Two self-controlled DIY cars with 5 electromagnetic sensors and one 8-bit CMOS camera running on a closed track with a 100 mA in 20Hz AC current  under the lane is accomplished. Besides, the cars are required to finish 3 times of meeting on the 50 cm wide track.

#### Description:

(The two cars are basically identical except for some tiny errors caused by hand-made process.  Hence unless otherwise specified, the following descriptions are for both cars)

1. The car with 4 wheels is DC motor driven and powered by a set of 18650 battery. Direction control relies on the modeled steering gear, which has 6V driven voltage and is controlled by pulse width modulation wave(PWM). 

2. The basic dimension of the car is $27cm \times 16.4cm \times 13.8cm$ .

   ![project_img_1](https://s1.ax1x.com/2020/06/03/tUwWAP.md.jpg)

   *Figure1 the "Smart Car" which is everything but smart*

3. A NXP® K60™ Series MCU MK60FX512VLQ10 is used as main control unit. ARM® KEIL™ $\mu Vision5$ is used to program the MCU and debug the program.

4. Four separated two-layer printed copper board (PCB)  is designed. One of the PCBs is used to stabilize, to rise or decrease voltage level and to supply power to each part of the cars. One another is used to magnify the signal received by the sensor, and one is used to connect both 5 sensors to magnifying part. The other PCB is used to drive the 2 DC Motors. Each PCB is connected by DuPont line and  cable lines to conduct signals. And 5mm copper lines are used to conduct current.

   ![project_img_2](https://s1.ax1x.com/2020/06/03/tUwftf.jpg)

   *Figure2 One of the Four PCBs (with Altium Designer)*

   ![project_img_3](assets/img/Projects/project_img_3.jpg)

   *Figure3 Another of the Four PCBs (with Altium Designer)*

5. Software in the MCU is self-written and has reached the goal it requires, i.e. self-running  on the closed track and accomplished 3 times of meetings which could been found in Repo [Project_Sonic](https://github.com/SHIELDJY/Project_Sonic).

#### Honor

* 3rd Place (East China) in 2018
* 2nd Place (East China) in 2019



### National Integrated Circuit Innovation and Entrepreneurship Competition

### NI Cup

*3 Apr, 2019 - 20 Aug, 2019*

#### Brief

A  Integrated circuit amplifier based on Bipolar Junction Transistor (BJT) is designed with NI® Multisim™ 14. Several technical index are satisfied, i.e. Input offset voltage, offset current, input bias current$I_b$, common mode rejection ratio (CMRR), power supply rejection ratio (PSRR), open-loop voltage gain $G_{ov}$, open-loop bandwidth $f_{Bw}$ output voltage amplitude $V_{opp}$ and slew rate(SR).

#### Honor

* 2nd Place (East China) on Jul, 2019
* Honor of Excellence (National) on Aug, 2019

---

## Government Funded Project

### Mapping Robot Based on Visual SLAM

*12 Apr, 2018 - 20 Apr, 2019*

*Funded by Ministry of Education of PRC*

#### Brief

A Visual Simutaneous Localization and Mapping (v-SLAM) Robot, Jixiaohei（济小黑）(Figure 4)is designed and built to guide the Blinds who have trouble to see what is going on in the surroundings, since in China the construction of barrier-free facilities is generally lagging behind the other countries and there are few ways to make those have problem to see to walk around without professional assistants.

#### Description

A Lidar-based SLAM robot is built formerly by  fellow students, called Jixiaobai (济小白)(Figure 5), to provide a moblie  beverage stand. However, a binocular visual based SLAM robot is built with a $Intel NUC_{TM}$ as processing unit, STM32F108C3T6 in $STMicro$ STM32 Family as controlling unit, two DC Motors as powering and steering unit, a Binocular camera used as visual sensor. The goal of simutaneously localization and mapping is accomplished, however, due to the irreversive PCB damage and the end of funding period, the demo is limited with a few clips of the process.

![project_img_5](https://s1.ax1x.com/2020/06/03/tUw59S.jpg)
*Figure 4 Jixiaohei(Visual based SLAM Robot)*

#### Demos

Shown as in Figure 5, a Lidar based SLAM Robot could achieve its simutaneous localization and could accomplish its human detection to prevent some unpredictable dangers.

![project_img_7](https://s1.ax1x.com/2020/06/03/tUwI1g.gif)
*Figure 5 Demo for Jixiaobai(Lidar-based SLAM Robot by fellow students)*

Shown as in Figure 6, the visual based SLAM Robot could achieve its localization and could automatically map the surroundings in a prettty precise way. The whole software is running on a docker file so that backup and back-going process could be achieved easily.
![project_img_6](https://s1.ax1x.com/2020/06/03/tUwocQ.gif)
*Figure 6 Demo for Jixiaohei(Visual based SLAM Robot)*

 However, due to the end of funding period, our project has been stopped to achieving seperately, i.e. we have not yet make the robot move by it self since we choosed a wrong version of NUC with AMD Graphic Card and must use a Thunderbot 3 lightening interface to plug a NIVIDA Graphic Card to run demos on which consumes far more power than we have been thought so fomerly designed low-voltage and current power suppy system could not cooperate with the modified system. Besides, the tiny little robot could hardly afford such heavy two machines, /sad.

 Code has been made public in [VSlamDemo](https://github.com/DmitriZhao/ROS-Navigation-Demo) and now one of our fellow students, [DmitriZhao](https://github.com/DmitriZhao), is still working on this demo in order to run a virtual visual based SLAM for other projects.

 ---

## Coursework

### A Sample Crossing with Traffic Tight(in 1:250 Scale)

#### Brief
