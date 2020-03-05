# Simulation of Quadcopter

Today the PID concept is used universally in applications requiring accurate and optimized automatic control. 
This project aims to design a 3D simulation to illustrate the behavior of various control loop mechanisms 
(proportional (P) or/and integral (I) or/and derivative (D) controller) with freely selectable parameters. 
The simulation also allows the user to control a virtual quadcopter with a wireless IMU (inertial measurement unit) 
as a joystick and to move the quadcopter to a desired reference. The simulation should also allow the user to test 
the performance of the desired controller (e.g. PID) for the virtual quadcopter.

For the visualization of the simulation, a 3D animation is created in JavaScript using the library Babylon. js. 
The whole thing is placed on the browser - HTML5 is used for this. Besides, a controller and a line dynamic is also 
used for the automated movement of the quadcopter. This is realized in Matlab/Simulink. From Matlab, the manipulated 
variable and the output of the line dynamics are transferred to JavaScript. Also, the user should be able to enter data 
(such as B. the reference, parameters of the PID controller, etc. ) on the user interface, which is then fed back to 
MatLab/Simulink. The corresponding block diagram of the project is shown in Figure 1. 

![Block diagram of project](master/Blockschaltbild.png)

The interface between Matlab and HTML is realized with the WebSocket protocol because it has the property to maintain 
an open connection while the user actively uses this open connection without asking the server for the answer. 
This guarantees a real-time simulation. Since, as mentioned above, you also want to drive the quadcopter yourself in the 
simulation, an inertial measurement unit (IMU) is used. The Xsens MTw Awinda sensor is used as IMU, which sends the acquired 
data to a receiver via Bluetooth, whereby the receiver (dongle) is connected to the PC. The data arrives in Matlab as a 
quaternion vector and is stored therein parameters necessary for us (e. g. B. Inclination forward/backward and left/right).
