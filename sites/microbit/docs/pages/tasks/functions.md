# Functions Tasks

## Show an Image Multiple Times

!!! abstract "Instructions"
    Complete the code below so that the micro:bit shows a heart image 3 times.

??? code "click to expand"
    ```python
    from microbit import *

    def show_heart_three():
       display.show(Image.HEART)
       sleep(500)
    
    show_heart_three()
    ```

## Run Function

!!! abstract "Instructions"
    Complete the code below so that it executes the function.

??? code "click to expand"
    ```python
    from microbit import *

    def show_square():
            display.show(Image.SQUARE)
            sleep(500)
            display.clear()
            sleep(500)
    ```

## Triangles

!!! abstract "Instructions"
    Fix the code below to show a triangle three times.

??? code "click to expand"
    ```python
    from microbit import *

    def show_triangle():
        display.show(Image.TRIANGLE)
        sleep(500)
        display.clear()
        sleep(500)
    
    show_triangle()
    show_triangle()
    ```

## Drawing a Square

!!! abstract "Instructions"
    The function draw_line(position) takes a position as a parameter and draws a line on the micro:bit display in that position.  Complete the code to draw lines that over time create a square.  The square will be drawn from *top* to *left* and then all the way around to the top again.  Valid arguments/parameters for the position are: "*top*", "*right*", "*bottom*" and "*left*".

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
