# Micro:bit Iteration (Event Loop)

## What is a Loop?

A **loop** is used to repeat code.

A common loop in MicroPython is:

```python
while True:
```

This means:

* Run the code forever
* The program keeps repeating until stopped

***

## Basic Event Loop Example

```python
from microbit import *

while True:
    display.show(Image.HEART)
    sleep(500)
    display.clear()
    sleep(500)
```

**What happens**

* The program shows a heart
* Waits
* Clears the screen
* Repeats forever

***

## How the Loop Works

Step-by-step:

1. The program enters the loop (`while True`)
2. Runs the code inside
3. Goes back to the top
4. Repeats again

This continues forever unless:

* The micro:bit is reset
* Power is removed

***

## Indentation (VERY IMPORTANT)

Python uses **indentation** to define what belongs inside the loop.

**Correct Example**

```python
from microbit import *

while True:
    display.show(Image.HAPPY)
    sleep(1000)
    display.show(Image.SAD)
    sleep(1000)
```

Both images repeat because they are **inside the loop**

***

**Incorrect Example**

```python
from microbit import *

while True:
    display.show(Image.HAPPY)

sleep(1000)
display.show(Image.SAD)
```

**What happens**

* `HAPPY` repeats forever
* `SAD` never runs

***

## Fix the Indentation

```python
from microbit import *

while True:
    display.show(Image.HAPPY)
    sleep(1000)
    display.show(Image.SAD)
    sleep(1000)
```

***

## Stopping the Loop

An event loop runs forever, but you can stop it by using a command:  *break*

```python
from microbit import *

count = 0

while True:
    count = count + 1
    if count < 10:
        print(count)
    else:
        break
```

!!! note
    In the above code, the loop will stop after counting to 10 because of the `break` statement.

***

## Combining Loops and Functions

We can call functions inside a loop.

```python
from microbit import *

def flash(times):
    for i in range(times):
        display.show(Image.HEART)
        sleep(200)
        display.clear()
        sleep(200)

while True:
    if button_a.is_pressed():
        flash(3)
```

**What happens?**

* The loop runs forever
* When button A is pressed → function runs

***

## Example: Random Behaviour

```python
from microbit import *
import random

def random_delay():
    return random.randint(1, 3)

def show_face(delay):
    display.show(Image.HAPPY)
    sleep(delay * 1000)

while True:
    d = random_delay()
    show_face(d)
```

**What happens?**

* A random number is generated
* The display shows for a random time
* Repeats forever

***

## Summary

Loops allow us to:

* Repeat actions continuously
* Create interactive programs
* Build event-driven systems

**Key Concepts**

* `while True:` → infinite loop
* Indentation → controls what repeats
* Functions → can run inside loops
* Inputs → (e.g. buttons) work well with loops

***

## Practice Ideas (Micro:bit)

1. Create a loop that:
    * Flashes a smiley face continuously

2. Create a program that displays "Hello <your name>"

***
