# Robot-Hand
# Robotic-Arm

#### Table of Contents

 [- Overview](https://github.com/OstrichIsYum/Robotic-Hand/blob/main/README.md#overview)
 
 [- Tools](https://github.com/OstrichIsYum/Robotic-Hand/blob/main/README.md#tools)
 
 [- Wiring Diagram](https://github.com/OstrichIsYum/Robotic-Hand/blob/main/README.md#wiring-diagram-and-commented-code)
 
 [- Plans and Designs](https://github.com/OstrichIsYum/Robotic-Hand/blob/main/README.md#plans-and-designs)
 
 [- Photos and Videos](https://github.com/OstrichIsYum/Robotic-Hand/blob/main/README.md#photos-and-videos)
 
 [- Problems and Solutions](https://github.com/OstrichIsYum/Robotic-Hand/blob/main/README.md#problems-and-solutions)

 [- Collaborators](https://github.com/OstrichIsYum/Robotic-Hand/blob/main/README.md#collaborators)


### Overview

- This projects goal was to make a Robotic arm. The fun part was that there weren't any real specifications, so anything could happen. What we decided was to make a flex sensor controlled arm, that would mimic the fingers of an individual. In Theory, this arm could be used as a multi-purposed arm. It could pick up certain toxic objects that may be considered dangerous for humans to touch or come in contact with, being attached to a rover, used to test chemical reactions from a distance, additional virtual assistants, or even petting porcupines. The user could wear a glove with the flex sencors attached, and the hand does exactally what the controller does. It's a fairly Simple idea, but carrying it out is a whole other story.

_________________________________________________________________________________________________________________________________________________________________________

### Tools

 [- Arduino (Code)](https://www.arduino.cc/en/software)
 
 [- Onshape (CAD)](https://www.onshape.com/en/)
 
 [- Tinkercad (Wiring Diagram)](https://www.tinkercad.com/)
 
 [- Github (Documentation)](https://github.com/)
 
 ________________________________________________________________________________________________________________________________________________________________________
 
 ### Wiring Diagram and Commented Code

<img src="Screenshot%20(3).png?raw=true" width="400">
 
<details><summary>Robotic Arm Code</summary>
 
``` arduino
#include <Servo.h> // HEY!!!... here's a servo

Servo servo1; // Labeling Micro Servo #1
Servo servo2; // Labeling Micro Servo #2
Servo servo3; // Labeling Micro Servo #3
Servo servo4; // Labeling Micro Servo #4
Servo servo5; // Labeling Micro Servo #5

int flex1 = A0; // Pin set up for Flex Sensor #1
int flex2 = A1; // Pin set up for Flex Sensor #2
int flex3 = A2; // Pin set up for Flex Sensor #3
int flex4 = A3; // Pin set up for Flex Sensor #4
int flex5 = A4; // Pin set up for Flex Sensor #5

void setup()
{
  Serial.begin(9600);
  
  servo1.attach(8); // Pin set up for Micro Servo #1
  servo2.attach(9); // Pin set up for Micro Servo #2
  servo3.attach(10); // Pin set up for Micro Servo #3
  servo4.attach(11); // Pin set up for Micro Servo #4
  servo5.attach(12); // Pin set up for Micro Servo #5
}

void loop()
{
  int flexValue1; // For calibrating Flex Sensor #1
  int flexValue2; // For calibrating Flex Sensor #2
  int flexValue3; // For calibrating Flex Sensor #3
  int flexValue4; // For calibrating Flex Sensor #4
  int flexValue5; // For calibrating Flex Sensor #5
  int servoPosition1; // For Synchronizing the angles of the Flex Sencor #1 to Micro Servo #1
  int servoPosition2; // For Synchronizing the angles of the Flex Sencor #2 to Micro Servo #2
  int servoPosition3; // For Synchronizing the angles of the Flex Sencor #3 to Micro Servo #3
  int servoPosition4; // For Synchronizing the angles of the Flex Sencor #4 to Micro Servo #4
  int servoPosition5; // For Synchronizing the angles of the Flex Sencor #5 to Micro Servo #5

  flexValue1 = analogRead(flex1); // Renaming analogRead for #1
  flexValue2 = analogRead(flex2); // Renaming analogRead for #2
  flexValue3 = analogRead(flex3); // Renaming analogRead for #3
  flexValue4 = analogRead(flex4); // Renaming analogRead for #4
  flexValue5 = analogRead(flex5); // Renaming analogRead for #5

  servoPosition1 = map(flexValue1, 600, 800, 0, 180); // when flex sensor #1 is bend, micro servo #1 will make the angle...
  servoPosition1 = constrain(servoPosition1, 0, 180); // .. but will not go passed 0 or 180
  servoPosition2 = map(flexValue2, 600, 800, 0, 180); // when flex sensor #2 is bend, micro servo #2 will make the angle...
  servoPosition2 = constrain(servoPosition2, 0, 180); // .. but will not go passed 0 or 180
  servoPosition3 = map(flexValue3, 600, 800, 0, 180); // when flex sensor #3 is bend, micro servo #3 will make the angle...
  servoPosition3 = constrain(servoPosition3, 0, 180); // .. but will not go passed 0 or 180
  servoPosition4 = map(flexValue4, 600, 800, 0, 180); // when flex sensor #4 is bend, micro servo #4 will make the angle...
  servoPosition4 = constrain(servoPosition4, 0, 180); // .. but will not go passed 0 or 180
  servoPosition5 = map(flexValue5, 600, 800, 0, 180); // when flex sensor #5 is bend, micro servo #5 will make the angle...
  servoPosition5 = constrain(servoPosition5, 0, 180); // .. but will not go passed 0 or 180

  servo1.write(servoPosition1);
  servo2.write(servoPosition2);
  servo3.write(servoPosition3);
  servo4.write(servoPosition4);
  servo5.write(servoPosition5);

  delay(100); // reaction time for Micro Servo
  }
```
</details>
 
_________________________________________________________________________________________________________________________________________________________________________

### Plans and Designs

#### [- Planning Document and Pseudocode](https://docs.google.com/document/d/1A5yr3gwvPFNczzGg2IPSaRJFIutgpFQ-Hbp36jQhLAk/edit?usp=sharing)

- We had many iterations of what the project could look like, however, in the end, you can see that the designs we came up with ended up looking nothing like the end result. At First, we thought it would be good to attach the arm to some sort of stand or wall. However, we soon realized that this would take extra time away from the actual design, so we stayed away from it. We even had a prototype design for these specifications, and it would’ve moved along the wall like [Mark Rober’s moving dart board,](https://www.youtube.com/watch?v=MHTizZ_XcUM) but we scratch that idea as well. This design could be done in the future, but we decided to keep it simple. Our final design uses a premade hand, controlled by servos pulling on each finger, with elastic pulling back to keep its shape.

#### Stand and Wall designs
<img src="Idea%231's.jpg?raw=true" width="200"><img src="Idea%232's.jpg?raw=true" width="200"><img src="Idea%233's.jpg?raw=true" width="200">

#### [- CAD Prototype Specified for wall ](https://cvilleschools.onshape.com/documents/bb650a5758ea41f57e61b52f/w/1ee44fa1089f16d3b393ba3a/e/24473f01d90508c6ebd4ea05)

<img src="Screenshot%202021-06-09%202.15.11%20PM.png?raw=true" width="400"> [← Wall mounted design](https://drive.google.com/file/d/1KeHIvSfq9kleZb0yazV1TSGmkmo0Zmrf/view?usp=sharing)

#### [- Final Design](https://cvilleschools.onshape.com/documents/e2edc0296736b251a4e3fe74/w/817a81a4a4728dc8bb2cad43/e/76581a513e1b4ba1cefbcda2)

<img src="Screenshot%202021-05-03%2011.10.20%20AM.png?raw=true" width="400"> [←Hand working](https://drive.google.com/file/d/125KFlFFFpU-OIzBG-1Z3dFMdSSbtWHqi/view?usp=sharing)
 
 ________________________________________________________________________________________________________________________________________________________________________
 
 ### Photos and Videos
 
 [1. Code staring to work](https://drive.google.com/file/d/16vUKTdU-LGm613mKrdmvg-yJmQ_zKxg0/view?usp=sharing)
 
 [2. Robotic Arm done (missing two flex sensors, but code completely works)](https://drive.google.com/file/d/125KFlFFFpU-OIzBG-1Z3dFMdSSbtWHqi/view?usp=sharing)
 
3. Robotic Arm fully contructed
<img src="https://github.com/hcoyle91/Robot-Hand/blob/e430b16c6d871e3e28249e15b37e499d08cd1535/picture%2010.png" width="325">
 
4. Final assembly with first prototype
<img src="https://github.com/hcoyle91/Robot-Hand/blob/007f299c76986c3f3cd28e107b4acc76967f4d24/picture%209.png" width="325">
 
 ________________________________________________________________________________________________________________________________________________________________________
  
### Problems and Solutions
 
- The main issues I ran into a lot were that most of the materials I was given didn't work. I went through many USB Cords and two Metro Express's during this school year. I also didn't have any prior expierence with flex sensors before, and I couldn't find a single thing about using them with a metro express. The best solution I found was switch over to an Arduino Uno. Now that I had somthing that worked, I was able to figure out how to use flex sensors. For anyone overwhelmed by using Flex Sencors for the first time or trying to recreate this project, Here is the code for the project in english." If the flex sensor is bent to a certain angle between 0 and 180, the servo will match the angle." that's it. And if you the code for this project, I hope can see that it's not as complex as you might think. it's a bit redundant but it's not complex. So when it doubt, with any project, "Make it as simple as you can so you don't hurt your brain.For Cad, it was a bit difficult to find a high quality pre-made hands to download onto onshape. However that was quickly taken care of. the only real obstacle was the speed of 3d printing and fabrication. Assembly was also a bit of a pain due to working at home, but as you can see, it turn out alright.

 ________________________________________________________________________________________________________________________________________________________________________
 
 ### Collaborators

- [Henry C.](https://github.com/hcoyle91)
- [Dylan H.](https://github.com/OstrichIsYum)
