# Coding Standards

Apply the following standards consistently across the project.

## 1. File Naming

- source files use `snake_case`
- header files match the corresponding source file name
- test files use the `_tests` suffix
- avoid vague names such as `final`, `temp`, `new`, or `test2`

## 2. Variable, Function, Type, and Constant Naming

- variables use `snake_case`
- functions use `snake_case`
- classes and structs use `PascalCase`
- constants use `kCamelCase` or `UPPER_SNAKE_CASE`
- do not mix naming styles in the same file or module

## 3. Code Organization

- keep parsing logic separate from business logic
- keep CLI handling separate from core logic
- keep formatting or output logic separate from transformation logic
- place reusable declarations in the appropriate header files
- avoid putting multiple unrelated responsibilities into one file

## 4. Formatting and Coding Style

- use consistent indentation throughout the file
- use one brace style consistently within the project
- keep functions reasonably small and focused
- wrap long lines in a readable way
- organize includes consistently
- use helper functions only when they improve clarity or reduce duplication

## 5. Comment Policy

Useful comments explain:

- why a non-obvious decision was made
- assumptions about input or output
- constraints or invariants
- tricky edge-case behavior

Avoid comments that only restate obvious code.

## 6. Documentation Policy

- update documentation when behavior, interface, or usage changes
- keep README instructions consistent with the actual code and commands
- keep design, test, and traceability documents aligned with implementation changes

## 7. Testing Policy

- add or update tests when behavior changes
- keep test files under the test directory used by the project
- keep test names clear and behavior-oriented
- ensure local and CI test commands remain valid after changes

## 8. Review Standard

Every change should be reviewed for:

- correctness
- naming consistency
- module placement
- readability
- test coverage
- documentation impact
- unnecessary complexity or duplication
