# Task 1 - Introduction to Edison
For each of the tasks below, **copy** the code into **EdPy** and follow the instructions.

## Analyse
!!! abstract "Instructions"
    By reading the code have a guess at what the Edison will do. 

    Download the code to your Edison and describe what the Edison does. Is it similar to what you guessed above? 

??? example "Code - Click to expand"
    Be mindful to maintain the lines and tabs (indentation) when pasting into the EdPy editor.

    ```py
    #-------------Setup----------------

    import Ed

    Ed.EdisonVersion = Ed.V3
    Ed.DistanceUnits = Ed.CM
    Ed.Tempo = Ed.TEMPO_MEDIUM

    #--------Your code below-----------

    Ed.Drive(Ed.FORWARD, Ed.SPEED_FULL, 30)

    Ed.Drive(Ed.SPIN_RIGHT, Ed.SPEED_1, 180)
    Ed.Drive(Ed.SPIN_LEFT, Ed.SPEED_1, 90)

    Ed.Drive(Ed.FORWARD, Ed.SPEED_FULL, 30)
    ```

## Spin Right
!!! abstract "Instructions"
    Edit the code so that the Edison only spins to the right. Program the Edison and test. 

## Increase Speed
!!! abstract "Instructions"
    Edit the code again so that the Edison spins faster. Program and observe the result. 