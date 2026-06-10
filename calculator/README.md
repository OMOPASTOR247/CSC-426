# CSC426 Calculator (Java Swing)

A GUI calculator built with Java Swing for the CSC426 weekly dev exercise.

## What it does

The whole expression you type is shown in the display, and the answer is added
after you press `=`. For example, typing `2 + 4 - 93` and pressing `=` shows:

```
2+4-93=-87
```

Supported keys:

| Button  | Operation                  |
|---------|----------------------------|
| `+`     | Addition                   |
| `-`     | Subtraction                |
| `*`     | Multiplication             |
| `/`     | Division                   |
| `\`     | Integer (floor) division   |
| `^`     | Exponentiation (power)     |
| `%`     | Modulo (remainder)         |
| `Clear` | Clear everything           |
| `<-`    | Backspace (delete a digit) |
| `.`     | Decimal point              |
| `=`     | Evaluate the expression    |

Notes:

* Expressions follow normal operator precedence, so `2 + 3 * 4` gives 14, and
  `^` is evaluated right to left, so `2 ^ 3 ^ 2` gives 512.
* Division and modulo by zero show `Error` instead of crashing.
* Whole number answers are shown without a trailing `.0`.
* The keyboard works too: type the digits and operators, press Enter to evaluate,
  Backspace to delete, and Esc to clear.

## Requirements

JDK 17 or newer. It was checked on OpenJDK 21.

## Build and run

```bash
javac Calculator.java
java Calculator
```

On Java 11 and above you can also run it without compiling first:

```bash
java Calculator.java
```

## How it works

Key presses build up an expression string that is shown in the display. When you
press `=`, a small recursive descent parser reads that string and evaluates it
with the correct precedence: `+` and `-` first at the lowest level, then
`*`, `/`, `\` and `%`, then `^` at the highest level. The result is shown after
an equals sign, and it also becomes the starting value if you carry on with
another operator.
