# Course_Material
This repository contains the group projects completed during my Degree(Diploma and BTech) in picture and pdf format. The Readme file is about "The Automatic Staiecase Light" project using Arduino.

int IRSensor = 2; 

void setup() 
{
  pinMode (IRSensor, INPUT); 
  pinMode (6, OUTPUT); 
  pinMode (7, OUTPUT);
  pinMode (8, OUTPUT);
  pinMode (9, OUTPUT);
  pinMode (10, OUTPUT);
  pinMode (11, OUTPUT);
  pinMode (12, OUTPUT);
}

void loop()
{
  int statusSensor = digitalRead (IRSensor);
  
  if (statusSensor == 0)
  {
    digitalWrite(6, HIGH);
    delay(100);
     digitalWrite(7, HIGH);
    delay(100);
     digitalWrite(8, HIGH);
    delay(100);
     digitalWrite(9, HIGH);
    delay(100);
     digitalWrite(10, HIGH);
    delay(100);
     digitalWrite(11, HIGH);
    delay(100);
     digitalWrite(12, HIGH);
    delay(10000);
        digitalWrite(6, LOW);
    delay(300);
     digitalWrite(7, LOW);
    delay(300);
     digitalWrite(8, LOW);
    delay(300);
     digitalWrite(9, LOW);
    delay(300);
     digitalWrite(10, LOW);
    delay(300);
     digitalWrite(11, LOW);
    delay(300);
     digitalWrite(12, LOW);
  
  }
 
  else
  {
     digitalWrite(12, LOW);
     digitalWrite(11, LOW);
     digitalWrite(10, LOW);
     digitalWrite(9, LOW);
     digitalWrite(8, LOW);
     digitalWrite(7, LOW);
     digitalWrite(6, LOW);
  }  
}




CODE EXPLANATION:
Variables:
int IRSensor = 2;
This declares a variable called IRSensor and assigns it the value 2, which is the Arduino pin where the IR sensor is connected. The pin is set as an input in the setup() function.

setup() function:
void setup() 
{
  pinMode(IRSensor, INPUT); 
  pinMode(6, OUTPUT); 
  pinMode(7, OUTPUT);
  pinMode(8, OUTPUT);
  pinMode(9, OUTPUT);
  pinMode(10, OUTPUT);
  pinMode(11, OUTPUT);
  pinMode(12, OUTPUT);
}
The setup() function runs once when the Arduino is powered on or reset.
pinMode(IRSensor, INPUT) sets pin 2 (where the IR sensor is connected) as an input, meaning it will read the sensor's state (either HIGH or LOW).
Pins 6 through 12 are set as outputs (pinMode(6, OUTPUT) through pinMode(12, OUTPUT)) because these pins are connected to LEDs (or other devices) that will be turned on or off.

loop() function:
void loop()
{
  int statusSensor = digitalRead(IRSensor);
The loop() function continuously runs after setup().
The digitalRead(IRSensor) function reads the state of the IR sensor connected to pin 2. The state is stored in the variable statusSensor. The value will be either 0 (LOW) if the sensor is not activated or 1 (HIGH) if it is activated.

If the sensor is triggered (statusSensor == 0):
  if (statusSensor == 0)
  {
    digitalWrite(6, HIGH);
    delay(100);
    digitalWrite(7, HIGH);
    delay(100);
    digitalWrite(8, HIGH);
    delay(100);
    digitalWrite(9, HIGH);
    delay(100);
    digitalWrite(10, HIGH);
    delay(100);
    digitalWrite(11, HIGH);
    delay(100);
    digitalWrite(12, HIGH);
    delay(10000);
If the IR sensor reads 0 (indicating it is triggered, i.e., an object or person is detected), the program will execute the following sequence:
Each LED (pins 6 to 12) is turned on (digitalWrite(pin, HIGH)) with a delay of 100 milliseconds between each LED.
After turning on all the LEDs, there is a long delay of 10,000 milliseconds (10 seconds), during which the LEDs will stay on.
Turning off LEDs:
    digitalWrite(6, LOW);
    delay(300);
    digitalWrite(7, LOW);
    delay(300);
    digitalWrite(8, LOW);
    delay(300);
    digitalWrite(9, LOW);
    delay(300);
    digitalWrite(10, LOW);
    delay(300);
    digitalWrite(11, LOW);
    delay(300);
    digitalWrite(12, LOW);
  }
After the 10-second delay, the LEDs will be turned off one by one. Each LED is turned off with a delay of 300 milliseconds between each action.
If the sensor is not triggered (statusSensor != 0):
  else
  {
     digitalWrite(12, LOW);
     digitalWrite(11, LOW);
     digitalWrite(10, LOW);
     digitalWrite(9, LOW);
     digitalWrite(8, LOW);
     digitalWrite(7, LOW);
     digitalWrite(6, LOW);
  }
}
If the IR sensor is not triggered (i.e., it reads 1), the else block executes, which turns off all the LEDs connected to pins 6 through 12 immediately.

