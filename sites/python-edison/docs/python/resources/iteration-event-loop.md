# Iteration - Event Loop

## While Loop
You may have noticed that many of the example programs have contained a line with:
```py
while True: 
```

This is a loop.  A loop will run whatever is inside it until it meets a **false** condition. `while True:` is the same as saying `run forever` and will run until you stop the Edison.

Let's look at the syntax (structure) of a while loop – lines 11 and 12:
```py
#-------------Setup----------------

import Ed

Ed.EdisonVersion = Ed.V3

Ed.DistanceUnits = Ed.TIME
Ed.Tempo = Ed.TEMPO_MEDIUM

# --- Event loop -----
while True:
  Ed.PlayBeep()
```

If this code gets loaded onto the Edison it will play a beep sound, and keep playing it.   

1. The code enters at `line 11` and see that the `while` loop is `true`
2. It will then run `line 12` and play the beep
3. It will then come back up to `line 11` and once again see that the loop is `true`
4. It will then run `line 12` and play the beep
5. etc...

!!! abstract "Try it and see"
    Copy the code to EdPy and download it to your Edison. You will hear a droning sound instead of distinct beeps. Why?

We can also make the Edison continually drive:
```py
#-------------Setup----------------

import Ed

Ed.EdisonVersion = Ed.V3

Ed.DistanceUnits = Ed.CM
Ed.Tempo = Ed.TEMPO_MEDIUM

#--------Your code below-----------
Ed.ReadIRData()

while True:
    Ed.Drive(Ed.FORWARD, Ed.SPEED_3, 20)
```

## Python Syntax
Notice that the code underneath the event loop (`while True:`) is **indented**. This is how Python understands that the code below needs to be repeated. **Indentation** is used in Python to allow us to attach code to structures such as while loops. 

Indentation can either be created using the tab key or spaces, so long as they are consistent.

```py
#-------------Setup----------------

import Ed

Ed.EdisonVersion = Ed.V3

Ed.DistanceUnits = Ed.CM
Ed.Tempo = Ed.TEMPO_MEDIUM

#--------Your code below-----------
while True:
    Ed.Drive(Ed.FORWARD, Ed.SPEED_3, 10)
Ed.Drive(Ed.BACKWARDS, Ed.SPEED_3, 10)
```

In the above example we could expect the Edison to **move forward** by `10cm` and then **go backwards** `10cm`. What actually happens is that the Edison will **move forwards forever** and **never go backwards**. Why?

!!! abstract "Fix the indentation"
    Copy the above code into EdPy and fix it so that the Edison repeats cycles of move forward 10cm and goes backwards 10cm.

Of course, the event loop can be combined with what we've learnt previously (functions and variables):

```py
#-------------Setup----------------
import Ed

Ed.EdisonVersion = Ed.V3

Ed.DistanceUnits = Ed.CM
Ed.Tempo = Ed.TEMPO_MEDIUM
#--------Your code below-----------

# this function returns a number from one to six
def get_number():
    return Ed.Random(1, 3)
    
# beeping(num) will beep 'num' times
def beeping(num):
    Ed.PlayBeep()
    Ed.TimeWait(num, Ed.TIME_SECONDS)
        
while True:
    n = get_number()
    beeping(n)
```

In the above example the Edison will beep and pause for a random number of seconds between one and three. You can see from above that functions are being called from within the while loop.