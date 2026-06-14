# Lists Tasks

## What does this do?

!!! abstract "Instructions"
    Read the code and guess what will happen. Then run it on the micro:bit and check your answer.

```python
from microbit import *

values = [1, 2, 3, 4, 5]
for value in values:
    display.scroll(str(value))
    sleep(200)
```

## Modify the List

!!! abstract "Instructions"
    Add more values to the list and observe the result.

## List Operations

!!! abstract "Instructions"
    Try using `append()` to add a value and `pop()` to remove one.

## Buttons

!!! abstract "Instructions"
    Create a program that uses buttons A and B.  Every time a button is pressed, the corresponding letter is added to a list.  When both buttons are pressed together, the contents of the list are displayed on the screen and printed to the serial.

## Secret Number game upgrade

!!! abstract "Instructions"
    Upgrade the secret number game from the previous task.  Use a list to keep track of the user's guesses and print them at the end of the game.
