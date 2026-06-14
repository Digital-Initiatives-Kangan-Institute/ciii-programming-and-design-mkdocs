# File Manipulation (Micro:bit Python - Online Editor) - PART 3

Up until now, our Micro:bit programs have run in the simulator and have not kept data once the program restarts. In standard Python, we can save data into files and read it back later. With the Micro:bit Python Editor online, we can still learn the _ideas_ behind file handling, but there are some important limitations.

!!!note
    Students using the online Micro:bit Python Editor do not have a physical micro:bit device, so they cannot use the micro:bit as a real storage device.  This means that there is some important functionality unavailable.  We cannot see changes that we make to files in the file editor nor _append_ to files.

In this topic, we are learning the syntax and logic of file handling in Python. On a real micro:bit, files would be stored on the device itself. In the online editor, file-related code may not behave exactly the same way, so the main goal is to understand how open(), write(), and read() work.

***

## File Modes

There are several file modes in Python:

- 'w': Write mode. Creates a file or overwrites an existing one.
- 'r': Read mode. Opens a file for reading.

In this course, we will focus on 'w' and 'r'.  We will simulate 'a' by making use of string manipulation.

???abstract "extra modes that we won't use - click to expand"
    - 'a': Append mode. Adds new content to the end of a file.
    - 'x': Exclusive creation mode. Creates a new file, but gives an error if the file already exists.

???abstract "What is append? - click to expand"
    Append mode is used when we want to add new content without deleting the old content.  Basically, it allows us to keep adding lines to the end of a file.  We will reproduct this behaviour by reading the contents of a file into a variable, then adding new text to that variable, and writing the whole thing back to the file.

***

## Reading from a File

To read from a file, we use open() with mode 'r' for read mode. This allows us to access the contents of the file.

```python
from microbit import *
from os import *

with open('main.py', 'r') as file:
    content = file.read()
    print(content) # Sends output directly to the simulated serial console
```

There are 3 notable things that we've not seen before.

1. _from os import_
2. _open('main.py', 'r') as file_
3. _with_

**from os import**
This line allows us to use file handling functions. In the online Micro:bit editor, this is necessary to access files. In a standard Python environment, you can read and write files without this import.

**open('main.py', 'r') as file**
This line does two things:

1. _open('main.py', 'r')_ - this opens the _main.py_ file in read mode ('r').
2. _as file_ - this store the content of _open_ in a variable called _file_.  Obviously, this _file_ variable could be called whatever we want, but _file_ is a common convention.
3. _with_ - this is a special syntax that ensures the file is properly closed after we're done with it.  It is a good practice to use _with_ when working with files because it handles closing the file for us, even if an error occurs.

!!!note
    We are opening the contents _main.py_ in this example.  That's not something normally done.  We're just doing that to show the functionality of opening a file and reading it.

***

## Writing to a File

To write to a file, we use open() with mode 'w' for write mode. This creates a new file or overwrites an existing one.

```python
from microbit import *
from os import *

# Open file in write mode ("w")
with open("myfile.txt", "w") as file:
    # Write text into the file
    file.write("Hello Minh's class!\n")
    file.write("Another line of text.\n")

```

**file = open("myfile.txt", "w")** - this opens the file in write mode. If the file does not exist, it will be created. If it already exists, it will be overwritten.
**file.write("Hello Minh's class!\n")** - this writes the specified text into the file.

!!!note
    The file _myfile.txt_ will be created but not viewable in the files list in the micro:bit online editor.  This is a limitation of the online editor.  In a real Python environment, you would be able to see the file in the directory.  We will be able to see it programmatically by reading from it (next section).

!!!note
    The \\n means newline. It tells Python to start the next text on a new line.

Writing again to the file will _overwrite_ the contents of the file:

```python
from microbit import *
from os import *

with open("myfile.txt", "w") as file:
    # Write text into the file
    file.write("Hello Minh's class!\n")
    file.write("Another line of text.\n")

with open('myfile.txt', 'w') as file:
    file.write('Goodbye, Micro:bit!')

with open('myfile.txt', 'r') as file:
    content = file.read()
    print(content) # This will print "Goodbye, Micro:bit!" and the previous lines will be lost
```

***

## Viewing files in the current directory

We can view files in the current directory using listdir() from the os module.

append the following code to the file writing code from the previous section:

```python
all_files = listdir()
print(all_files)
```

You will see a list of files in the current directory, which should include main.py and myfile.txt (if it was created successfully).  This is a way to confirm that the file was created, even though we cannot see it in the file editor.

Now go to the file editor and create a new file called _temp.py_.  If you run the code again, you should see temp.py in the list of files.  This is a way to confirm that the file was created, even though we cannot see it in the file editor.

!!!note
    We are creating a _.py_ file due to limitations of the online editor.  In a real Python environment, you could create any type of file.

***

## "Appending" to a file

Appending means adding new content to the end of a file without deleting the existing content.  In Python, we can use mode 'a' to append to a file. However, in the online Micro:bit editor, this functionality is not available.  Instead, we can simulate appending by reading the existing content of the file into a variable, adding new text to that variable, and then writing the whole thing back to the file.

```python
from microbit import *
from os import *

with open("myfile.txt", "w") as file:
    # Write text into the file
    file.write("Hello Minh's class!\n")
    file.write("Another line of text.\n")

# append new text by reading the existing content, adding new text, and writing it back
content = ""

with open("myfile.txt", "r") as file:
    content = file.read()

with open("myfile.txt", "w") as file:
    file.write(content)  # write the existing content back to the file
    file.write("This is new text that simulates appending.\n")  # add new text
# end of the append simulation

# read contents after the new write to confirm that the new text was added
with open("myfile.txt", "r") as file:
    content = file.read()
    print(content) # This will show the original lines plus the new line that simulates appending

```

***

## Class Activities

**Task:**

- Write a file called example.txt
- Add this message:
  - _Hello students!_

***
**Task:**

- Use your previous file
- Print all contents

***

**Task:**

- Create a file using 'w'
- Add:
  - Line 1: _My favourite food is BanhMi._

- Use appending to add the following lines:
  - Line 2: _I also like KFC._
  - Line 3: _Ice cream is great too._

***

**Task:**

- Use your previous file
- Print all contents
