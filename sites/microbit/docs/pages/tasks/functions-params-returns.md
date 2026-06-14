# Functions, Parameters, and Returns Tasks

## Using Parameters

!!! abstract "Instructions"
    The function show_image(image, delay) takes an image and a delay as parameters.  Complete the code to show the image for the specified amount of time.j
Read the code and guess what will happen. Then run it on the micro:bit and check your answer.

```python
from microbit import *

def show_image(image, delay):
    display.show(image)
    sleep(delay)
    display.clear()

show_image(Image.HEART, 1000)
show_image(Image.HAPPY, 500)
```

## Drawing a Square

!!! abstract "Instructions"
    The function draw_line(position) takes a position as a parameter and draws a line on the micro:bit display in that position.  Complete the code to draw lines that over time create and square.  The square will be drawn from *top* to *left* and then all the way around to the top again.  Valid arguments/parameters for the position are: "*top*"", "*right*", "*bottom*" and "*left*".

??? code "click to expand"
    ```python
    from microbit import *

    def draw_line(position):
        if position == "top":
            display.show(Image(
                            '99999:'
                            '00000:'
                            '00000:'
                            '00000:'
                            '00000'))
        
        elif position == "right":
            display.show(Image(
                            '00009:'
                            '00009:'
                            '00009:'
                            '00009:'
                            '00009'))
        
        elif position == "bottom":
            display.show(Image(
                            '00000:'
                            '00000:'
                            '00000:'
                            '00000:'
                            '99999'))
        
        elif position == "left":
            display.show(Image(
                            '90000:'
                            '90000:'
                            '90000:'
                            '90000:'
                            '90000'))
        
        else:
            print("Invalid position")
    
    # call functions here:
    ```

## Create a Function with Return Value

!!! abstract "Instructions"
    The function get_message() returns a string message.  Complete the code to return a custom message and display it on the micro:bit.
Write a function that returns a custom message. Display the message on the micro:bit.

## Beeping

!!! abstract "Instructions"
    Call the beeping function so that the micro:bit beeps 5 times.

??? example "Code - Click to expand"
    ```python
    from microbit import *
    import music

    # beeping(num) will beep 'num' times
    def beeping(num):
        for i in range(num):
            music.pitch(880, 200)  # Play a beep sound
            sleep(300)

    # call the beeping function to make micro:bit beep 5 times    
    ```

## Using Returns

!!! abstract "Instructions"
    As stated in the comment in the code, use the returned value from the get_number() function as the parameter for the beeping(num) function.  This will make the micro:bit beep a random number of times between one and six.

??? example "Code - Click to expand"
    ```python
    from microbit import *
    import music
    import random

    # this function returns a number from one to six
    def get_number():
        return random.randint(1, 6)

    # beeping(num) will beep 'num' times
    def beeping(num):
        for i in range(num):
            music.pitch(880, 200)
            sleep(300)

    #---------------
    # run get_number() and use the returned value in the beeping(num) function
    ```
