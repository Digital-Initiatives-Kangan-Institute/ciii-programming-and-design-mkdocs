# Strings

As covered in the data types section, a string is a sequence of characters. Strings can be manipulated using various built-in functions and methods in Python.

## String functions

Some useful string functions:

- `len(s)`: Returns the length of the string `s`.
- `s.upper()`: Converts all letters to uppercase.
- `s.lower()`: Converts all letters to lowercase.
- `s.replace(old, new)`: Replaces part of the string.

## len(s)

  ```python
  text = "Hello, World!"
  print(len(text))  # Output: 13
  ```

## s.upper()

  ```python
  text = "Hello, World!"
  print(text.upper())  # Output: HELLO, WORLD!
  ```

## s.lower()

  ```python
  text = "Hello, World!"
  print(text.lower())  # Output: hello, world!
  ```

## s.replace(old, new)

  ```python
  text = "Hello, World!"
  print(text.replace("World", "micro:bit"))  # Output: Hello, micro:bit!
  ```
