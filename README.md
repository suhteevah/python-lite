# python-lite

[![no_std](https://img.shields.io/badge/no__std-compatible-brightgreen)](https://docs.rs/python-lite)
[![Crates.io](https://img.shields.io/crates/v/python-lite)](https://crates.io/crates/python-lite)
[![License](https://img.shields.io/crates/l/python-lite)](LICENSE-MIT)

A minimal Python interpreter written in Rust. Works in `no_std` environments
(with `alloc`) -- designed for embedded systems, bare-metal OS kernels, and
WebAssembly.

Extracted from [ClaudioOS](https://github.com/suhteevah/claudio-os), a
bare-metal Rust operating system that runs AI coding agents directly on
hardware with no Linux kernel.

## Features

### Data Types
- **int** -- 64-bit signed integers with overflow checking
- **float** -- 64-bit IEEE 754 floating point
- **str** -- UTF-8 strings with escape sequences
- **bool** -- `True` / `False`
- **list** -- dynamic arrays with negative indexing
- **None**

### Operators
- Arithmetic: `+`, `-`, `*`, `/`, `//` (floor div), `%`, `**` (power)
- Comparison: `==`, `!=`, `<`, `>`, `<=`, `>=`
- Boolean: `and`, `or`, `not` (short-circuit)
- Augmented assignment: `+=`, `-=`, `*=`, `/=`
- String repetition: `"ab" * 3` gives `"ababab"`
- List concatenation: `[1, 2] + [3, 4]`

### Control Flow
- `if` / `elif` / `else`
- `while` loops with `break` and `continue`
- `for` / `in` loops (over lists, strings, `range()`)
- Indentation-based blocks (Python-style)

### Functions
- `def` with positional parameters
- `return` values
- Recursive calls (max depth: 256)

### Built-in Functions
`print`, `len`, `range`, `str`, `int`, `float`, `type`, `abs`, `min`, `max`,
`sum`, `sorted`, `reversed`, `enumerate`, `isinstance`

### String Methods
`upper`, `lower`, `strip`, `lstrip`, `rstrip`, `startswith`, `endswith`,
`find`, `replace`, `split`, `join`, `isdigit`, `isalpha`, `count`

### List Methods
`append`, `pop`, `insert`, `extend`, `index`, `count`, `reverse`

### Safety Limits
- Max 100,000 loop iterations per loop
- Max 256 recursion depth
- Integer overflow detection

## Usage

Add to your `Cargo.toml`:

```toml
[dependencies]
python-lite = "0.1"
```

For `no_std` environments:

```toml
[dependencies]
python-lite = { version = "0.1", default-features = false }
```

### Quick Start

```rust
fn main() {
    let output = python_lite::execute(r#"
def fizzbuzz(n):
    for i in range(1, n + 1):
        if i % 15 == 0:
            print("FizzBuzz")
        elif i % 3 == 0:
            print("Fizz")
        elif i % 5 == 0:
            print("Buzz")
        else:
            print(i)

fizzbuzz(20)
"#).unwrap();

    print!("{}", output);
}
```

### Using the Interpreter Directly

```rust
use python_lite::{Interpreter, Value};

fn main() {
    let tokens = python_lite::execute("x = 42\nprint(x * 2)").unwrap();
    assert_eq!(tokens.trim(), "84");
}
```

### Error Handling

```rust
fn main() {
    match python_lite::execute("x = 1 / 0") {
        Ok(output) => println!("{}", output),
        Err(e) => eprintln!("Python error: {}", e),  // "division by zero"
    }
}
```

## What This Is NOT

This is not CPython. It is not fully Python-compatible. It implements a useful
subset of Python syntax -- enough that an AI agent (or a human) can write
scripts for data processing, algorithms, and automation on constrained
platforms.

Notable differences from CPython:

- No classes (yet)
- No imports / modules
- No exceptions (`try`/`except`)
- No dictionaries (yet)
- No tuple type
- No generators / `yield`
- No `with` statement
- No list comprehensions (yet)
- `isinstance()` takes a string type name, not a type object
- Fractional float exponents (`2.0 ** 0.5`) return `NaN` (no libm dependency)

## License

Licensed under either of:

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or <http://www.apache.org/licenses/LICENSE-2.0>)
- MIT License ([LICENSE-MIT](LICENSE-MIT) or <http://opensource.org/licenses/MIT>)

at your option.

## Contributing

Contributions are welcome. Please open an issue or pull request on
[GitHub](https://github.com/suhteevah/python-lite).

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

---

## Support This Project

If you find this project useful, consider buying me a coffee! Your support helps me keep building and sharing open-source tools.

[![Donate via PayPal](https://img.shields.io/badge/Donate-PayPal-blue.svg?logo=paypal)](https://www.paypal.me/baal_hosting)

**PayPal:** [baal_hosting@live.com](https://paypal.me/baal_hosting)

Every donation, no matter how small, is greatly appreciated and motivates continued development. Thank you!
