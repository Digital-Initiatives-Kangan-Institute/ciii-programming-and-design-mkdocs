
Here is the cleaned **Markdown version without emojis**, ready for classroom use:

***

# Loops with Conditions (micro:bit)

Previously, we used loops like `while True:` that run forever.

However, we can add a **condition** to a loop so it **stops when the condition is no longer true**. This makes it similar to an `if` statement, but it repeats.

***

## Example: Counter with a While Loop

```python
from microbit import *

count = 0
MAX_COUNT = 10

while count < MAX_COUNT:
    display.show(count)
    sleep(500)
    count = count + 1

display.clear()
```

***

**What is happening?**

* `count` starts at 0
* The loop runs while `count` is less than 10
* Each loop:
  * Displays the number
  * Waits 500ms
  * Increases `count` by 1
* Stops when `count` reaches 10

***

**Think About It**

* How many times does this loop run?
* What changes if we use:

```python
while count <= MAX_COUNT:
```

***

## Key Parts of a While Loop

To make a loop work correctly:

1. **Tracking variable**

    ```python
    count = 0
    ```

2. **Condition**

    ```python
    while count < MAX_COUNT:
    ```

3. **Update the variable**

    ```python
    count = count + 1
    ```

***

**Common Mistakes**

* If the variable never changes, the loop becomes infinite
* If the condition never becomes false, the loop never stops
* Incorrect update such as:

```python
count = count - 1
```

***

## Practice: How Many Times?

How many times will each loop run?

***

```python
count = 0

while count < 20:
    print(count)
    sleep(200)
    count = count + 1
```

***

```python
count = 0

while count <= 20:
    print(count)
    sleep(200)
    count = count + 1
```

***

```python
count = 1

while count < 20:
    print(count)
    sleep(200)
    count = count + 1
```

***

```python
count = 0

while count == 20:
    print(count)
    sleep(200)
    count = count + 1
```

***

```python
count = 0

while count < 20:
    print(count)
    sleep(200)
    count = count + 2
```

***

# For Loops (Better for Counters)

A **for loop** is often cleaner when you know how many times to repeat something.

***

## Example: Using a For Loop

```python
from microbit import *

MAX_COUNT = 10

for count in range(MAX_COUNT):
    display.scroll(count)
    sleep(1000)

display.clear()
```

***

## Why For Loops are Easier

* No need to create `count = 0`
* No need to manually increase it
* Automatically runs the correct number of times

***

## Understanding This Line

```python
for count in range(MAX_COUNT):
```

* `for` starts the loop
* `count` is the loop variable
* `in` is a required keyword
* `range(MAX_COUNT)` generates numbers from 0 to `MAX_COUNT - 1`

***

## Key Idea

**While loops** are best when you do not know how long the loop will run.  
**For loops** are best when you know the number of repetitions.
