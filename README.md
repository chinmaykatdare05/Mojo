# MOJO

## Variable Assignment

- `let` - runtime, immutable
- `var` - runtime, mutable
- `alias` - compile time, immutable

## Data Types

- `string`, `int`, `float`, `bool`, `uint`
- `int` -> `int8`, `int16`, `int32`, `int64` (default)
- `uinit` -> same as `int`
- `float` -> same as `int` (`float16` is useful/better)

## Input

```mojo
from python import Python

fn main() raises:
  let py = Python.import_module('builtins')
  let user_input = py.input('What is your favourite colour? ')
  print('Your favourite colour is:', user_input)
```

### Array

```mojo
from python import PythonObject

fn main() raises:
  let x: PythonObject = [1, 2, 3, 4, 5]
  for i in range(x.__len__()):
    print(x[i])
```

### Function

```mojo
fn add(x: Int, y: Int) -> Int:
  let c: Int = x + y
  return c

fn main():
  let x: Int = add(2, 5)
  print(x)
```

### Classes

```mojo
struct Banana:
  var Rype: Bool
  var Length: Float32
  var Color: String

  fn __init__(inout self, Rype: Bool, Length: Float32, Color: String):
    self.Rype = Rype
    self.Length = Length
    self.Color = Color

  fn rype(self, rhs: Banana) -> Bool:
    return self.Rype

  fn length(self, rhs: Banana) -> Float32:
    return self.Length

  fn color(self, rhs: Banana) -> String:
    return self.Color

fn main():
  let banana = Banana(False, 4.7, 'yellow')
  print(banana.rype(banana))
```

### Modules

```mojo
from python import Python

fn main() raises:
  let math = Python.import_module('math')
  let sqrt = math.sqrt(4)
  print(sqrt)
```

### Error Handling

```mojo
raises, try, except, finally
```

### Special Keywords

- `inout`: Reads and mutates the original value directly, like lending a pen with permission to edit.
- `borrowed`: Reads the original value only, like borrowing a book to admire but not write in.
- `owned`: Takes exclusive control, like receiving a gift you can modify or discard at will.

### SIMD

```mojo
fn main():
  let x = SIMD[DType.float16, 4](1, 4, 9, 16)
  print(x*2)
```
