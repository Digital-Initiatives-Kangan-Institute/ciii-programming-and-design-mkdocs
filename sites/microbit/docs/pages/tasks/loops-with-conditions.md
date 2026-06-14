# Loops with Conditions Tasks

## What does this do?

Read the code and guess what will happen. Then run it on the micro:bit and check your answer.

```python
from microbit import *

for i in range(5):
    if i % 2 == 0:
        display.show(Image.HEART)
    else:
        display.show(Image.HAPPY)
    sleep(500)
    display.clear()
    sleep(200)
```

## Modify the Loop

Change the code to use a different range or condition.

## Create a Simple Game

!!! abstract "Instructions"
    Create a simple game where the user has to guess a number between 1 and 100.  Use selection to provide feedback on whether the guess is too low, too high, or correct.  The secret number is 42.

## Expand the Game

!!! abstract "Instructions"
    Make the game better by using the random module to create the secret number.

## Last addition

!!! abstract "Instructions"
    Add a counter to keep track of how many guesses the user has made and display it when they guess the correct number.
