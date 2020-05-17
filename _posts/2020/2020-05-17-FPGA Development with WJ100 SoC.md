---
title: "FPGA Development with wujian100 SoC - Part Nine: Working on Bugs"
publishDate: 2020-05-17 09:19:06 +0800
date: 2020-05-17 15:44:25 +0800
categories: FPGA SoC
position: blog
---

Bug issue.

---

<div id="toc"></div>

## FPGA Development with wujian100 SoC

### Part Nine: Working on Bugs

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

---

### Part 9 Bugs Issue

#### 001 return problem

category | compiler bug
solved | NO
confirmed | YES
Discription | As shown in code block, delay_flag will become 0 when interrupt is triggered. However, after I tested several times, whatever the judgment condition is, i.e. `delay_flag <= 0` or `delay_flag != 1`, the function just seems to stuck with `while`. And further experiments conducted by adding a `printf` function in the `if` statement shows that the judgement would work so that the only bug is about `return` statement. More informantion is digged when I see what is wrong with the assemble language and I found there is no `jmp` to return to the function where it originally is but a `jmp` statement to return to something implements the infinite `while` loop. Further experiments showns that this problem occurs when there are more than 3 times of loop in `while` and then it will enter some infinite loop.

```c
    while(1){
        if (delay_flag == 0) {
            return 0;
        }
    }
```

*Feel free to comment for your opinions or bugs you have found, I will continuously update this bug issue article.*
