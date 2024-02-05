---
title: Lab 2 – Bluetooth
---
# Author: Swapnil Barot (NetID: spb228)
---

[Return to Main Page](https://spbarot.github.io/)

## I. Objective

The purpose of this lab is to learn about the Bluetooth implementation used to connect the computer (off-board computing) and the Artemis board (on-board computing), as well as how to configure and initiate Bluetooth communication. 

---

## II. Materials/Software

1. 1x SparkFun RedBoard Artemis Nano
2. 1x USB A to C Cable
3. Computer
3. Arduino IDE (Software)
4. JupyterLab (Software)

---
## III. Procedure/Design/Results

#### System Setup

As part of the pre-lab setup, we created a virtual environment on our laptops (I'm running Windows 10) and installed the necessary Python libraries. We also changed the UUID and mac addresses at certain positions in the code files as instructed in the instructions to allow our Artemis board to connect to our laptops.

<img src="./../images/Lab1/virtualEnv.png" height="300" alt="image1" class="inline"/>

<img src="./../images/Lab1/ardMacAddr.png" height="300" alt="image1" class="inline"/>
---

#### Task 1 – Send an ECHO Command

The first task involves sending an “ECHO” command with a string value from the computer to the Artemis. The Artemis then receives the command and sends an augmented string back to the computer. As show in the images below, CMD.ECHO is utilized to send a string (HiHello) to the robot (Artemis). The Artemis then sends the string back to the computer (Robot Says -> HiHello (Received From Robot)).   

<img src="../images/Lab1/ard_cmd.png" height="300" alt="hi" class="inline"/> 
<img src="../images/Lab1/ard_echo.png" height="300" alt="image1" class="inline"/>


<img src="../images/Lab1/jup_echo.png" height="300" alt="hi" class="inline"/>




---

#### Task 2 – Send Three Floats

Task 2 involves sending three float values to the Artemis board using the SEND_THREE_FLOATS command. “ble.send_command” is utilized to transmit three float values to the Artemis. The Artemis extracts the values using “robot_cmd.get_next_value”. The images below display the program and the serial output in detail.  

<img src="../images/Lab2/Task2_ino.JPG" width="300" height="300" alt="hi" class="inline"/>

<img src="../images/Lab2/Task2_serial.JPG" width="300" height="10" alt="hi" class="inline"/>

<img src="../images/Lab2/Task2_jupyter.JPG" width="300" height="30" alt="hi" class="inline"/>
  

---

#### Task 3 – Notification Handler
 
A notification handler is setup to receive float values from the Artemis board. In the callback function, a float value is stored as a global variable such that it is updated every time the characteristic value changes. This eliminates the need to utilize the receive_float() function. 

<img src="../images/Lab2/Task3_jupyter.JPG" width="300" height="300" alt="hi" class="inline"/>

---

#### Task 4 – BLEFloat VS BLEString

Receiving a float value in python using receive_float() / BLEFloatCharacteristic enables python to directly receive a float value as a byte array (as transmitted by Artemis). On the other hand, using receive_string() / BLECStringCharacteristic forces python to convert the characters to floats in a byte array. The first option (float) requires 4 bytes (per float) while the second option (string) requires 1 byte (per character). Thus, the float values are more memory expensive, however, can lead to more precision.  It shall be noted that both options produce similar results. 

---

#### ECE 5960 Additional Tasks - Task 1 – Effective Data Rate
This task involves sending a message from the computer to receive a reply from the Artemis, while calculating the times and the data rate of each of the events. To measure the data rate, “performance_measurement” function is utilized, which transmits and receives strings while keeping track of the time. The subsequent for-loop adds to the string in each iteration, increasing the byte size of the package. This information is then captured and computed to capture the data rate (bytes/second), as shown in the images below. 

<img src="../images/Lab2/Task5_jupyter.JPG" width="300" height="300" alt="hi" class="inline"/>

<img src="../images/Lab2/Task5_output.JPG" width="300" height="300" alt="hi" class="inline"/>

<img src="../images/Lab2/Task5_graph.JPG" width="300" height="200" alt="hi" class="inline"/>


---
#### ECE 5960 Additional Tasks - Task 2 – Reliability

The reliability of the data transfer is also tested. To test the reliability of the system, data was sent at a much higher rate from the robot (Artemis) to the computer. This was accomplished by shortening the Arduino interval time to 100 milliseconds (500 milliseconds is typical), and by increasing the baud rate to 1000000 from 115200. As shown in the image below, the output is very similar to the Effective Data Rate task output, signaling that the higher data rate has no significant effect on the reliability. 

<img src="../images/Lab2/Task5_output.JPG" width="300" height="300" alt="hi" class="inline"/>

---

## IV. Conclusion

The goals of this lab were successfully satisfied as the experimenters utilized Bluetooth framework to interconnect the computer and the Artemis board. Knowledge gained in this lab will assist in utilizing Bluetooth in the future labs. The experiment was quite smooth, and the given references/guideline seemed to be very helpful. 

---

## V. Code Appendix

Please refer to respective tasks in Section III - Procedure/Design/Results for the code. 

---

## VI. References

1. [ECE 5960 – Lab 2 Guideline](https://cei-lab.github.io/ECE4960-2022/Lab2.html)
2. [Jupyter Lab Tutorial](https://cei-lab.github.io/ECE4960-2022/tutorials/jupyter_notebooks.html)

---

[Return to Main Page](https://spbarot.github.io/)



