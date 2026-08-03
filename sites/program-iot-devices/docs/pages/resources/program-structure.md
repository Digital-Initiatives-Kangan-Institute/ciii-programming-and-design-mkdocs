# Program Structure and Execution

---

## Program Structure

Every program written with the Arduino framework — regardless of which board it runs on — has exactly two required functions:

```cpp
void setup() {
  // Runs ONCE when the board powers on or resets
  // Used to configure pins, start Serial, initialise components
}

void loop() {
  // Runs REPEATEDLY after setup() finishes
  // Contains the main program logic
}
```

A sketch (Arduino's term for a program file) is built from four parts, always in this order:

1. **Library includes** (`#include`) — optional
2. **Global variable declarations** — optional but common
3. **`setup()`** — required, runs once
4. **`loop()`** — required, runs forever

---

### `setup()`

- Called exactly **once**, right after the board powers on or is reset (e.g. pressing the reset button, opening the Serial Monitor, or re-uploading code).
- This is where you do **one-time configuration**:
    - `pinMode()` — declare each pin as `INPUT` or `OUTPUT`
    - `Serial.begin()` — open the serial connection
    - Initialising sensor/library objects (e.g. `dht.begin()`, `servo.attach()`)
    - Setting starting values for variables
- Takes no parameters — `()` is empty because the framework calls it with nothing.

---

### `loop()` in detail

- Called **repeatedly**, forever, immediately after `setup()` finishes.
- Each pass through `loop()` is one "cycle" of your program — this is effectively the `PROCESS` and `OUTPUT` stages from the Input → Process → Output pattern.
- There's no way to "exit" `loop()` and go back to `setup()` — the only way `setup()` runs again is a physical reset or re-upload.
- Because it runs continuously, anything with `delay()` inside blocks the *entire* board — no other code runs during that pause.

---

### Where variables and includes fit

- `#include` statements must come **before** they're used, so by convention they go at the very top of the file.
- Global variables (declared outside `setup()`/`loop()`) are visible in **both** functions — that's why a pin number declared at the top can be used in `setup()` for `pinMode()` and reused anywhere in `loop()`. Variables declared *inside* `setup()` or `loop()` are local and disappear once that function call ends (though `setup()`'s locals only matter once, and `loop()`'s locals are recreated every cycle).

---

### Common mistakes

- Forgetting `void` or misspelling `setup`/`loop` (e.g. `Setup()`) — the compiler won't find the required functions and errors out.
- Putting `pinMode()` in `loop()` instead of `setup()` — it still works, but wastefully reconfigures the pin thousands of times per second.
- Doing one-time work (like printing a start-up banner) inside `loop()` — it'll print repeatedly instead of once.

---

## The Serial Monitor

The Serial Monitor is a tool in the Arduino IDE that lets you send and receive text between your board and your computer. It is useful for testing and debugging.

```cpp
Serial.begin(115200);       // Start serial communication (in setup) — pick a baud rate and use it consistently
Serial.println("Hello!");   // Print a line of text
Serial.print(temperature);  // Print a value without a new line
```

> **Note:** The baud rate is up to you, as long as the Serial Monitor is set to the same value. `9600` is a common default on Uno/Nano-family boards; `115200` is common on ESP32/ESP8266 and other faster boards.

---

## Example: Device Start-Up Message and LED Blink

This program prints a start-up message to the Serial Monitor and blinks the built-in LED to confirm the device is running.

```cpp
int ledPin = LED_BUILTIN;   // LED_BUILTIN automatically maps to the correct pin for your specific board
String deviceName = "IoT-Device-01";

void setup() {
  Serial.begin(115200);                    // Start serial communication (match this to your Serial Monitor's baud rate)
  pinMode(ledPin, OUTPUT);                 // Set LED pin as output

  Serial.println("=== Device Starting ===");
  Serial.print("Device name: ");
  Serial.println(deviceName);
  Serial.println("Status: ONLINE");
  Serial.println("=======================");
}

void loop() {
  digitalWrite(ledPin, HIGH);              // LED on
  Serial.println("LED: ON");
  delay(1000);

  digitalWrite(ledPin, LOW);              // LED off
  Serial.println("LED: OFF");
  delay(1000);
}
```

### Code Walkthrough

| Line | Explanation |
|------|-------------|
| `int ledPin = LED_BUILTIN;` | Declares a variable holding the board's built-in LED pin number |
| `String deviceName = "IoT-Device-01";` | Declares a String variable for the device name |
| `Serial.begin(115200)` | Opens a serial connection at 115200 bits per second — must match the Serial Monitor's baud rate |
| `pinMode(ledPin, OUTPUT)` | Configures the built-in LED pin as an output |
| `Serial.print()` | Prints text without a new line at the end |
| `Serial.println()` | Prints text and moves to a new line |
| `void loop()` | Everything inside runs continuously |

---

## Guided Build: Step by Step

Open this Wokwi simulation: [https://wokwi.com/projects/470517127243328513](https://wokwi.com/projects/470517127243328513)

Build the same program step by step.

### Step 1 — Declare your variables

```cpp
int ledPin = 13;
String deviceName = "MyIoTDevice";
```

### Step 2 — Write the `setup()` function

```cpp
void setup() {
  Serial.begin(115200);
  pinMode(ledPin, OUTPUT);
  Serial.println("Device is starting...");
  Serial.print("Name: ");
  Serial.println(deviceName);
}
```

### Step 3 — Write the `loop()` function

```cpp
void loop() {
  digitalWrite(ledPin, HIGH);
  Serial.println("ON");
  delay(500);

  digitalWrite(ledPin, LOW);
  Serial.println("OFF");
  delay(500);
}
```

### Step 4 — Upload and open the Serial Monitor

---

## Vocabulary

| Term | Definition |
|------|-----------|
| Input → Process → Output | The three-stage pattern every IoT program follows — read data, make a decision, act on the result |
| Variable | A named storage location that holds a value in memory |
| Data type | Specifies what kind of value a variable can hold (e.g., int, float, bool) |
| `int` | Integer — stores whole numbers |
| `long` | Stores whole numbers larger than `int`'s range allows |
| `float` | Floating point — stores decimal numbers |
| `double` | Stores decimal numbers; same precision as `float` on most Arduino boards, more precise on ARM/Xtensa boards |
| `char` | Stores a single character, held internally as an ASCII code |
| `String` | Stores a sequence of characters (text) |
| `bool` | Boolean — stores true or false |
| `byte` | Stores small positive whole numbers, 0 to 255 |
| Reserved word | A word the Arduino language already uses (e.g. `int`, `void`, `if`) that can't be used as a variable name |
| camelCase | Naming style for variables — first word lowercase, each following word capitalised (e.g. `ledPin`) |
| UPPER_CASE | Naming convention for constants, words separated by underscores (e.g. `MAX_SPEED`) |
| Scope | Determines where in the code a variable can be accessed — global or local |
| Global variable | Declared outside all functions; accessible everywhere and keeps its value for the program's entire runtime |
| Local variable | Declared inside a function or block; only accessible there and destroyed once it ends |
| Constant | A variable whose value is locked at declaration and can never be changed |
| `const` | Keyword used to declare a constant (e.g. `const int LED_PIN = 13;`) |
| `#define` | Alternative way to define a constant by text substitution before compiling; not type-checked like `const` |
| Comment | Text in code that is ignored by the compiler, used to explain the code |
| Commenting out | Temporarily disabling a line of code by turning it into a comment, without deleting it |
| `#include` | Imports a library into the program |
| Sketch | Arduino's term for a program file |
| `setup()` | Arduino function that runs once at start-up |
| `loop()` | Arduino function that runs continuously |
| `pinMode()` | Configures a pin as `INPUT` or `OUTPUT`, usually called in `setup()` |
| `digitalWrite()` | Sets a digital pin `HIGH` or `LOW`, e.g. to turn an LED on or off |
| `LED_BUILTIN` | Built-in constant that automatically points to the correct onboard LED pin for your specific board |
| Serial Monitor | Tool in the Arduino IDE for sending/receiving text over USB |
| Baud rate | The speed of serial communication, set with `Serial.begin()` and must match the Serial Monitor's setting |
| Compile | The process of converting code into instructions the microcontroller can execute |
