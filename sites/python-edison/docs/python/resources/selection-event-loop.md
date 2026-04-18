# Selection in the Event Loop

We can do more interesting things if we combine what we know with the **event loop** and **selection**. 

## Selection with the Keypad
We can run selection statements inside the event loops to get the Edison to respond to events. In the below example the Edison will keep checking for the triangle button to be pressed. When the circle (round) button is pressed it will play a beep. Remember to start the actual program by pressing triangle first:

```py
#-------------Setup----------------

import Ed

Ed.EdisonVersion = Ed.V3

Ed.DistanceUnits = Ed.CM
Ed.Tempo = Ed.TEMPO_MEDIUM
#--------Your code below-----------

while True:
    if Ed.ReadKeypad() == Ed.KEYPAD_ROUND:
        Ed.PlayBeep()
        Ed.TimeWait(500, Ed.TIME_MILLISECONDS)
        Ed.PlayBeep()
        Ed.TimeWait(500, Ed.TIME_MILLISECONDS)
```

!!! note
    Here the Edison is constantly checking the Keypad, when it detects a press on the circle button it will execute the indented code underneath.

    Notice the indentation: `line 12` is indented to indicate that it belongs to the while loop on `line 11`. `Lines 13-16` is indented again to indicate that it belongs to the selection statement on `line 12`.

    This indentation is very important in Python as it dictates the structure of the code/program.

## Selection with Indentation
```py
#-------------Setup----------------

import Ed

Ed.EdisonVersion = Ed.V3

Ed.DistanceUnits = Ed.CM
Ed.Tempo = Ed.TEMPO_MEDIUM
#--------Your code below-----------

while True:
    if Ed.ReadKeypad() == Ed.KEYPAD_ROUND:
        Ed.PlayBeep()
        Ed.TimeWait(500, Ed.TIME_MILLISECONDS)
    Ed.PlayBeep()
    Ed.TimeWait(500, Ed.TIME_MILLISECONDS)     
```

!!! note
    With a slight change to the program at `line 15`, we see completely different behaviour from the Edison.

    In this case the Edison will beep all the time because `lines 15` and `16` belong to the while statement at `line 11`. This means that on every loop / iteration `lines 15` and `16` will run.

## More Interactions
### Obstacle Detection
```py
#-------------Setup----------------

import Ed

Ed.EdisonVersion = Ed.V3

Ed.DistanceUnits = Ed.CM
Ed.Tempo = Ed.TEMPO_MEDIUM
#--------Your code below-----------

Ed.ObstacleDetectionBeam(Ed.ON)

while True:
    if Ed.ReadObstacleDetection() == Ed.OBSTACLE_AHEAD:
        Ed.PlayBeep()
```

!!! note
    It's important for the **obstacle detection beam** to be turned **on** before we use it (`line 11`). Inside the loop we are checking the value of the beam every single iteration (`line 14`).

    Before you upload this program to the Edison, have a guess at what the Edison does when running this program.

### Clap Sensing
```py
#-------------Setup----------------

import Ed

Ed.EdisonVersion = Ed.V3

Ed.DistanceUnits = Ed.CM
Ed.Tempo = Ed.TEMPO_MEDIUM
#--------Your code below-----------
Ed.ReadClapSensor() 

while True:
    if Ed.ReadClapSensor() == Ed.CLAP_DETECTED:
        Ed.PlayBeep()
        Ed.TimeWait(500, Ed.TIME_MILLISECONDS)
    
    Ed.TimeWait(300, Ed.TIME_MILLISECONDS)
```

!!! note
    `Line 10` is used to clear the Edison of previous clap detections.

### Light Levels
```py
#-------------Setup----------------

import Ed

Ed.EdisonVersion = Ed.V3
Ed.DistanceUnits = Ed.CM
Ed.Tempo = Ed.TEMPO_MEDIUM

#--------Your code below-----------
light_level = 960

while True:
    if Ed.ReadRightLightLevel() > light_level:
        Ed.PlayMyBeep(1000)
        Ed.TimeWait(500, Ed.TIME_MILLISECONDS)
    elif Ed.ReadLeftLightLevel() > light_level:
        Ed.PlayMyBeep(8000)
        Ed.TimeWait(500, Ed.TIME_MILLISECONDS)
    
    Ed.TimeWait(500, Ed.TIME_MILLISECONDS)
```

### Random Numbers
```py
#-------------Setup----------------

import Ed

Ed.EdisonVersion = Ed.V3
Ed.DistanceUnits = Ed.CM
Ed.Tempo = Ed.TEMPO_MEDIUM

#--------Your code below-----------

while True:
    num = Ed.Random(1, 4)
    
    if num == 1:
        Ed.Drive(Ed.FORWARD, Ed.SPEED_5, 10)
    elif num == 2:
        Ed.Drive(Ed.BACKWARD, Ed.SPEED_5, 10)
    elif num == 3:
        Ed.Drive(Ed.SPIN_LEFT, Ed.SPEED_5, 90)
    elif num == 4:
        Ed.Drive(Ed.SPIN_RIGHT, Ed.SPEED_5, 90)
        
    Ed.TimeWait(1500, Ed.TIME_MILLISECONDS)
```