
# Micro:bit Functions (MicroPython)

## What are Functions?

Functions are a core concept of programming.

*Functions allow us to:*

- Group code together
- Give that code a name
- Reuse code instead of rewriting it

*This makes programs:*

- Easier to read
- Easier to debug
- Easier to build in parts

You can think of a function as a **mini-program** inside your main program.

---

## Calling a Function

Calling a function means **running the code inside it**.

We already use built-in functions on the micro:bit, for example:

```python
from microbit import *

display.scroll("Hello")
```

Here, `display.scroll()` is a **built-in function**.

Functions always use **parentheses `()`**.

***

## Defining a Function

We can create our own functions using `def`.

**Syntax**

```python
def function_name():
    # code to run
```

**Example**

```python
from microbit import *

def small_dance():
    display.show(Image.HAPPY)
    sleep(500)
    display.show(Image.SAD)
    sleep(500)
    display.show(Image.HAPPY)
    sleep(500)

def show_heart():
    display.show(Image.HEART)
    sleep(1000)

# Call the functions
small_dance()
show_heart()
small_dance()
```

Here we created two functions of our own *small_dance* and *show_heart*.  
We can then run these as many times as we like by calling them. This is much easier than writing the same code multiple times.  

**Key Idea**

Functions are often used to gather together code that we want to reuse. This makes our program more efficient and easier to read.
We write the function **once**, but can call it **many times**.  

***

## Parameters (Inputs)

Functions can take inputs called **parameters**.  A parameter is a variable that we pass into the function when we call it.  Just like a normal variable we can use it inside the function by calling its name.

This makes them more flexible.

**Syntax**

```python
def function_name(parameter1, parameter2):
    # code using parameters
```

**Example**

```python
from microbit import *

def scroll_message(message):
    display.scroll(message)

def flash_icon(icon, delay):
    display.show(icon)
    sleep(delay)
    display.clear()
    sleep(delay)

scroll_message("Hi")
scroll_message("Microbit")

flash_icon(Image.HEART, 500)
flash_icon(Image.SQUARE, 200)
```

**Key Idea**

Parameters let you **reuse the same function with different values**.

***

## Returning Values (Output)

Functions can send a value back using `return`.

This allows us to **store or use the result**.

***

**Example 1: Returning a Value**

```python
from microbit import *

def add_nums(a, b):
    return a + b

result = add_nums(5, 13)
print(result)

display.scroll(result)
```

***

**Example 2: Custom Function with Return**

```python
from microbit import *

def is_even(number):
    return number % 2 == 0

if is_even(4):
    display.show(Image.YES)
else:
    display.show(Image.NO)
```

***

## Summary

Functions help us:

- Organise code into reusable blocks
- Avoid repetition
- Make programs easier to understand

**Key Concepts**

- `def` → define a function
- `()` → call a function
- Parameters → inputs
- `return` → output

***

## Class Activity (demo)

1. Create a function that:
    - Flashes a heart 3 times

2. Create a function with a parameter:
    - Display any message passed in

3. Create a function that:
    - Takes a number and returns double the value

4. Extension:
    - Use a button press to trigger your function
