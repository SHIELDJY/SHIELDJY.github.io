---
layout: project
title: Projects
permalink: /projects/
---

## Competitions

### National College Smart Car Competition

*15 Oct, 2017 - 25 Jul, 2018*

*8 Jun, 2019 - 25 Jul, 2020*

* Brief: 

  Two self-controlled DIY cars with 5 electromagnetic sensors and one 8-bit CMOS camera running on a closed track with a 100 mA in 20Hz AC current  under the lane is accomplished. Besides, the cars are required to finish 3 times of meeting on the 50 cm wide track.

* Description:

  (The two cars are basically identical except for some tiny errors caused by hand-made process.  Hence unless otherwise specified, the following descriptions are for both cars)

  1. The car with 4 wheels is DC motor driven and powered by a set of 18650 battery. Direction control relies on the modeled steering gear, which has 6V driven voltage and is controlled by pulse width modulation wave(PWM). 

  2. The basic dimension of the car is $27cm\times16.4cm\times13.8cm$.

     <img src="E:\Documents\GitHub\walterlv.github.io\assets\img\Projects\project_img_1.jpg" alt="project_img_1" style="zoom:50%;" />

     *Figure1 Pic for the Smart Car*

  3. A NXP® K60™ Series MCU MK60FX512VLQ10 is used as main control unit. ARM® KEIL™ $\mu Vision5$ is used to program the MCU and debug the program.

  4. Four separated two-layer printed copper board (PCB)  is designed. One of the PCBs is used to stabilize, to rise or decrease voltage level and to supply power to each part of the cars. One another is used to magnify the signal received by the sensor, and one is used to connect both 5 sensors to magnifying part. The other PCB is used to drive the 2 DC Motors. Each PCB is connected by DuPont line and  cable lines to conduct signals. And 5mm copper lines are used to conduct current.

     ![project_img_2](E:\Documents\GitHub\walterlv.github.io\assets\img\Projects\project_img_2.jpg)

     *FIgure2 Pic for One of the Four PCBs (with Altium Designer)*

     ![project_img_3](E:\Documents\GitHub\walterlv.github.io\assets\img\Projects\project_img_3.jpg)

     *Figure3 Pic for Another of the Four PCBs (with Altium Designer)*

  5. Software in the MCU is self-written and has reached the goal it requires, i.e. self-running  on the closed track and accomplished 3 times of meetings which could been found in Repo [Project_Sonic](https://github.com/SHIELDJY/Project_Sonic).

* Honor
  * 3rd Place (East China) in 2018
  * 2nd Place (East China) in 2019



### National Integrated Circuit Innovation and Entrepreneurship Competition - NI Cup

*3 Apr, 2019 - 20 Aug, 2019*

- Brief
- Description

---

## Government Funded Project

### Mapping Robot Based on Visual SLAM

*12 Apr, 2018 - 20 Apr, 2019*

*Funded by Ministry of Education of PRC*





