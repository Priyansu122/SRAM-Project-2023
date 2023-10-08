# 16 byte CMOS SRAM

- Designed a 16-byte SRAM (Static Random Access Memory) using the 180nm technology node.
- This SRAM design allows for reading or writing 8-bit data at a time.
- Throughout the project, various Cadence tools were employed to aid in the design and verification processes.

## Table of Contents

- [Introduction](#introduction)
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

## Introduction {#introduction}

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

##### write operation :
- In write operation, first we will precharge both the nodes to vdd .
- As we have discussed earlier we know that node s2 have 0 in it and s1 have 1 now we want to say write 1 to node s2.
- After precharge the write driver will be connected to the BL and BLB line as we want to write 1 in the s2 node data 1 i.e vdd will be connected to BL line as it is already precharged
  to vdd so there will no change in voltage for the BL line but the BLB line will be connected to data bar i.e 0 in this case so BLB line will be dischjarged to zero.
- Then WL=1, so that the data in BL and BLB line can be stored in the internal node of the sram i.e s2 and s1 in this case.
  
<figure>
<img src="./images/6T%20sram_page-0001.jpg" alt="SRAM transistor sizing calculation" title="Figure 3" height="500" width="700">
</figure>

- As shown above from equations we have estimated the sizes of noms and pmos in 6T sram.
- Using that size we have build testbenchs in **cadence virtuso schematic editor tool**.

**read simulation result**
<div style="display: flex; justify-content: space-between;">
  <img src="image1.jpg" alt="Image 1" width="48%">
  <img src="image2.jpg" alt="Image 2" width="48%">
</div>
- From the graph we can see that the Vbl = 1.8 that is the vdd the node volatge of sram is around 0.3 V which indicates that during read operation it cannot exceed the volatge 0.3V.

**Write simulation result**
<div style="display: flex; justify-content: space-between;">
  <img src="image1.jpg" alt="Image 1" width="48%">
  <img src="image2.jpg" alt="Image 2" width="48%">
</div>
- In the simulation word line is always ON.
- Here we have considered that the node s2 has 1 i.e the node voltage is vdd.
- At this time M3 and M5 is activated and from the other side M2 and M4 is activated.
- When the BL is at vdd the node s2 is also at vdd but when BL is discharged to 0 the s2 node voltage also discharges.
- When BL node is completely discharged to 0 at that time the s2 node voltage` is at around 100mv or 0.1V.
- From this information we can conclude that 0 has been written in the node s2.






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

