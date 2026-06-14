# Event Loop Tasks

## What does this do?

!!! abstract "Instructions"
    Read the code and guess what will happen. Then run it on the micro:bit and check your answer.

```python
from microbit import *

count = 0

while True:
    count = count + 1
    print(count)
    sleep(500)
```

## Modify the Event Loop

!!! abstract "Instructions"
    Modify the code so that it counts down from 10 to 0 instead of counting up. Run and check your answer.

## Create an event loop

!!! abstract "Instructions"
    Create an event loop that displays a happy face for 1 second, then a sad face for 1 second, and repeats forever.

## Function in an Event Loop

!!! abstract "Instructions"
    Move the code that displays the happy and sad faces into a function called `show_faces()`. Then call this function inside the event loop. Run and check your answer.

## Beeps

!!! abstract "Instructions"
    Modify the code to make the micro:bit beep every time it shows a happy face.  You can use `music.play(music.BA_DING)` to play a sound. Run and check your answer.

## print()

!!! abstract "Instructions"
    Modify the code again so that it prints "Happy!" when it shows a happy face and "Sad!" when it shows a sad face. Run and check your answer.
