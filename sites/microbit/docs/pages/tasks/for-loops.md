# For Loop Tasks

## What does this do?

Read the code and guess what will happen. Then run it on the micro:bit and check your answer.

```python
from microbit import *

for i in range(3):
    display.show(str(i))
    sleep(500)
    display.clear()
    sleep(200)
```

## line of leds

!!! abstract "Instructions"
    Use a for loop to light up leds across the top of the display of the micro:bit.

??? hint "Hint:  click to expand"
    `set_pixel(x, y, brightness)` can be used to light up a specific led.  The x and y parameters specify the position of the led (0-4) and the brightness parameter specifies how bright the led should be (0-9).

## square of leds

!!! abstract "Instructions"
    Use for loops to light up all the leds on the display of the micro:bit.

## secret number game

!!! abstract "Instructions"
    Upgrade the game from the previous task.  Use a for loop to control the amount of guesses a player has before they lose the game (max of 10).  At the end of a game it will print whether the user has won or failed and the number of attempts that they used.
