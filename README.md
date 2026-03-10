# GSL (Scripting Language)

GSL is a custom scripting language designed for general-purpose programming. It features a clean, C-like syntax with built-in support for variables, functions, control flow, lists, maps, and more.

---

## Installation

1. Ensure you have [.NET 8.0](https://dotnet.microsoft.com/download/dotnet/8.0) installed.
2. Run the Installer.

## Commands

All commands must be prefixed with `gsl`:

### Run a GSL Script
```
gsl gsp <filename>.gsl
```
Runs the specified GSL script file.

### Load a Custom Plugin
```
gsl lcsp <pluginname>
```
Loads a custom plugin from the `plugins/` folder.

### Download and Load a Plugin from URL
```
gsl pcsp <url> 
```
Downloads a plugin from a URL (supports Pastebin raw URLs, .gsl files, GitHub repositories, and .zip files) and loads it.

---

## Language Syntax

### Variables

```gsl
make x = 10           # Integer
make y = 3.14         # Float
make name = "Hello"   # String
make isTrue = true    # Boolean
make myList = pack[]  # Empty list
make myMap = {}       # Empty map
```

### Data Types

| Type    | Description                          | Example          |
|---------|--------------------------------------|------------------|
| `int`   | Integer numbers                      | `42`, `-10`      |
| `float` | Floating-point numbers               | `3.14`, `-0.5`   |
| `string`| Text strings                         | `"hello"`        |
| `bool`  | Boolean values (`true`/`false`)      | `true`, `false`  |
| `list`  | Ordered collections                  | `pack[1, 2, 3]`  |
| `map`   | Key-value pairs                      | `{ "key": val }` |
| `null`  | Null/empty value                     | `null`           |

### Comments

```gsl
# This is a single-line comment
```

### Control Flow

#### If/Else (Check)
```gsl
check condition {
    # code
}
check condition {
    # code
}
otherwise {
    # code
}
```

#### Loops

**While Loop (Spin)**
```gsl
spin condition {
    # code
}
```

**For Loop (Cycle)**
```gsl
cycle 10 {
    # runs 10 times
}
```

**For Each Loop**
```gsl
foreach item in myList {
    say item
}
```

### Functions

```gsl
craft myFunction(param1, param2) {
    make result = param1 + param2
    give result
}

# Call function
make x = myFunction(5, 3)
```

### Operators

| Operator | Description        |
|----------|--------------------|
| `+`      | Addition/Concat    |
| `-`      | Subtraction        |
| `*`      | Multiplication     |
| `/`      | Division           |
| `%`      | Modulo             |
| `==`     | Equality           |
| `!=`     | Not equal          |
| `<`      | Less than          |
| `>`      | Greater than       |
| `<=`     | Less or equal      |
| `>=`     | Greater or equal  |
| `&`      | Logical AND        |
| `|`      | Logical OR         |
| `!`      | Logical NOT        |

### Compound Assignment

```gsl
x += 5    # x = x + 5
x -= 3    # x = x - 3
x *= 2    # x = x * 2
x /= 4    # x = x / 4
```

### List Operations

```gsl
make lst = pack[1, 2, 3]
pushin lst 4          # Add to end: [1, 2, 3, 4]
make first = lst[0]    # Get first element
lst[0] = 10            # Set element
sizeof lst             # Get list length (3)
```

### Map Operations

```gsl
make m = {}
m["name"] = "John"
m["age"] = 25
make val = m["name"]
```

### Built-in Statements

| Statement    | Description                              |
|--------------|------------------------------------------|
| `make`       | Define a new variable                    |
| `say`        | Print to console with newline            |
| `pause`      | Sleep for specified seconds              |
| `pushin`     | Add element to list                      |
| `pullout`    | Remove element from list by index        |
| `give`       | Return value from function               |
| `stop`       | Break out of loop                        |
| `skip`       | Skip to next iteration                   |
| `link`       | Load a module/plugin                      |
| `check`      | If/else conditional                      |
| `spin`       | While loop                                |
| `cycle`      | For loop (count-based)                   |
| `foreach`    | For each loop                            |
| `craft`      | Define a function                         |

### Built-in Expressions

| Expression    | Description                              |
|---------------|------------------------------------------|
| `ask`         | Get user input from console              |
| `sizeof`      | Get length of list/string/map           |
| `kindof`      | Get type of value                        |
| `rand`        | Generate random number                   |

---

## Standard Library Functions

### I/O Functions (`std/io.gsl`)

| Function           | Description                          |
|--------------------|--------------------------------------|
| `print(val)`       | Print value to console               |
| `println(val)`    | Print value with newline             |
| `input()`          | Get user input                       |
| `input_int(p)`    | Get integer input with prompt        |
| `input_float(p)`   | Get float input with prompt          |
| `input_string(p)`  | Get string input with prompt         |
| `sleep(seconds)`   | Pause execution for seconds          |

### Math Functions (`std/math.gsl`)

| Function        | Description                          |
|-----------------|--------------------------------------|
| `abs(n)`        | Absolute value                       |
| `round(n)`      | Round to nearest integer             |
| `floor(n)`      | Floor value                          |
| `ceil(n)`       | Ceiling value                        |
| `max(a, b)`     | Maximum of two values                |
| `min(a, b)`     | Minimum of two values                |
| `clamp(v, lo, hi)` | Clamp value to range              |
| `pow(base, exp)` | Power (base^exp)                    |
| `sqrt(n)`       | Square root                          |
| `sign(n)`       | Sign of number (-1, 0, 1)            |
| `even(n)`       | Check if even                        |
| `odd(n)`        | Check if odd                         |
| `sum(list)`     | Sum of list elements                 |
| `average(list)` | Average of list elements             |
| `gcd(a, b)`     | Greatest common divisor              |
| `lcm(a, b)`     | Least common multiple                |
| `isprime(n)`    | Check if prime                       |
| `pi()`          | Returns Pi (3.14159)                 |
| `e()`           | Returns e (2.71828)                  |
| `mod(a, b)`     | Modulo operation                     |

### String Functions (`std/string.gsl`)

| Function              | Description                          |
|-----------------------|--------------------------------------|
| `repeat_str(s, n)`    | Repeat string n times                |
| `contains(s, sub)`    | Check if string contains substring  |
| `startswith(s, pre)`  | Check if starts with prefix          |
| `endswith(s, suf)`    | Check if ends with suffix            |
| `isempty(s)`          | Check if string is empty             |
| `str_reverse(s)`      | Reverse string                       |
| `str_count(s, ch)`    | Count occurrences of character      |
| `str_join(list, sep)` | Join list with separator            |
| `str_pad_left(s, w, c)` | Pad left with character           |
| `str_pad_right(s, w, c)` | Pad right with character          |
| `str_len(s)`          | Get string length                    |
| `str_concat(a, b)`    | Concatenate strings                  |
| `str_replace(s, o, n)` | Replace substring                  |
| `substring(s, start, len)` | Get substring                   |
| `split(s, delim)`     | Split string by delimiter            |
| `trim(s)`             | Remove leading/trailing whitespace  |
| `to_upper(s)`         | Convert to uppercase                |
| `to_lower(s)`         | Convert to lowercase                |

### List Functions (`std/list.gsl`)

| Function           | Description                          |
|--------------------|--------------------------------------|
| `list_get(l, i)`   | Get element at index                 |
| `list_first(l)`    | Get first element                    |
| `list_last(l)`     | Get last element                     |
| `list_contains(l, v)` | Check if list contains value    |
| `list_indexof(l, v)` | Get index of value               |
| `list_count(l, v)` | Count occurrences of value         |
| `list_sum(l)`      | Sum of all elements                  |
| `list_max(l)`      | Maximum element                      |
| `list_min(l)`      | Minimum element                      |
| `list_reverse(l)`  | Reverse list                         |
| `list_copy(l)`     | Copy list                            |
| `list_concat(a, b)`| Concatenate two lists                |
| `list_fill(v, n)`  | Create list with n copies of value  |
| `list_range(s, e)` | Create list from start to end        |
| `list_sort(l)`     | Sort list                            |
| `list_unique(l)`   | Remove duplicates                    |

### Type Functions (`std/type.gsl`)

| Function        | Description                          |
|-----------------|--------------------------------------|
| `to_int(val)`   | Convert to integer                   |
| `to_float(val)` | Convert to float                    |
| `to_string(val)`| Convert to string                    |
| `is_int(val)`   | Check if integer                     |
| `is_float(val)` | Check if float                       |
| `is_string(val)`| Check if string                      |
| `is_list(val)`  | Check if list                        |
| `is_bool(val)`  | Check if boolean                     |

---

## Example Code

### Hello World
```gsl
say "Hello, World!"
```

### Fibonacci Sequence
```gsl
craft fib(n)
{
    check n <= 1 {
        give n
    }
    give fib(n - 1) + fib(n - 2)
}

make i = 0
cycle 10 {
    say fib(i)
    i = i + 1
}
```

### List Manipulation
```gsl
make numbers = pack[5, 2, 8, 1, 9]
list_sort(numbers)
foreach n in numbers {
    say n
}
```

---


## License

The MIT License (MIT)
Copyright © 2026 <GSL TEAM>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
