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

### Working  
The circuit is connected as follows:
- Connect 5V Vin of Arduino to breadboard.
- The Vcc of HC-SR04 and servo motor will also be connected to this input on the breadboard.
- Connect the ground of Arduino, HC-SR04, and servomotor to the breadboard.
- The trigger pin of HC-SR04 is connected to pin 13 of Arduino.
- The echo pin is connected to pin 11 of Arduino.
- The PWM signal of the servo motor is connected to PWM pin 6 of Arduino.

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

After connecting the arduino with ultrasonic sensor, HC-SR04, we need to write a code on IDE that will measure the distance using the sensor.  

First you have to define the Trig and Echo pins. In this case they are the pins number 9 and 10 on the Arduino Board and they are named trigPin and echoPin. Then you need a Long variable, named “durations” for the travel time that you will get from the sensor and an integer variable for the distance.  

In the setup you have to define the trigPin as an output and the echoPin as an Input and also start the serial communication for showing the results on the serial monitor.  

In the loop first you have to make sure that the trigPin is clear so you have to set that pin on a LOW State for just 2 µs. Now for generating the Ultra sound wave we have to set the trigPin on HIGH State for 10 µs. Using the pulseIn() function you have to read the travel time and put that value into the variable “duration”. This function has 2 parameters, the first one is the name of the echo pin and for the second one you can write either HIGH or LOW. In this case, HIGH means that the pulsIn() function will wait for the pin to go HIGH caused by the bounced sound wave and it will start timing, then it will wait for the pin to go LOW when the sound wave will end which will stop the timing. At the end the function will return the length of the pulse in microseconds. For getting the distance we will multiply the duration by 0.034 and divide it by 2 At the end we will print the value of the distance on the Serial Monitor.  

### LabVIEW Circuit   
![image](https://github.com/izmanaveed/Range-Finder-Radar-System-Using-Ultrasonic-Sensor/assets/59065717/d4d2a8b2-8e62-4d26-8a84-8b775faf2f7b)  

The correct COM port selection is very necessary as only then it will read the data that arduino sends from EchoPin. Wrong COM port does not display any data on the Front Panel. To ensure the correct COM port is selected, right click on my computer and click on Manage. Go to device manager and check the COM port currently in use. 


