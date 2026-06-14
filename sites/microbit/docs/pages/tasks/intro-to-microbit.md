# Introduction to micro:bit Tasks

## Analyse

!!! abstract "Instructions"
    By reading the code, guess what the micro:bit will do. Then run the code and describe what happens. Is it similar to your guess?

??? code "click to expand"
     Be mindful to maintain the lines and tabs (indentation) when pasting into the micro:bit editor.
    ```python
    from microbit import *

    # Your code below
    display.show(Image.HEART)
    sleep(1000)
    display.show(Image.HAPPY)
    sleep(1000)
    display.clear()
    ```

## Show Only One Image

Edit the code so that the micro:bit only shows the heart image. Run and test.

## Increase Speed

Edit the code again so that the images change faster. Run and observe the result.

## Use print()

In addition to displaying the images on the LED display.  Print the corresponding words (Heart and Happy) to the serial console.
