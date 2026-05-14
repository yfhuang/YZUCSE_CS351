# C++23 Coding Standards v2

Apply the following standards consistently across the project.

This document is written for both human developers and AI coding tools.
When generating or modifying code, follow these rules unless the user explicitly overrides them.

---

## 0. Target Language and Scope

- the target programming language is **C++23**
- use standard C++23 features when they improve clarity, safety, or correctness
- prefer the C++ standard library over custom utilities when the standard library already provides a clear solution
- do not introduce non-standard compiler extensions unless explicitly required
- do not add third-party dependencies unless explicitly requested

### Allowed file types

- implementation files use `.cpp`
- header files use `.hpp`
- inline or template-only headers may use `.hpp`
- test files use `.cpp`

---

## 1. AI Tool Execution Rules

When acting as an AI coding assistant:

- make the **smallest reasonable change** that satisfies the request
- do not perform unrelated refactoring unless explicitly requested
- preserve public APIs, file layout, and behavior unless change is required
- do not rename files, functions, classes, or variables without a clear reason
- do not invent requirements that are not stated
- when requirements are missing, choose the most conservative and maintainable interpretation
- when a rule conflicts with existing project conventions, prefer the existing project convention and mention the conflict
- before finalizing, self-check naming, structure, tests, and documentation impact

---

## 2. File Naming

- source files use `snake_case.cpp`
- header files use the matching `snake_case.hpp`
- test files use the `_tests.cpp` suffix
- avoid vague names such as `final`, `temp`, `new`, `misc`, `stuff`, or `test2`

### Examples

- `config_parser.cpp`
- `config_parser.hpp`
- `config_parser_tests.cpp`

### File mapping rules

- each reusable module should normally have one matching `.hpp` and `.cpp` pair
- declarations intended for reuse belong in the header
- implementation details belong in the source file
- exceptions are allowed for:
  - template-heavy modules
  - header-only utilities
  - very small internal-only helpers that are not reused outside one translation unit

---

## 3. Naming Rules

### Variables

- local variables use `snake_case`
- function parameters use `snake_case`
- data members use `snake_case_` with a trailing underscore

### Functions

- functions use `snake_case`
- predicate functions should prefer names such as `is_valid`, `has_value`, `can_parse`
- functions that mutate state should use clear action verbs

### Types

- classes use `PascalCase`
- structs use `PascalCase`
- enums use `PascalCase`
- enum values use `PascalCase`

### Constants

Use exactly one style for ordinary constants:

- prefer `kCamelCase` for named constants
- reserve `UPPER_SNAKE_CASE` only for macros or compile-time configuration symbols when unavoidable

### Namespaces

- namespaces use `snake_case`
- avoid deep namespace nesting unless it improves clarity
- do not use `using namespace ...` in header files

### Prohibited mixing

- do not mix naming styles in the same module
- do not mix `kCamelCase` and `UPPER_SNAKE_CASE` for the same kind of constant

---

## 4. Code Organization

Keep responsibilities separated.

- parsing logic must be separate from business logic
- CLI handling must be separate from core logic
- formatting or output logic must be separate from transformation logic
- validation logic should be isolated when it is non-trivial
- reusable declarations belong in headers
- unrelated responsibilities should not be placed in the same file

### Preferred structure

- `main.cpp` only handles argument parsing, orchestration, and process exit status
- core logic lives in reusable modules
- I/O code should be isolated from pure transformation logic when practical
- business rules should be testable without invoking the CLI

---

## 5. Header Rules

- header files must have include guards or `#pragma once`
- prefer `#pragma once` unless the project already standardizes on include guards
- include only what is required
- prefer forward declarations in headers when they reduce unnecessary coupling
- never place `using namespace` directives in headers
- keep headers self-contained: a header should compile when included into a minimal source file

---

## 6. Include Order

Organize includes in this order, with one blank line between groups:

1. matching project header
2. C++ standard library headers
3. third-party headers
4. project headers

### Example

```cpp
#include "config_parser.hpp"

#include <filesystem>
#include <string>
#include <vector>

#include <fmt/core.h>

#include "cli_options.hpp"
#include "text_formatter.hpp"