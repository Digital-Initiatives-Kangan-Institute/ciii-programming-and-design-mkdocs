# Letters and Numbers

In programming, we often work with different types of data. The most common types are numbers and strings. Understanding these data types is essential for writing effective code.

There is distinction between letters (words) and numbers because if we want to perform calculations, we need to use numbers. If we want to work with text, we use strings.  For example, if we want to calculate the area of a rectangle, we need to use numbers for the length and width. If we want to display a message, we use strings.  Also the program can get confused if we're not specific about the data type.
For example, if we try to add a number and a string together, it will cause an error because they are different types of data.

```python
num1 = 5
num2 = "10"

result = num1 + num2  # This will cause an error because we cannot add a number and a string together

```

!!! note
    In the above code, `result1` is the sum of two numbers, while `result2` is the concatenation (joining) of two strings. This illustrates the difference between numbers and strings in Python.

***

## Data Types

In Python, a data type tells us what kind of value a variable holds. The most common data types are numbers (integers and floats) and strings (text).
Unlike some other languages, Python does not require you to declare the data type of a variable. The interpreter automatically determines the data type based on the value assigned to the variable.
In the code below, num1 and num2 are recognised as numbers because they are assigned number values. num3 and num4 are recognised as strings because they are assigned text values (even though they look like numbers, they are actually text because they are in quotes).

```python
num1 = 5
num2 = 10

num3 = "5"
num4 = "10"

result1 = num1 + num2
print(result1)  # This will print 15

result2 = num3 + num4
print(result2)  # This will print "510" because it joins the word "5" and "10""

```

!!! note
    A string is created by enclosing characters in quotes. It can contain letters, numbers, and symbols. Even if a string contains numbers, it is still treated as text and cannot be used for mathematical operations without conversion.

***

## Numbers - Integers and Floats

- **Integers** are whole numbers, like 1, -5, or 42.
- **Floats** are numbers with decimals, like 3.14 or -0.5.

Example:

```python
x = 7      # integer
y = 3.14   # float
```

***

## Strings

A string is a sequence of characters, like words or sentences. Strings are written in quotes.

Example:

```python
name = "micro:bit"
message = 'Hello!'
```

***

## Type Casting

Type casting means converting a value from one data type to another. This is useful when you need to work with user input or combine numbers and strings.

- **String to Integer**
  The `input()` function always returns a string. To use the value as a number, convert it with `int()`:

  ```python
  age_str = input("Enter your age: ")  # e.g., user types 12
  age = int(age_str)  # Now age is an integer
  print(age + 1)  # This will print 13
  ```

!!! note
    You'll often see string to integer conversion when working with user input, as the input is always treated as text. Converting it to an integer allows you to perform mathematical operations on it.

- **Integer to String**
  If you want to join a number with a string, convert the number to a string using `str()`:

  ```python
  score = 10
  message = "Your score is " + str(score)
  print(message)  # Output: Your score is 10
  ```

***

## String functions

Some useful string functions:

- `len(s)`: Returns the length of the string `s`.
- `s.upper()`: Converts all letters to uppercase.
- `s.lower()`: Converts all letters to lowercase.
- `s.replace(old, new)`: Replaces part of the string.

### Examples for Each String Function

- **len(s)**

  ```python
  text = "Hello, World!"
  print(len(text))  # Output: 13
  ```

- **s.upper()**

  ```python
  text = "Hello, World!"
  print(text.upper())  # Output: HELLO, WORLD!
  ```

- **s.lower()**

  ```python
  text = "Hello, World!"
  print(text.lower())  # Output: hello, world!
  ```

- **s.replace(old, new)**

  ```python
  text = "Hello, World!"
  print(text.replace("World", "micro:bit"))  # Output: Hello, micro:bit!
  ```

***

## Class Activity

Create a program that receives an input using the `input()` function.  provide

- Create a string with your name and print it in uppercase and lowercase.
- Ask the user for a sentence and print how many characters it has.
- Replace a word in a string with another word and print the result.
- Combine two strings (e.g., first name and last name) and print the full name.
