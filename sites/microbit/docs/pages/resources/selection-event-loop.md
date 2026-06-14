# Selection in the Event Loop

We can do more interesting things if we combine what we know with the **event loop** and **selection**.

## Selection with the Buttons

We can run selection statements inside the event loop to get the micro:bit to respond to events. In the below example the micro:bit will keep checking for button A to be pressed. When button A is pressed it will play a beep sound. Remember that the loop runs continuously from the moment the program starts:

```python
from microbit import *
import music

while True:
    if button_a.is_pressed():
        music.pitch(440, 200)
        sleep(500)
        music.pitch(440, 200)
        sleep(500)
```

!!! note
    Here the micro:bit is constantly checking button A. When it detects a press it will execute the indented code underneath.

    `music.pitch(440, 200)` plays a tone at 440 Hz (the note A4) for 200 milliseconds. You can change the number to get a higher or lower pitch.

    Notice the indentation: the `if` statement is indented to indicate that it belongs to the `while` loop. The `music.pitch()` and `sleep()` calls are indented again to indicate that they belong to the `if` statement.

    This indentation is very important in Python as it dictates the structure of the code/program.

## Selection with Indentation

```python
from microbit import *
import music

while True:
    if button_a.is_pressed():
        music.pitch(440, 200)
        sleep(500)
    music.pitch(440, 200)
    sleep(500)
```

!!! note
    With a slight change to the program, we see completely different behaviour from the micro:bit.

    In this case the micro:bit will beep all the time because the last two lines (`music.pitch()` and `sleep()`) belong to the `while` loop, not the `if` statement. This means that on every loop / iteration those lines will always run.

## More Interactions

**Obstacle Detection (Distance Sensor)**

The micro:bit can read analog signals from its pins. Below is an example using an IR distance sensor connected to pin 1 — a low reading means something is close:

```python
from microbit import *
import music

while True:
    # Reads an analog signal from pin 1 (e.g. IR distance sensor)
    # A low reading (close to 0) means an obstacle is detected
    if pin1.read_analog() < 100:
        music.pitch(440, 200)
        sleep(200)
```

!!! note
    Connect an IR distance sensor to pin 1 and GND/3V on the edge connector. `pin1.read_analog()` returns a value from 0 to 1023. A low value means an obstacle is close. Inside the loop we check the sensor value every single iteration.

    Before you run this program, have a guess at what the micro:bit does when running it.

**Clap / Sound Sensing (micro:bit V2)**

```python
from microbit import *
import music

# Set the threshold for what counts as a "loud" sound (0-255)
microphone.set_threshold(SoundEvent.LOUD, 150)

while True:
    if microphone.was_event(SoundEvent.LOUD):
        music.pitch(440, 200)
        sleep(500)

    sleep(300)
```

!!! note
    `microphone.set_threshold(SoundEvent.LOUD, 150)` sets the sensitivity — higher values mean only very loud sounds will trigger it. `microphone.was_event(SoundEvent.LOUD)` checks whether a loud sound occurred since the last time it was called, and clears the history each time — similar to resetting the sensor each loop.

    **Note:** The built-in microphone is only available on the **micro:bit V2**.

**Light Levels**

```python
from microbit import *
import music

light_threshold = 150

while True:
    if display.read_light_level() > light_threshold:
        # Bright light detected — play a high-pitched tone
        music.pitch(1000, 200)
        sleep(500)

    sleep(500)
```

!!! note
    The micro:bit uses its LED display to read ambient light levels via `display.read_light_level()`, which returns a value from 0 (dark) to 255 (bright). The threshold value can be adjusted to suit your environment.

    Unlike the Edison which has separate left and right light sensors, the micro:bit has a single combined light sensor through the display. Two different pitches could be used to simulate different responses — try changing the frequency passed to `music.pitch()`.

**Random Numbers**

```python
from microbit import *
import random
import music

while True:
    num = random.randint(1, 4)

    if num == 1:
        display.scroll("F")   # Forward
        music.pitch(440, 300)
    elif num == 2:
        display.scroll("B")   # Backward
        music.pitch(330, 300)
    elif num == 3:
        display.scroll("L")   # Left
        music.pitch(550, 300)
    elif num == 4:
        display.scroll("R")   # Right
        music.pitch(660, 300)

    sleep(1500)

```
