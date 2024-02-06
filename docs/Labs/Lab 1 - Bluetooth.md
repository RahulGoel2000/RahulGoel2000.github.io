---
title: Lab 2 – Bluetooth
---
# Author: Rahul Goel (NetID: rg764)
---

[Return to Main Page](https://rahulgoel2000.github.io/)

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

<img src="./../images/Lab1/virtualEnv.png" width="100%" alt="image1" class="inline"/>
---

#### ECHO Command

The first task involves sending an “ECHO” command with a string value from the computer to the Artemis. The Artemis then receives the command and sends an augmented string back to the computer. As show in the images below, CMD.ECHO is utilized to send a string (HiHello) to the robot (Artemis). The Artemis then sends the string back to the computer (Robot Says -> HiHello (Received From Robot)).   

<img src="../images/Lab1/ard_cmd.png" width="100%" alt="hi" class="inline"/> 

<img src="../images/Lab1/ard_echo.png" width="100%" alt="image1" class="inline"/>

<img src="../images/Lab1/jup_echo.png" width="100%" alt="hi" class="inline"/>


---

#### GET_TIME_MILLIS Command

The command requested the current time from the Artemis board. This required using the Arduino package's millis() method, converting and storing the result as a double, and passing it as a string to Python.   

<img src="../images/Lab1/Getmil_ard.png" width="100%" alt="hi" class="inline"/>

** time_measure is a variable with double as datatype. Created to automatically typecast millis(), which outputs a long long.

<img src="../images/Lab1/Getmil_jup.png" width="100%" alt="hi" class="inline"/>



---

#### Notification Handler
 
To be able to collect data without having to explicitly call it, a Python notification handler was created to automatically receive the data. 

<img src="../images/Lab1/notification.png" width="100%" alt="hi" class="inline"/>

---

#### Gets the current time in millisecond for few seconds

On the arduino side created a loop which kept sending the timestamp using millis for continuous five seconds. recrded the data on the python end and tried to calculate the effective data transfer rate. In these case there was some gap between continuos messages being send because of the time consumed each time by the millis() function.

<img src="../images/Lab1/get_millis_5s_ard.png" width="100%" alt="hi" class="inline"/>
<img src="../images/Lab1/get_millis_5s_jup.png" width="100%" alt="hi" class="inline"/>
<img src="../images/Lab1/get_millis_5s_2.png" width="100%" alt="hi" class="inline"/>

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

[Return to Main Page](https://rahulgoel2000.github.io/)



