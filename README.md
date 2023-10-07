# 16 byte CMOS SRAM

- Designed a 16-byte SRAM (Static Random Access Memory) using the 180nm technology node.
- This SRAM design allows for reading or writing 8-bit data at a time.
- Throughout the project, various Cadence tools were employed to aid in the design and verification processes.

## Table of Contents

- [Introduction](#Introduction)
- [Architecture](#architecture)
  - [Components](#components)
    - [Component 1](#component-1)
    - [Component 2](#component-2)
    - [Component 3](#component-3)
  - [Images](#images)
- [Usage](#usage)
- [Installation](#installation)
- [Contributing](#contributing)
- [License](#license)

## Introduction

### SRAM :
Static Random Access Memory, commonly known as SRAM, is a fundamental type of semiconductor memory used extensively in modern digital electronic systems. Unlike dynamic RAM (DRAM), which requires periodic refreshing, SRAM is static in nature, meaning it holds data as long as power is supplied.

Applications of SRAM include serving as cache memory in microprocessors, providing high-speed storage for critical data and instructions, and acting as the primary memory in various embedded systems where fast and reliable access to data is essential. SRAM is favored for its fast read and write access times, making it a crucial component in optimizing the performance of various electronic devices.



## Architecture
<figure>
<figcaption>Figure 1: Architecture of 16 byte SRAM</figcaption>
<img src="./images/architecture%20sram%20project_page-0001.jpg" alt="Architecture_SRAM" title="Figure 1" height="650" width="3000">
</figure>


## Components

In this section, Various components of projects are explained and realted equations, simulation results are mentioned.

### 6T SRAM
<figure>
<figcaption>Figure 2: 6T SRAM</figcaption>
<img src="./images/6T%20sram_page-0001.jpg" alt="6T SRAM" title="Figure 2" height="500" width="700">
</figure>

- The above fingure i.e figure 2 shows the classic structure of a 6T sram which can store one bit data.
- These are basically two back to back inverter with access transistor i.e M3 and M5.
- Since there are two back to back inverter structure is there till the time the vdd and ground supply is there for inverter the data will not change.
#### Operation :
- There are basically 3 modes of opeartion,
     - read operation
     - write operation
     - hold operation
- In read and write operation WL (Word line) = 1 and in hold operation WL = 0
- Word line will be controlled by a signal called control and decoder output that will be discussed later.
- read write operation will be controlled by  signal rwn and  control as shown in figure 1 i.e SRAM architecture.
##### read operation :
- in read operation first the bit line (BL) and bit line bar (BLB) node will be charged to vdd.
- Then the WL = 1, in figure 2 suppose node S2 is at vdd and S1 is at zero i.e we can say that we have stored a one in sram cell when we will make WL = 1 then
  BLB node is at vdd and s1 node is at vdd then there will be no change there where as in the other side BL node is at vdd and s2 is at 0 and M1 is also ON
  hence BL node will try to discharge through that path of M3 and M1.In this way BLB node is stable and BL node is going down which is a indication that we are
  reading zero similarly while reading one BL node will be stable at logic 1 where as BLB node will be dischagred gradually.
- Now BL node will be discharged and it will charge S2 node and if S2 node will be charged to same or more than threshold voltage then the NMOS on the other side 
  i.e M2 will be ON it may toggle the data stored even if it will not toggle there will be a unneccesary current flow since NMOS is on and thats a power loss.
- Thats why we try to keep the node S2 voltage around 0.3 i.e less than the threashold now how can we do that for that we have modify the sizing of two NMOS i.e
  M1 and M3 and because SRAM is a symmetric structure M2 and M4 will also have the same size.

<figure>
<img src="./images/6T%20sram_page-0001.jpg" alt="SRAM transistor sizing calculation" title="Figure 3" height="500" width="700">
</figure>





#### Component 3

Explain the third component and its role within the project.

### Images

Include images to help visualize your project's architecture. Two images will be displayed side by side, and one image will be displayed separately.

#### Image 1

![Image 1 Description](image1.jpg)

#### Image 2

![Image 2 Description](image2.jpg)

#### Image 3

![Image 3 Description](image3.jpg)

## Usage

Provide instructions on how to use your project or any relevant code snippets.

## Installation

Explain how to install your project, including any dependencies and setup instructions.

## Contributing

Provide guidelines for contributing to your project, including how to report issues or submit pull requests.

## License

Specify the license under which your project is distributed. For example:

This project is licensed under the [MIT License](LICENSE).

