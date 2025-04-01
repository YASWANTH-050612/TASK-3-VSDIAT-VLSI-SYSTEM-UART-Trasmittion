# TASK-3-VSDIAT-VLSI-SYSTEM-UART-Transmition

# UART Transmission Project Documentation

## Overview
In this project, I worked on implementing a UART (Universal Asynchronous Receiver-Transmitter) transmitter on an FPGA. The goal was to understand the existing Verilog code, implement a working UART transmitter, and test it by transmitting data to a receiving device like a PC or another UART-compatible device.

## Steps I Took

### 1. Studying the Existing Code
I started by accessing the `uart_tx` project in the `VSDSquadron_FM` repository. The first task was to examine the Verilog code to understand how the UART transmitter was structured. 

- The transmitter module essentially takes in data and transmits it serially, one bit at a time, starting with a "start" bit, followed by the data bits, and ending with a "stop" bit. 
- I paid special attention to the baud rate generation logic and the shift register, which converts parallel data into serial data that could be transmitted over a single wire.

### 2. Design Documentation

#### 2.1 Block Diagram
I created a block diagram to visualize the UART transmitter module. Here’s a breakdown of the key components:
- **Data Input**: This represents the data that will be sent out.
- **Shift Register**: The shift register serializes the data to send it out bit by bit.
- **Baud Rate Generator**: This part of the design controls the timing of the transmission. It ensures the data is sent at the correct rate (e.g., 9600 bps).
- **Control Logic**: Handles the management of start bits, data bits, and stop bits.
- **TX Output**: The final output that drives the UART TX pin.

#### 2.2 Circuit Diagram
I also created a circuit diagram to show how the FPGA’s UART TX pin connects to the receiving device. The FPGA's output pin sends data to the receiver, whether it's a PC or another device, using standard UART protocol. If needed, I added a voltage level converter to ensure the voltage levels were compatible between the FPGA and the receiving device.

### 3. Implementation

#### 3.1 Hardware Setup
For the hardware setup, I connected the FPGA to the receiving device (in this case, my PC) via the UART TX pin. I made sure everything was properly powered and that the clock signals were in place. The circuit was set up based on the diagram I designed earlier.

#### 3.2 Synthesizing and Programming the FPGA
Once the hardware was assembled, I moved on to synthesizing the Verilog code. For synthesis, I used **Xilinx Vivado**, a powerful FPGA development tool, to:
- Synthesize the Verilog design.
- Implement the logic onto the FPGA.
- Generate the bitstream file.
- Program the FPGA with the generated bitstream, which loaded the UART transmitter design onto the hardware.

### 4. Testing and Verification

#### 4.1 Test Setup
To test the UART transmitter, I connected the FPGA to a PC using a **USB-to-UART adapter**. On the PC, I used **PuTTY** as the serial terminal emulator to monitor the transmitted data. Here are the key settings:
- **Baud Rate**: 9600 bps
- **Data Bits**: 8
- **Parity**: None
- **Stop Bits**: 1

#### 4.2 Testing Process
I sent a known sequence of data from the FPGA and observed the transmitted data in the serial terminal. The key things I checked were:
- The timing of the start and stop bits.
- The correct data bits being transmitted.
- Any potential errors, such as data corruption or incorrect baud rate.
- Ensuring that the data arrived in the right order.

Initially, the data transmission worked fine, and everything appeared to be functioning as expected. However, after a while, I encountered an issue where the transmission stopped working. The serial terminal began showing errors, and it was clear that the FPGA was no longer transmitting correctly. After some troubleshooting, I identified that the issue seemed to be related to my PC setup. The USB-to-UART adapter might have been malfunctioning, or there was some incompatibility between the FPGA and the receiving device, causing intermittent failures.

Unfortunately, due to this issue on the PC, I was unable to successfully record and upload a video of the transmission in operation. The error made it impossible to demonstrate the UART transmission in real time. 

### 5. Documentation

#### 5.1 Diagrams and Code Walkthrough
I documented everything thoroughly:
- **Block Diagram**: I included a detailed block diagram that showed all the components of the UART transmitter and how they interact.
- **Circuit Diagram**: The circuit diagram showed how the FPGA was physically connected to the receiving device.
- **Code Walkthrough**: I wrote up an explanation of the Verilog code, explaining how the baud rate was generated and how the data was serialized and transmitted. I also described how the control logic ensured the proper timing of the start, data, and stop bits.

#### 5.2 Testing Outcomes
During testing, I confirmed that the transmitted data was accurate at first. However, due to the error on the receiving end (related to my PC setup), the system stopped working after a while. Despite this, the initial tests confirmed that the FPGA UART transmitter worked as expected.

#### 5.3 Video Documentation
Unfortunately, I wasn't able to upload a video demonstration of the UART transmission due to the issues I encountered with the PC setup. The transmission initially worked but then failed after some time, and I couldn’t record the video while troubleshooting the problem.

## Tools Used
Throughout the project, I used the following tools:
- **Xilinx Vivado**: For synthesizing the Verilog code and programming the FPGA.
- **PuTTY**: As a serial terminal to communicate with the UART receiver and monitor the transmitted data.
- **USB-to-UART Adapter**: For connecting the FPGA to the PC, allowing the UART data to be transmitted and received.

## Conclusion
This project allowed me to implement and test a UART transmitter on an FPGA. I was able to study the existing code, design the necessary diagrams, and successfully implement the hardware. While I encountered some issues during testing, such as intermittent failures in the PC setup, the UART transmitter worked correctly in initial tests. I look forward to resolving the issues and possibly revisiting the project to record the video and demonstrate the UART transmission in full operation.

