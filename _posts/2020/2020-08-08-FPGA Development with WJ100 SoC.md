---
title: "FPGA Development with wujian100 SoC - Part Ten: Add On-Board Buttons to SoC"
publishDate: 2020-08-08 19:00:06
date: 2020-08-08 19:00:06
categories: FPGA SoC
position: blog
---

Add On-Board Buttons to SoC

---

<div id="toc"></div>

## FPGA Development with wujian100 SoC

### Part Ten: Add On-Board Buttons to SoC

Author: 加一(Jiayi)

## Something to say

Recently I participate a contest named Integrate Circuit Innovation Contest which requires me to use WJ100 developed by Ali Inc. team t-head and a FPGA develop board with Xlinx XC7A200TR3B Core. It's not my first time to cope with FPGA but still, I find it difficult to interpret Verilog Code and make the FPGA works. Luckily, with the help of WJ100 Sdk and CDK(C-sky Develop Kit) which developed by Ali Inc. we could jump the Verilog and long waiting synthesizing part directly to use the pre-setted circuit and easy writing C to develop.

---

## About WJ100

>T-Head's Wujian SoC Platform utilizes the cloud-terminal-integration design philosophy that fuses software and hardware. Full stack integration of chips, operating systems and algorithms enables customers to develop chip products that can be mass-production.
>
>Low power consumption: User-defined power consumption scenarios, with standby power consumption of less than 1uA, and operating power consumption of less than 100uA/MHz

According to the official sites of t-head Inc., WJ100 is a low cost and high power efficiency SoC, which barely means that it could be easily deployed on any chips and consumes lower power.

However, as I talked before, it is a open source project and as I believed, the real function of this SoC is to simplify the use of FPGA and to offer the developer a brand new way to develop: integrate Soc and FPGA to deal with some projects which require both power efficiency and fast steady frequency.

* related websites
[t-head](https://www.t-head.cn/)

### How to use WJ100 SoC

This tutorial is for those who utilize vivado to generate bitstream file and CDK to develop your own projects on *Windows*.

* For Part 1 Bitsream Generation please refer to [Part_1_Bitstream_Generation](https://shieldjy.github.io/post/FPGA-Development-with-WJ100-SoC-P1.html).

* For Part 2 CDK Toolkit and wujian100 SDK please refer to [Part_2_CDK_Toolkit&Wujian100_SDK](https://shieldjy.github.io/post/FPGA-Development-with-WJ100-SoC-P2.html).

* For Part 3 Start a New Project on CDK please refer to [Part_3_Start_a_New_Project_on_CDK](https://shieldjy.github.io/post/FPGA-Development-with-WJ100-SoC-P3.html)

* For Part 4 Hello World please refer to [Part4_Hello_World](https://shieldjy.github.io/post/FPGA-Development-with-WJ100-SoC-P4.html)

* For Part 5 GPIO please refer to [Part5_GPIO](https://shieldjy.github.io/post/FPGA-Development-with-WJ100-SoC-P5.html)

* For Part 6 UART please refer to [Part6_UART](https://shieldjy.github.io/post/FPGA-Development-with-WJ100-SoC-P6.html)

* For Part 7 TIMER please refer to [Part7_TIMER](https://shieldjy.github.io/post/FPGA-Development-with-WJ100-SoC-P7.html)

* For Part 8 Interrupt please refer to [Part8_VIC](https://shieldjy.github.io/post/FPGA-Development-with-WJ100-SoC-P8.html)

* For Part 9 Working on Bugs please refer to [Part9_BUGs](https://shieldjy.github.io/post/FPGA-Development-with-WJ100-SoC.html)

---

### Part 10 Add On-Board Buttons to SoC

According to the official file, there are  four keys that could be defined seperately by the user. And only one of them is pre-defined in SoC(K3 which is PB4 in wujian100). The table is shown in *table 1*.

*table 1 user defined key signal connection with FPGA*
User defined key|Signal Name|FPGA U1|Name in Soc
K3|KEY1|U1.AB7|PB4_XX_XX_XX_UART3TX
K4|KEY2|U1.Y8|
K5|KEY3|U1.AB6|
K6|KEY4|U1.V8|

As shown above, I have searched in `wujian100_open` project for specific word and have found in `XC7A200T3B.xdc` file which defines the pins of FPGA and what it reflects inner the SoC. Then I found definitions related to user keys are commented by the officials shown as code below.

```v
    #===========================================
    # USER KEYs:
    #===========================================
    #set_property PACKAGE_PIN AB7   [get_ports ];	#k3
    #set_property PACKAGE_PIN Y8    [get_ports {gpio0_port[2]}];	#k4
    #set_property PACKAGE_PIN AB6   [get_ports {gpio0_port[3]}];	#k5
    #set_property PACKAGE_PIN V8    [get_ports {gpio0_port[4]}];	#k6
```

As we could see, the Port on FPGA is not mapped correctly to where we expect it would be. Hence, I changed the mapping ralation and got the codes below.

```v
    #===========================================
    # USER KEYs:
    #===========================================
    #set_property PACKAGE_PIN AB7   [get_ports ];	#k3
    set_property PACKAGE_PIN Y8    [get_ports PAD_GPIO_29];	#k4
    set_property PACKAGE_PIN AB6   [get_ports PAD_GPIO_30];	#k5
    set_property PACKAGE_PIN V8    [get_ports PAD_GPIO_31];	#k6
```

After changing the mapping relationship of GPIO in SoC, there might be conflict between newly established pin and already existed ones. So, we need to comment those codes below to prevent errors.

```v
    #===========================================
    # YOC SOCKET 2
    #===========================================
    #set_property PACKAGE_PIN U20     [get_ports PAD_GPIO_29]
    #set_property PACKAGE_PIN AB20    [get_ports PAD_GPIO_30]
    #set_property PACKAGE_PIN T20     [get_ports PAD_GPIO_31]
```

Then follow the steps in [Part_1_Bitstream_Generation](https://shieldjy.github.io/post/FPGA-Development-with-WJ100-SoC-P1.html) to generate a bitstream file and test if it works in wujian100.
