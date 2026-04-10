# Introduction to Python and Edison Robot V3
Over the next ten weeks we will be learning the basics of programming. 

The environments that we'll be utilising will be the Python programming language and the Edison V3 robot.  We'll also make use of a microcontroller environment called Wokwi towards the end.

## Why Python?
Python is a great language to start learning programming because it is simple, readable, and widely used. Its clear, English-like syntax makes it easier for beginners to understand programming concepts without getting overwhelmed by complex rules. Python also has a huge community and countless free resources, meaning learners can quickly find tutorials, examples, and help when stuck. At the same time, it is powerful enough to be used in real-world applications such as web development, data science, artificial intelligence, and automation. This combination of simplicity and versatility makes Python both beginner-friendly and highly practical for future projects. 

## Why Edison?
The Edison V3 robot is a great way to start learning programming because it combines simplicity with powerful, hands-on learning. Learners can write code that directly controls its sensors, motors, and outputs, making abstract concepts easy to understand through real-world results. It is affordable, durable, and easy to set up with USB charging and a built-in rechargeable battery, so the focus stays on coding rather than technical setup. With free resources, browser-based programming tools, and strong community support, Edison V3 provides an engaging and practical entry point into programming. 

Most importantly, hopefully it's going to be fun!

## What do we need?
We'll provide you with an Edison robot during class time.
To interface with the robot you'll need to go to:  https://www.edpyapp.com/v3/ 
It's recommended that you use the Chrome browser to open the above coding environment. 
 
There are also video tutorials and a workbook that the Edison team have made available for you to use.  Feel free to use these but be aware that they are not an official part of the course. 

All classwork and assignments will be available via MSTeams.

## Getting to know the Edison
![Edison Sensors Top](../assets/edison-sensors.png)

## Downloading a simple program to the Edison
The Edison is programmed via an editor which is found at [https://www.edpyapp.com/v3/](https://www.edpyapp.com/v3/) (use Chrome to open). 

### Connect Edison to the computer using the USB cable
Connect Edison to the computer using the USB cable:

![Edison Plugged In](../assets/edison-plugged-50.jpg)

### Upload the Python code to the Edison
Press the ‘Program’ button in the upper right corner of the EdPy app, In the pop-up window select ‘Edison V3 – Paired’ and click ‘Connect’:

![Program Button](../assets/edpy-upload-cmp.gif)

## Structure of an EdPy program
Programming the Edison consists of two main parts.  The Setup part and the Instructional code.  Let's look at the code below which you'll use in Task 1. 

```py
#-------------Setup----------------
import Ed
Ed.EdisonVersion = Ed.V3

Ed.DistanceUnits = Ed.TIME
Ed.Tempo = Ed.TEMPO_MEDIUM

#--------Your code below-----------
while True:
    Ed.PlayBeep()
    Ed.LeftLed(Ed.OFF)
    Ed.RightLed(Ed.ON)
    Ed.Drive(Ed.SPIN_RIGHT, Ed.SPEED_5, 350)
    Ed.TimeWait(20, Ed.TIME_MILLISECONDS)
    Ed.PlayBeep()
    Ed.LeftLed(Ed.ON)
    Ed.RightLed(Ed.OFF)
    Ed.Drive(Ed.SPIN_LEFT, Ed.SPEED_5, 350)
    Ed.TimeWait(20, Ed.TIME_MILLISECONDS)
```

### Setup code  
All Edison programs must contain the setup code.  The Setup section tells the Edison how it should set itself up.  This means what version it is and what units it should use.  For example, should it measure distance in cm or seconds. 

- Line 1 of the setup code starts with a ‘#’ (hash) character. When a line starts with this character, it is called a ‘comment line.’ Any characters that come after the ‘#’ are ignored by the compiler. The text following after the # is used to document code so that other people can understand the program. Line 9 contains another comment line which will also be ignored by the EdPy compiler.  Comments are used to communicate with other programmers, not the computer. 
```py linenums="0"
#-------------Setup----------------#
```

- Line 2 contains the ‘import’ command. This tells Python to ‘import’ another library of pre-written Python code. In line 4 of the setup, we are importing all the built-in Edison Python commands, in other words, all the EdPy commands. These built-in commands will all start with the prefix ‘Ed.’ and allow us to program the Edison robot in Python.  The import allows the compiler/computer to understand how to interface with the Edison robot.  
```py linenums="0"
import Ed
```

- Line 3 defines the built-in Edison variable that relates to the version of Edison you are using.  
```py linenums="0"
Ed.EdisonVersion = Ed.V3
```

- Line 5 defines the built-in Edison variable that relates to the distance units used by the robot: inches, cm or time (in seconds). If you want to use inches, you should change this line to: Ed.DistanceUnits = Ed.INCH If you are using an Edison V1, then you must select Ed.TIME for the distance units: Ed.DistanceUnits = Ed.TIME 
```py linenums="0"
Ed.DistanceUnits = Ed.TIME
```

- Line 6 defines the built-in Edison variable which relates to how fast or slow Edison plays a musical tune. See the documentation section for the different speeds that can be set. 
```py linenums="0"
Ed.Tempo = Ed.TEMPO_MEDIUM
```

- Look at the character sets in the sample code that are written in all capitals, such as V1, V2, CM and INCH. In Python, the convention is that any variable name written in all caps is a ‘constant’. Constants are variables that maintain the same value everywhere in your program and are used as a reference point throughout the program. EdPy has a range of helpful built-in constants.  These are similar to pre-defined settings that our program will use with the Edison. 

### Instructional Code 
Lines 9-19 are telling the Edison to do something – giving the Edison instructions to perform.  Can you make a guess at what the Edison will do from reading the code? 

```py linenums="0"
#--------Your code below-----------
while True:
    Ed.PlayBeep()
    Ed.LeftLed(Ed.OFF)
    Ed.RightLed(Ed.ON)
    Ed.Drive(Ed.SPIN_RIGHT, Ed.SPEED_5, 350)
    Ed.TimeWait(20, Ed.TIME_MILLISECONDS)
    Ed.PlayBeep()
    Ed.LeftLed(Ed.ON)
    Ed.RightLed(Ed.OFF)
    Ed.Drive(Ed.SPIN_LEFT, Ed.SPEED_5, 350)
    Ed.TimeWait(20, Ed.TIME_MILLISECONDS)
```

Code is ideally written in a way that is understandable by reading it. The above code is a fairly decent example. 

## Task Attempt
Attempt [Task 1 - Intro to Edison](../tasks/task-1-intro-to-edison.md)