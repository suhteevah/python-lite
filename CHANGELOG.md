# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.1.0] - 2026-04-02

### Added

- Initial release, extracted from the ClaudioOS bare-metal operating system.
- Tokenizer with Python-style significant indentation (INDENT/DEDENT tokens).
- Recursive-descent parser with Pratt-style precedence climbing.
- Tree-walking interpreter with captured `print()` output.
- **Data types:** `int`, `float`, `str`, `bool`, `list`, `None`.
- **Arithmetic:** `+`, `-`, `*`, `/`, `//`, `%`, `**` with int/float promotion.
- **Comparison:** `==`, `!=`, `<`, `>`, `<=`, `>=`.
- **Boolean logic:** `and`, `or`, `not` with short-circuit evaluation.
- **Control flow:** `if`/`elif`/`else`, `while`, `for`/`in`, `break`, `continue`.
- **Functions:** `def`, `return`, recursion (max depth 256).
- **Augmented assignment:** `+=`, `-=`, `*=`, `/=`.
- **String operations:** concatenation, repetition, indexing, and methods
  (`upper`, `lower`, `strip`, `split`, `join`, `replace`, `find`, `startswith`,
  `endswith`, `isdigit`, `isalpha`, `count`).
- **List operations:** indexing, concatenation, and methods
  (`append`, `pop`, `insert`, `extend`, `index`, `count`, `reverse`).
- **Builtins:** `print`, `len`, `range`, `str`, `int`, `float`, `type`, `abs`,
  `min`, `max`, `sum`, `sorted`, `reversed`, `enumerate`, `isinstance`.
- Safety limits: max 100,000 loop iterations, max 256 recursion depth.
- `no_std` + `alloc` support for bare-metal and embedded use.
- `std` feature (enabled by default) for conventional Rust projects.
- 28 unit tests covering all major features.
