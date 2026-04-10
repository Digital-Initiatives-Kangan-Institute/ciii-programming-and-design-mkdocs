# Task 1 - Introduction to Edison
## Analyse
Copy the below code into EdPy. By reading the code have a guess at what the Edison will do. 

Download the code to your Edison and describe what the Edison does. Is it similar to what you guessed above? 

```py
#-------------Setup----------------
import Ed 
 
Ed.EdisonVersion = Ed.V3 
 
 
Ed.DistanceUnits = Ed.CM 
Ed.Tempo = Ed.TEMPO_MEDIUM 
 
 
#--------Your code below----------- import Ed

Ed.EdisonVersion = Ed.V3
Ed.DistanceUnits = Ed.CM
Ed.Tempo = Ed.TEMPO_MEDIUM

#--------Your code below-----------

song=Ed.TuneString(23, "c4,d6,e7,g4,f2")


while True: 
    Ed.PlayBeep() 
    Ed.LeftLed(Ed.OFF) 
    Ed.RightLed(Ed.ON) 
    
#    Ed.Drive(Ed.SPIN_RIGHT, Ed.SPEED_5, 350) 
#    Ed.TimeWait(20, Ed.TIME_MILLISECONDS) 
#    Ed.PlayBeep() 
#    Ed.LeftLed(Ed.ON) 
#    Ed.RightLed(Ed.OFF) 
#    Ed.Drive(Ed.SPIN_LEFT, Ed.SPEED_5, 350) 
#    Ed.TimeWait(20, Ed.TIME_MILLISECONDS) 
    Ed.Drive(Ed.FORWARD, 10, 20)
    Ed.Drive(Ed.SPIN_RIGHT, Ed.SPEED_5, 90)
    Ed.PlayBeep() 
    Ed.PlayTune(song)
#    while Ed.ReadMusicEnd() == Ed.MUSIC_NOT_FINISHED:
#        pass
    Ed.Drive(Ed.FORWARD, 10, 10)
    Ed.Drive(Ed.SPIN_RIGHT, Ed.SPEED_5, 90)
    Ed.PlayBeep() 
    Ed.PlayTune(song)
#    while Ed.ReadMusicEnd() == Ed.MUSIC_NOT_FINISHED:
#        pass
    Ed.Drive(Ed.FORWARD, 10, 20)
    Ed.Drive(Ed.SPIN_LEFT, Ed.SPEED_5, 90)
    Ed.PlayBeep() 
    Ed.PlayTune(song)
#    while Ed.ReadMusicEnd() == Ed.MUSIC_NOT_FINISHED:
#        pass
    Ed.Drive(Ed.FORWARD, 10, 10)
    Ed.Drive(Ed.SPIN_LEFT, Ed.SPEED_5, 90)
    Ed.PlayBeep()  
    Ed.PlayTune(song)
#    while Ed.ReadMusicEnd() == Ed.MUSIC_NOT_FINISHED:
#        pass
    Ed.Drive(Ed.FORWARD, 10, 20)
    Ed.Drive(Ed.SPIN_RIGHT, Ed.SPEED_5, 90)
    Ed.PlayBeep() 
    Ed.PlayTune(song)
#    while Ed.ReadMusicEnd() == Ed.MUSIC_NOT_FINISHED:
#        pass
    Ed.Drive(Ed.FORWARD, 10, 10)
    Ed.Drive(Ed.SPIN_RIGHT, Ed.SPEED_5, 90)
    Ed.PlayBeep()  
    Ed.PlayTune(song)
#    while Ed.ReadMusicEnd() == Ed.MUSIC_NOT_FINISHED:
#        pass
```

Be mindful to maintain the lines and tabs (indentation) when pasting into the EdPy editor 

## Spin Right
Edit the code so that the Edison only spins to the right.  Program the Edison and test. 

## Increase Speed
Edit the code again so that the Edison spins faster.  Program and observe the result. 