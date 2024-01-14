# Range-Finder-Radar-System-Using-Ultrasonic-Sensor  
Two methods are used to illustrate the working of this project, i.e., using the ultrasonic sensor HC-SR04 interfaced with LabVIEW or implementing the project with a purely programming-based technique using the Processing Development Environment (PDE). Both methods help the observer and reader develop a better understanding of the workings of the HC-SR04 sensor and its applications.  

## PROBLEM STATEMENT  
To implement a range-finding device using Arduino Uno as well as show simulations of a range finder on LabVIEW.  

## PROJECT OBJECTIVES  
- Implement a working model of a range finder using an ultrasonic sensor (hardware part)
- Interface Arduino with LabVIEW so that it displays distance measurement (software part)

## Hardware Implementation  

### Components  
- Ultrasonic sensor HC-SR04
- Arduino Uno
- Servo motor
- Breadboard and jumper wires
- Processing development Environment (PDE)
- Arduino IDE

### Circuit Diagram   
![image](https://github.com/izmanaveed/Range-Finder-Radar-System-Using-Ultrasonic-Sensor/assets/59065717/295f5783-0b0e-4e72-afb3-82fa1adea67a)  

### Connections  
The circuit is connected as follows:
- Connect 5V Vin of Arduino to breadboard.
- The Vcc of HC-SR04 and servo motor will also be connected to this input on the breadboard.
- Connect the ground of Arduino, HC-SR04, and servomotor to the breadboard.
- The trigger pin of HC-SR04 is connected to pin 13 of Arduino.
- The echo pin is connected to pin 11 of Arduino.
- The PWM signal of the servo motor is connected to PWM pin 6 of Arduino.

### Working 
#### Ultrasonic Sensor
Ultrasonic Sensor emits an ultrasound at 40 000 Hz which travels through the air and if there is an object or obstacle in its path It will bounce back to the module. Considering the travel time and the speed of the sound you can calculate the distance.  
The HC-SR04 Ultrasonic Module has 4 pins, Ground, VCC, Trig, and Echo. The Ground and the VCC pins of the module need to be connected to the Ground and the 5-volt pins on the Arduino Board respectively and the trig and echo pins to any Digital I/O pin on the Arduino Board. To generate the ultrasound, you need to set the Trig on a High State for 10 µs. That will send out an 8-cycle sonic burst which will travel at the speed of sound and it will be received in the Echo pin. The Echo pin will output the time in microseconds the sound wave traveled. For example, if the object is 10 cm away from the sensor, and the speed of the sound is 340 m/s or 0.034 cm/µs the sound wave will need to travel about 294 u seconds. But what you will get from the Echo pin will be double that number because the sound wave needs to travel forward and bounce backward.  So to get the distance in cm we need to multiply the received travel time value from the echo pin by 0.034 and divide it by 2.  

#### Servo Motor
Servos are controlled by sending an electrical pulse of variable width, or pulse width modulation (PWM), through the control wire. There is a minimum pulse, a maximum pulse, and a repetition rate. A servo motor can usually only turn 90° in either direction for a total of 180° movement. The motor's neutral position is defined as the position where the servo has the same amount of potential rotation in both the clockwise or counter-clockwise direction. The PWM sent to the motor determines the position of the shaft, and based on the duration of the pulse sent via the control wire; the rotor will turn to the desired position. The servo motor expects to see a pulse every 20 milliseconds (ms) and the length of the pulse will determine how far the motor turns. For example, a 1.5ms pulse will make the motor turn to the 90° position. Shorter than 1.5ms moves it in the counterclockwise direction toward the 0° position, and any longer than 1.5ms will turn the servo in a clockwise direction toward the 180° position.  
When these servos are commanded to move, they will move to the position and hold that position. If an external force pushes against the servo while the servo is holding a position, the servo will resist from moving out of that position. The maximum amount of force the servo can exert is called the torque rating of the servo. Servos will not hold their position forever though; the position pulse must be repeated to instruct the servo to stay in position.

### Result  
![image](https://github.com/izmanaveed/Range-Finder-Radar-System-Using-Ultrasonic-Sensor/assets/59065717/220e261f-82d7-4662-9de1-94090de329b5)  

## Software Implementation  

### Hardware/Software Used:  
- LabVIEW
- NI-VISA
- VIPM (VI Package Manager)
- Linx [LABView MakerHub]
- Arduino IDE
- Arduino Uno
- HC-SR04

### Circuit Diagram  
![image](https://github.com/izmanaveed/Range-Finder-Radar-System-Using-Ultrasonic-Sensor/assets/59065717/775b908c-248b-4149-bbf8-bda8efd48173)  

After connecting the Arduino with the ultrasonic sensor, HC-SR04, we need to write a code on IDE that will measure the distance using the sensor.  

First, you have to define the Trig and Echo pins. In this case, they are the pins number 9 and 10 on the Arduino Board and they are named trigPin and echoPin. Then you need a Long variable, named “durations” for the travel time that you will get from the sensor and an integer variable for the distance.  

In the setup, you have to define the trigPin as an output and the echoPin as an Input and also start the serial communication to show the results on the serial monitor.  

In the loop first, you have to make sure that the trigPin is clear so you have to set that pin on a LOW State for just 2 µs. Now for generating the Ultrasound wave, we have to set the trigPin on HIGH State for 10 µs. Using the pulseIn() function you have to read the travel time and put that value into the variable “duration”. This function has 2 parameters, the first one is the name of the echo pin and for the second one, you can write either HIGH or LOW. In this case, HIGH means that the pulsIn() function will wait for the pin to go HIGH caused by the bounced sound wave and it will start timing, then it will wait for the pin to go LOW when the sound wave will end which will stop the timing. At the end, the function will return the length of the pulse in microseconds. To get the distance we will multiply the duration by 0.034 and divide it by 2 At the end we will print the value of the distance on the Serial Monitor.  

### LabVIEW Circuit  
We start the VI by placing an ‘open serial’ linx block. It is followed by an Ultrasonic read block and finally, ends with a close block.
As we change the distance of the object from the ultrasonic sensor, the Arduino reads that distance and sends it to Labview, and then displays the output on the front panel of Labview.
The while loop is used so that the sensor can give readings continuously as the loop runs instead of having to re-run the VI each time.  

![image](https://github.com/izmanaveed/Range-Finder-Radar-System-Using-Ultrasonic-Sensor/assets/59065717/d4d2a8b2-8e62-4d26-8a84-8b775faf2f7b)  

The correct COM port selection is very necessary as only then it will read the data that Arduino sends from EchoPin. The wrong COM port does not display any data on the Front Panel. To ensure the correct COM port is selected, right-click on my computer and click on Manage. Go to the device manager and check the COM port currently in use. 

### Working  
The hardware is setup as:  
- Connect trigger pin of HC-SR04 with pin 9.
- Connect Echo pin of HC-SR04 with pin 10.
- Connect Vcc of HC-SR04 with 5V of Arduino.
- Connect Ground of HC-SR04 with ground of Arduino.

The software setup is as follows:
- Create a control on serial port of open block of LINX.
- Create a control on trigger pin of sensor block.
- Create a control on echo pin of sensor block.
- Create a control on distance (cm and inches) pin of sensor block.
- Connect all LINX resource pins.
- Connect all error out and error in pins.
- Make a while loop around the central sensor block.
- Create a control for stopping the while loop.

### Interfacing Arduino with LabVIEW  
To interface Arduino with LabVIEW, first download NI-VISA. This software allows LABView communication with Arduino without it, LABView does not detect Arduino COM port. Next, HC-SR04 LIFA_BASE needs to be downloaded. The Arduino code will be uploaded in this base which will allow communication with LabVIEW.

### Result   
![image](https://github.com/izmanaveed/Range-Finder-Radar-System-Using-Ultrasonic-Sensor/assets/59065717/2633e550-841e-401c-8f10-de2aae8a3837)  

### Problems Faced  
Some problems faced during this project are as follows:  
- Before downloading NI-VISA, LabVIEW was unable to detect the COM port.
- Incorrect COM port did not give us any readings on the front panel.
- Arduino was not getting properly interfaced with LabVIEW, although it would give output on the serial monitor.
- The ‘Open’ block of LINX presented many errors. Error 5006 was the most common. It occurs due to unknown reasons. Error 5003 was also displayed sometimes. This is because LabVIEW does not recognize the COM port or the wrong COM port has been used in initializing sub-vi of the Open block.
- To eradicate these errors, the sub-vis and sub-sub-vis had to be removed. Even after that, readings were not displayed on the front panel.
- Arduino IDE sometimes presented an uploading error.
