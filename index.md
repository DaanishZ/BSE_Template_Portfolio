# Phone Controlled Robot Arm
My project will use an arduino and an android app to control a robot arm. This will be done using servo motors connected to the robot arm and arduino. The app must be able to establish a connection and control the robot arm. This robot arm will be able to do simple tasks such as holding onto items, picking up items, and pushing items away. 

<p align="center">
<a href="https://ibb.co/bXbNCZt"><img src="https://i.ibb.co/6FXDTxQ/WIN-20220722-09-37-44-Pro.jpg" alt="WIN-20220722-09-37-44-Pro" border="0"></a>
</p>
  
| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Daanish Zai | Canyon Crest Academy | Engineering | Incoming Sophomore

# Project Image
<p align="center">
<a href="https://ibb.co/Z88x3bM"><img src="https://i.ibb.co/3NNcwPC/20220721-123521.jpg" alt="20220721-123521" border="0"></a>
</p>

# Final Milestone
My final milestone allowed for control of the robotic arm through an application on my computer. I used the processing program in order to control all five servos of my arm.

[![Milestone 3](https://res.cloudinary.com/marcomontalbano/image/upload/v1658507592/video_to_markdown/images/youtube--Gh1PW66VUKI-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://youtu.be/Gh1PW66VUKI "Milestone 3"){:target="_blank" rel="noopener"}

# Second Milestone
My second milestone involved assembling my robot arm. When fully completed, my arm have 5 servo motors. I enabled these servo motors to be controlled using either potentiometers or a GUI interface on my computer. Challenges included aligning the claw properly so that it would open and close properly. I fixed this by removing the claw, and repositioning it to that it could open and close at proper angles.

[![Milestone 2](https://res.cloudinary.com/marcomontalbano/image/upload/v1658165576/video_to_markdown/images/youtube--jp-kyhQX7Nw-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://youtu.be/jp-kyhQX7Nw "Milestone 2")

# First Milestone
My first milestone involved using an Arduino, HC-05 Bluetooth module, and Android application to move a servo motor. One of my challenges was uploading to code to the Arduino. I did not realize at first that I had to unplug my HC-05 in order to upload my code without error. After I figured this out, my code uploaded properly. Another challenge included connecting the Arduino to my phone. My phone kept connecting to other bluetooth devices. I fixed this error by unpairing any other bluetooth devices so that my bluetooth module was the only available connection.

[![Milestone 1](https://res.cloudinary.com/marcomontalbano/image/upload/v1657646065/video_to_markdown/images/youtube--OJJFwEuBUb8-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://youtu.be/OJJFwEuBUb8 "Milestone 1"){:target="_blank" rel="noopener"}

# Bill of Materials

| Item | Qty | Price | Where to Buy |
| ------------- | ------------- | ------------- | ------------- |
| Adeept Robotic Arm Kit  | 1  | $64.99  | https://www.amazon.com/dp/B087R8DLG6 |
| Breadboard  | 1 |  $6.75  | https://www.amazon.com/BB400-Solderless-Plug-BreadBoard-tie-points/dp/B0040Z1ERO |
| Potentiometer  | 1 | $1.85  |  https://www.tubesandmore.com/products/potentiometer-alpha-linear-38-bushing  |
| Micro Servo | 1 | $5.95 | https://www.adafruit.com/product/169  |
| Jumper Wires  | 6 | 10¢/wire  |  https://www.amazon.com/Breadboard-Jumper-Wire-75pcs-pack/dp/B0040DEI9M |
| Arduino Uno Board  | 1  | $27.60  | https://store-usa.arduino.cc/products/arduino-uno-rev3?selectedStore=us  |
| Arduino IDE  | 1  | $0  | https://www.arduino.cc/en/software/ |
| HC-05 Bluetooth Module  | 1  | $9.99  | https://www.amazon.com/DSD-TECH-HC-05-Pass-through-Communication/dp/B01G9KSAF6 |

# Schematics

This is a schematic of the Adeept robotic arm drive board that is connected to the robotic arm.

<p align="center">
<a href="https://ibb.co/jzppdJK"><img src="https://i.ibb.co/Nr44XTh/c14cded516.jpg" alt="c14cded516" border="0"></a>
</p>  

# How to recreate the project

When recreating the project, know that it is not too difficult of a task, but neither is it too easy. Grab a screwdriver or two, and have a positive and open mindset througout the building process to have the most success. Not to mention have fun! If you face issues regarding servo motors, take apart the corresponding servo motor from the diagram and replace or attempt to screw it back together. Keep a pair of pliers or wrenches to help you fix the pesky screws and bolts. Do not use pressure or handle the robot arm with roughness. The components may definitely break! Do not apply too much pressure. If your program is not working either restart the laptop or computer you are using, or re-upload the code. Make sure all your ports are connected check the “Tools” button in Arduino. Be careful at all time and have fun again! *** I also suggest looking here and following the instructions: http://www.adeept.com/learn/details/id/31.

# Arduino Code for Processing

```
import controlP5.*;
import processing.serial.*;

ControlP5 cp5;

controlP5.Button b1;
controlP5.Button b2;
controlP5.Button m1;
controlP5.Button m2;
controlP5.Button m3;
controlP5.Button m4;
controlP5.Button m5;
controlP5.Button m6;
controlP5.Button m7;
controlP5.Button m8;
controlP5.Button m9;
controlP5.Button m10;
controlP5.Button k1;
controlP5.Button k2;
controlP5.Button k3;
controlP5.Button k4;
controlP5.Button k5;
controlP5.Button k6;
controlP5.Button k7;
controlP5.Button k8;
controlP5.Button k9;
controlP5.Button k10;

Textlabel label1;
Textlabel label2;
Textlabel label3;
Textlabel label4;
Textlabel label5;
Textlabel label6;
Textlabel label7;
Textlabel label8;

int buttonValue = 1;

char letter;

boolean isOpen=true;

boolean b1Open, b2Open, Aopen, Sopen, btMute;

boolean toggleValue = false;

float b1x=-300, b1y=190, b2x=-300, b2y=190, m1x=-200, m1y=330, m2x=1400, m2y=330, m3x=-200, m3y=390;
float m4x=1400, m4y=390, m5x=-200, m5y=450, m6x=1400, m6y=450, m7x=-200, m7y=510, m8x=1400, m8y=510, m9x=1400, m9y=570;
float m10x=1400, m10y=570, k1x=-200, k1y=430, k2x=1400, k2y=430, k3x=-200, k3y=430, k4x=1400, k4y=430, k5x=-200, k5y=430;
float k6x=1400, k6y=430, k7x=-200, k7y=430, k8x=1400, k8y=430, k9x=1400, k9y=430, k10x=1400, k10y=430;
float label1x=-600, label1y=600, label2x=-600, label2y=600, label3x=-600, label3y=600, label4x=-600, label4y=380;
float label5x=-600, label5y=380, label6x=1300, label6y=380, label7x=1300, label7y=380, label8x=1300, label8y=380;
Serial port1;

void setup() {

  size(1200, 700);
  smooth();
  // List all the available serial ports:
  printArray(Serial.list());
  // Open the port you are using at the rate you want:
  port1 = new Serial(this, "COM7", 9600);

  // Or you can use the port number directly:
  // port1 = new Serial(this,"COM9", 9600);

  // starts the serial communication
  port1.bufferUntil('\n');

  cp5 = new ControlP5(this);

  b1 = cp5.addButton("b1")
    .setValue(4)
    .setPosition(b1x, b1y)
    .setSize(250, 100);

  b2 = cp5.addButton("b2")
    .setValue(4)
    .setPosition(-300, 190)
    .setSize(200, 100);

  m1 = cp5.addButton("m1")
    .setValue(4)
    .setPosition(-200, 330)
    .setSize(90, 50);

  m2 = cp5.addButton("m2")
    .setValue(4)
    .setPosition(1400, 330)
    .setSize(90, 50);

  m3 = cp5.addButton("m3")
    .setValue(4)
    .setPosition(-200, 390)
    .setSize(90, 50);

  m4 = cp5.addButton("m4")
    .setValue(4)
    .setPosition(1400, 390)
    .setSize(90, 50);

  m5 = cp5.addButton("m5")
    .setValue(4)
    .setPosition(-200, 450)
    .setSize(90, 50);

  m6 = cp5.addButton("m6")
    .setValue(4)
    .setPosition(1400, 450)
    .setSize(90, 50);

  m7 = cp5.addButton("m7")
    .setValue(4)
    .setPosition(-200, 510)
    .setSize(90, 50);

  m8 = cp5.addButton("m8")
    .setValue(4)
    .setPosition(1400, 510)
    .setSize(90, 50);

  m9 = cp5.addButton("m9")
    .setValue(4)
    .setPosition(-200, 570)
    .setSize(90, 50);

  m10 = cp5.addButton("m10")
    .setValue(4)
    .setPosition(1400, 570)
    .setSize(90, 50);

  k1 = cp5.addButton("q")//q
    .setValue(4)
    .setPosition(-200, 430)
    .setSize(90, 90);

  k2 = cp5.addButton("w")//w
    .setValue(4)
    .setPosition(1400, 430)
    .setSize(90, 90);

  k3 = cp5.addButton("e")//e
    .setValue(4)
    .setPosition(-200, 430)
    .setSize(90, 90);

  k4 = cp5.addButton("r")//r
    .setValue(4)
    .setPosition(1400, 430)
    .setSize(90, 90);

  k5 = cp5.addButton("t")//t
    .setValue(4)
    .setPosition(-200, 430)
    .setSize(90, 90);

  k6 = cp5.addButton("y")//y
    .setValue(4)
    .setPosition(1400, 430)
    .setSize(90, 90);

  k7 = cp5.addButton("u")//u
    .setValue(4)
    .setPosition(-200, 430)
    .setSize(90, 90);

  k8 = cp5.addButton("i")//i
    .setValue(4)
    .setPosition(1400, 430)
    .setSize(90, 90);

  k9 = cp5.addButton("o")
    .setValue(4)
    .setPosition(-200, 430)
    .setSize(90, 90);

  k10 = cp5.addButton("p")
    .setValue(4)
    .setPosition(1400, 430)
    .setSize(90, 90);

  PFont pfont = createFont("Arial", 20, true);
  ControlFont font = new ControlFont(pfont, 241);

  b1.getCaptionLabel()//captionLabel
    .setFont(font)
    .setSize(50)
    .toUpperCase(false)
    .setText(" keyboard");

  b2.getCaptionLabel()
    .setFont(font)
    .setSize(50)
    .toUpperCase(false)
    .setText(" mouse");

  m1.getCaptionLabel()
    .setFont(font)
    .setSize(20)
    .toUpperCase(false)
    .setText("Gripper+");

  m2.getCaptionLabel()
    .setFont(font)
    .setSize(20)
    .toUpperCase(false)
    .setText("Gripper-");

  m3.getCaptionLabel()
    .setFont(font)
    .setSize(20)
    .toUpperCase(false)
    .setText("Rotate+");

  m4.getCaptionLabel()
    .setFont(font)
    .setSize(20)
    .toUpperCase(false)
    .setText("Rotate-");

  m5.getCaptionLabel()
    .setFont(font)
    .setSize(20)
    .toUpperCase(false)
    .setText("Elbow+");

  m6.getCaptionLabel()
    .setFont(font)
    .setSize(20)
    .toUpperCase(false)
    .setText("Elbow-");

  m7.getCaptionLabel()
    .setFont(font)
    .setSize(20)
    .toUpperCase(false)
    .setText("Shoulder+");

  m8.getCaptionLabel()
    .setFont(font)
    .setSize(20)
    .toUpperCase(false)
    .setText("Shoulder-");

  m9.getCaptionLabel()
    .setFont(font)
    .setSize(20)
    .toUpperCase(false)
    .setText("Base+");

  m10.getCaptionLabel()
    .setFont(font)
    .setSize(20)
    .toUpperCase(false)
    .setText("Base-");


  k1.getCaptionLabel()
    .setFont(font)
    .setSize(50)
    .toUpperCase(false)
    .setText(" Q");//A

  k2.getCaptionLabel()
    .setFont(font)
    .setSize(50)
    .toUpperCase(false)
    .setText(" W");//S

  k3.getCaptionLabel()
    .setFont(font)
    .setSize(50)
    .toUpperCase(false)
    .setText(" E");//D

  k4.getCaptionLabel()
    .setFont(font)
    .setSize(50)
    .toUpperCase(false)
    .setText(" R");//F

  k5.getCaptionLabel()
    .setFont(font)
    .setSize(50)
    .toUpperCase(false)
    .setText(" T");//G

  k6.getCaptionLabel()
    .setFont(font)
    .setSize(50)
    .toUpperCase(false)
    .setText(" Y");//H

  k7.getCaptionLabel()
    .setFont(font)
    .setSize(50)
    .toUpperCase(false)
    .setText(" U");//J

  k8.getCaptionLabel()
    .setFont(font)
    .setSize(50)
    .toUpperCase(false)
    .setText(" I");//K

  k9.getCaptionLabel()
    .setFont(font)
    .setSize(50)
    .toUpperCase(false)
    .setText(" O");

  k10.getCaptionLabel()
    .setFont(font)
    .setSize(50)
    .toUpperCase(false)
    .setText(" P");

  label1 = cp5.addTextlabel("label1")
    .setText("Keyboard Activated.")
    .setPosition(-600, 600)
    .setColorValue(0xff888888)
    .setFont(createFont("Arial", 50));

  label2 = cp5.addTextlabel("label2")
    .setText("Mouse Activated.")
    .setPosition(-600, 600)
    .setColorValue(0xff888888)
    .setFont(createFont("Arial", 50));

  label4 = cp5.addTextlabel("label4")
    .setText("Gripper")
    .setPosition(-600, 380)
    .setColorValue(0xff888888)
    .setFont(createFont("Arial", 40));

  label5 = cp5.addTextlabel("label5")
    .setText("Rotate")
    .setPosition(-600, 380)
    .setColorValue(0xff888888)
    .setFont(createFont("Arial", 40));

  label6 = cp5.addTextlabel("label6")
    .setText("Elbow")
    .setPosition(1300, 380)
    .setColorValue(0xff888888)
    .setFont(createFont("Arial", 40)); 

  label7 = cp5.addTextlabel("label7")
    .setText("Shoulder")
    .setPosition(1300, 380)
    .setColorValue(0xff888888)
    .setFont(createFont("Arial", 40)); 

  label8 = cp5.addTextlabel("label8")
    .setText("Base")
    .setPosition(1300, 380)
    .setColorValue(0xff888888)
    .setFont(createFont("Arial", 40));
}

void stop()
{
  super.stop() ;
}

void draw() {
  background(0, 0, 0);

  textSize(70);

  fill(169, 169, 169);
  text("Adeept Robotic Arm", 250, 100);
  textSize(32);
  text("www.adeept.com", 850, 650);
  if (isOpen==true) {
    b1x = b1x+(250-b1x)*0.1; 
    b1.setPosition(b1x, b1y);
    b2x = b2x+(750-b2x)*0.1; 
    b2.setPosition(b2x, b2y);
  }
  if (isOpen==true && b2Open==true) {
    m1x = m1x+(500-m1x)*0.1; 
    m1.setPosition(m1x, m1y);
    m2x = m2x+(610-m2x)*0.1; 
    m2.setPosition(m2x, m2y);
    m3x = m3x+(500-m3x)*0.1; 
    m3.setPosition(m3x, m3y);
    m4x = m4x+(610-m4x)*0.1; 
    m4.setPosition(m4x, m4y);
    m5x = m5x+(500-m5x)*0.1; 
    m5.setPosition(m5x, m5y);
    m6x = m6x+(610-m6x)*0.1; 
    m6.setPosition(m6x, m6y);
    m7x = m7x+(500-m7x)*0.1; 
    m7.setPosition(m7x, m7y);
    m8x = m8x+(610-m8x)*0.1; 
    m8.setPosition(m8x, m8y);
    m9x = m9x+(500-m9x)*0.1; 
    m9.setPosition(m9x, m9y);
    m10x = m10x+(610-m10x)*0.1; 
    m10.setPosition(m10x, m10y);
  }
  if (!(isOpen==true && b2Open==true)) {
    m1x = m1x+(-100-m1x)*0.1; 
    m1.setPosition(m1x, m1y);
    m2x = m2x+(1300-m2x)*0.1; 
    m2.setPosition(m2x, m2y);
    m3x = m3x+(-100-m3x)*0.1; 
    m3.setPosition(m3x, m3y);
    m4x = m4x+(1300-m4x)*0.1; 
    m4.setPosition(m4x, m4y);
    m5x = m5x+(-100-m5x)*0.1; 
    m5.setPosition(m5x, m5y);
    m6x = m6x+(1300-m6x)*0.1; 
    m6.setPosition(m6x, m6y);
    m7x = m7x+(-100-m7x)*0.1; 
    m7.setPosition(m7x, m7y);
    m8x = m8x+(1300-m8x)*0.1; 
    m8.setPosition(m8x, m8y);
    m9x = m9x+(-100-m9x)*0.1; 
    m9.setPosition(m9x, m9y);
    m10x = m10x+(1300-m10x)*0.1; 
    m10.setPosition(m10x, m10y);
  }
  if (isOpen==true && b1Open==true) {
    k1x = k1x+(100-k1x)*0.1; 
    k1.setPosition(k1x, k1y);
    k2x = k2x+(200-k2x)*0.1; 
    k2.setPosition(k2x, k2y);
    k3x = k3x+(300-k3x)*0.1; 
    k3.setPosition(k3x, k3y);
    k4x = k4x+(400-k4x)*0.1; 
    k4.setPosition(k4x, k4y);
    k5x = k5x+(500-k5x)*0.1; 
    k5.setPosition(k5x, k5y);
    k6x = k6x+(600-k6x)*0.1; 
    k6.setPosition(k6x, k6y);
    k7x = k7x+(700-k7x)*0.1; 
    k7.setPosition(k7x, k7y);
    k8x = k8x+(800-k8x)*0.1; 
    k8.setPosition(k8x, k8y);
    k9x = k9x+(900-k9x)*0.1; 
    k9.setPosition(k9x, k9y);
    k10x = k10x+(1000-k10x)*0.1; 
    k10.setPosition(k10x, k10y);
    label1x = label1x+(100-label1x)*0.1; 
    label1.setPosition(label1x, label1y);
    label4x = label4x+(140-label4x)*0.1; 
    label4.setPosition(label4x, label4y);
    label5x = label5x+(340-label5x)*0.1; 
    label5.setPosition(label5x, label5y);
    label6x = label6x+(550-label6x)*0.1; 
    label6.setPosition(label6x, label6y);
    label7x = label7x+(730-label7x)*0.1; 
    label7.setPosition(label7x, label7y);
    label8x = label8x+(960-label8x)*0.1; 
    label8.setPosition(label8x, label8y);
  }
  if (!(isOpen==true && b1Open==true)) {
    k1x = k1x+(-200-k1x)*0.1; 
    k1.setPosition(k1x, k1y);
    k2x = k2x+(1300-k2x)*0.1; 
    k2.setPosition(k2x, k2y);
    k3x = k3x+(-100-k3x)*0.1; 
    k3.setPosition(k3x, k3y);
    k4x = k4x+(1300-k4x)*0.1; 
    k4.setPosition(k4x, k4y);
    k5x = k5x+(-100-k5x)*0.1; 
    k5.setPosition(k5x, k5y);
    k6x = k6x+(1300-k6x)*0.1; 
    k6.setPosition(k6x, k6y);
    k7x = k7x+(-100-k7x)*0.1; 
    k7.setPosition(k7x, k7y);
    k8x = k8x+(1300-k8x)*0.1; 
    k8.setPosition(k8x, k8y);
    k9x = k9x+(-100-k9x)*0.1; 
    k9.setPosition(k9x, k9y);
    k10x = k10x+(1300-k10x)*0.1; 
    k10.setPosition(k10x, k10y);
    label1x = label1x+(-600-label1x)*0.1; 
    label1.setPosition(label1x, label1y);
    label4x = label4x+(-600-label4x)*0.1; 
    label4.setPosition(label4x, label4y);
    label5x = label5x+(-600-label5x)*0.1; 
    label5.setPosition(label5x, label5y);
    label6x = label6x+(1300-label6x)*0.1; 
    label6.setPosition(label6x, label6y);
    label7x = label7x+(1300-label7x)*0.1; 
    label7.setPosition(label7x, label7y);
    label8x = label8x+(1300-label8x)*0.1; 
    label8.setPosition(label8x, label8y);
  }
  if (isOpen==true && b2Open==true) {
    label2x = label2x+(100-label2x)*0.1; 
    label2.setPosition(label2x, label2y);
  }
  if (!(isOpen==true && b2Open==true)) {
    label2x = label2x+(-600-label2x)*0.1; 
    label2.setPosition(label2x, label2y);
  } 

  if (b1.isPressed()) {
    b1Open = true;
    b2Open = false;
    port1.write("b");
  }
  if (b2.isPressed()) {
    b1Open = false;
    b2Open = true;
    port1.write("m");
  }

  if (isOpen==true) {
    buttonColor();
    mouseCheck();
  }
  if (isOpen==false) {
    b1Open=false;
    b2Open=true;
    port1.write("z");
  }
}

void keyPressed() {
  if (b1Open == true) {
    if (key >= 'A' && key <= 'z') {
      port1.write(key);
      println(key);
    }
  }
}

void mouseCheck() {
  if (b2Open == true) {
    if (m1.isPressed()) {
      port1.write("q");
      println("Gripper+");
    }
    if (m2.isPressed()) {
      port1.write("w");
      println("Gripper-");
    }
    if (m3.isPressed()) {
      port1.write("e");
      println("Rotate +");
      delay(10);
    }
    if (m4.isPressed()) {
      port1.write("r");   
      println("Rotate -");
      delay(10);
    }
    if (m5.isPressed()) {
      port1.write("t");   
      println("elbow up");
      delay(10);
    }
    if (m6.isPressed()) {
      port1.write("y");   
      println("elbow down");
      delay(10);
    }
    if (m7.isPressed()) {
      port1.write("u");   
      println("sholder up");
      delay(10);
    }
    if (m8.isPressed()) {
      port1.write("i");
      println("shoulder down");
      delay(10);
    }
    if (m9.isPressed()) {
      port1.write("o");
      println("base right");
      delay(10);
    }
    if (m10.isPressed()) {
      port1.write("p");
      println("base left");
      delay(10);
    }
  }
}

void buttonColor() {
  if (b1Open==true) {
    if (keyPressed && key=='q') {//a
      k1.setColorBackground(color(255, 0, 0) );
    } else {
      k1.setColorBackground(color(2, 72, 90));
    }
    if (keyPressed && key=='w') {//s
      k2.setColorBackground(color(255, 0, 0));
    } else {
      k2.setColorBackground(color(2, 72, 90));
    }
    if (keyPressed && key=='e') {//d
      k3.setColorBackground(color(255, 0, 0));
    } else {
      k3.setColorBackground(color(2, 72, 90));
    }
    if (keyPressed && key=='r') {//f
      k4.setColorBackground(color(255, 0, 0));
    } else {
      k4.setColorBackground(color(2, 72, 90));
    }
    if (keyPressed && key=='t') {//g
      k5.setColorBackground(color(255, 0, 0));
    } else {
      k5.setColorBackground(color(2, 72, 90));
    }
    if (keyPressed && key=='y') {//h
      k6.setColorBackground(color(255, 0, 0));
    } else {
      k6.setColorBackground(color(2, 72, 90));
    }
    if (keyPressed && key=='u') {//j
      k7.setColorBackground(color(255, 0, 0));
    } else {
      k7.setColorBackground(color(2, 72, 90));
    }
    if (keyPressed && key=='i') {//k
      k8.setColorBackground(color(255, 0, 0 ));
    } else {
      k8.setColorBackground(color(2, 72, 90));
    }
    if (keyPressed && key=='o') {
      k9.setColorBackground(color(255, 0, 0 ));
    } else {
      k9.setColorBackground(color(2, 72, 90));
    }
    if (keyPressed && key=='p') {
      k10.setColorBackground(color(255, 0, 0 ));
    } else {
      k10.setColorBackground(color(2, 72, 90));
    }
  }
}
```