Conclusion:
The program continuously checks the state of an IR sensor. If the sensor detects something (sensor state is 0), it lights up LEDs on pins 6 to 12 sequentially with a 100ms delay. After all LEDs are lit, they stay on for 10 seconds and then turn off one by one with a 300ms delay.
If the sensor is not triggered, the program turns off all LEDs.


About:
The Automatic Staircase System is a practical, energy-efficient solution designed to improve the safety and usability of staircases, especially in low-light environments. The system automatically detects when a person is on the staircase and provides a visual indication using LEDs, enhancing both functionality and safety. The project demonstrates my ability to work with hardware and software integration, and it has been an excellent learning experience for me during my engineering studies.

This system uses an Arduino, IR sensors, and a series of LEDs to automatically detect when someone is on the staircase and indicate the direction of travel (up or down) using visual signals. The system is designed to provide a seamless and efficient user experience by lighting up the stairs automatically, improving visibility and safety for users.

1. Components Used:
Arduino Uno (Microcontroller):
This acts as the brain of the project, controlling all the logic and interactions based on input from the IR sensors and sending output to the LEDs.

IR Sensors:
I have used two IR sensors to detect movement on the stairs. One sensor is placed at the bottom of the stairs, and the other at the top. These sensors detect the presence of a person or an object by emitting and receiving infrared light. When the infrared light is interrupted, it triggers the sensor to send a signal to the Arduino.

LEDs:
A set of LEDs is used to indicate which step of the staircase is currently active. These LEDs are connected to pins 6 through 12 on the Arduino. When the sensors detect motion, corresponding LEDs will light up to show the direction and position of the person on the staircase.


2. Working of the System:

a. Step Detection Using IR Sensors:
When a person steps on the stairs, the IR sensor detects the interruption of the infrared light beam, indicating that a person is present.
The first IR sensor at the bottom will detect when a person is starting to climb the stairs, and the second IR sensor at the top will detect when they reach the top of the stairs.

b. LED Indication System:
Based on the signal from the IR sensors, the Arduino will turn on LEDs in sequence to indicate which step of the staircase the person is currently on.
For example, when a person begins to climb, the system lights up the first LED on the first step, the second LED for the second step, and so on.
The LEDs will stay lit for 10 seconds to provide ample time for the person to navigate the staircase. After that, the LEDs will turn off sequentially with a slight delay, to give a smooth effect as the person moves up or down.

c. Visual Feedback for Direction:
As the person progresses up or down the stairs, the LEDs dynamically light up and turn off in a sequence to show which direction the person is traveling.
This feature helps in providing a clear visual cue, especially in dark or poorly lit areas, improving safety.

3. Code and Logic Implementation:
The core of the project is controlled by the Arduino code, which continuously monitors the IR sensors to detect movement and adjusts the state of the LEDs accordingly.

IR Sensor Reading:
The Arduino continuously reads the state of the IR sensors. If the sensor detects an interruption (i.e., a person or object passing), it sends a signal to the Arduino to trigger the lighting of the LEDs.

LED Control:
When the IR sensor is triggered, the Arduino will turn on the LEDs sequentially with a short delay between each one (100ms), and then keep the LEDs on for 10 seconds. After the delay, the LEDs will turn off one by one with a 300ms delay, providing a smooth fading effect.

Turn Off LEDs:
If no movement is detected by the IR sensors, the system ensures that all LEDs are turned off, keeping the system energy-efficient and reducing unnecessary lighting.

4. Practical Application:
Enhanced Staircase Navigation:
This system can be used in residential or public spaces to help people navigate stairs, especially in the dark. The automatic lighting provides visual guidance, improving safety and convenience.

Hands-Free Operation:
It eliminates the need for manual control of the lights, making it a convenient, automated solution for staircases in homes, offices, or public buildings.

5. Future Improvements and Extensions:
Voice-Controlled System:
In future iterations, I plan to integrate a voice-control system where users can control the lighting or the direction of the staircase lighting using voice commands.

Bluetooth Control:
Another possible extension could be to add a Bluetooth module, allowing the user to control the system using a smartphone app for customization.
