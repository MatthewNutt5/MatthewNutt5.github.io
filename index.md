---
layout: default
---

# About

Welcome to my website! I am a 4th-year undergraduate at Rice University, pursuing a Bachelor's and a Master's in Electrical & Computer Engineering. My interests primarily lie in digital silicon, including VLSI, ASICs, and FPGAs, but I am generally invested in hardware design.

Outside of classes, I like to play and compose music, learn new cooking recipes, and do some weightlifting.

# Projects

## Snake Game ASIC (May 2025)

![VLSI Core](./assets/img/integrated_core.png)

This project is an ASIC that plays a basic version of the snake game, featuring an 8x8 multiplexed display grid, randomly generated apple positions, and dual-phase clocking. The system was implemented in Verilog, verified with testbenches on each module, synthesized, placed/routed, and finally connected to a padframe to prepare for tapeout.<br>[View Report PDF](./assets/pdf/snake_asic_report.pdf){:target="_blank"}

## 32-bit Carry-Bypass Adder (April 2025)

![4-bit Adder Stage](./assets/img/schematic.png)

This is a schematic-level design of a 32-bit carry-bypass adder for the Skywater 130nm PDK, with eight bypass units and transistor/gate sizing optimization for each unit. Thanks to these optimizations, we achieved a critical path delay of 640ps with 133 uW average power consumption.<br>[View Report PDF](./assets/pdf/32-bit_adder_report.pdf){:target="_blank"}
