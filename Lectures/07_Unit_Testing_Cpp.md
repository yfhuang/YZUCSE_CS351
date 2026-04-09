# Lecture 7 - Software Testing: Unit Testing with C++

## Purpose

This lecture introduces software testing with a practical focus on unit testing in C++. The objective is to help students understand what should be tested, how to structure tests, how to automate them with CMake, `ctest`, and GitHub Actions, and how unit tests support the larger project workflow introduced in the previous lectures.

In this course, unit testing is not an optional extra. It is part of the engineering evidence that a requirement has been implemented correctly.

## Learning Goals

By the end of this lecture, students should be able to:

1. explain the role of unit testing in the software development lifecycle
2. distinguish unit tests from integration tests and acceptance tests
3. write basic unit tests in C++ as small test executables
4. connect tests to requirements and edge cases
5. run unit tests locally and in CI
6. design code that is easier to test

## Why Testing Matters

Testing is a verification activity. It gives the team evidence that the implementation behaves as expected.

Good testing helps teams:

- catch regressions early
- document expected behavior
- refactor code more safely
- validate edge cases and error handling
- support code review with objective evidence
- maintain confidence as the project grows

Without tests, teams often rely on manual checking, memory, or optimistic assumptions. That does not scale.

## Testing Levels in This Course

Students should understand the difference between three common levels of testing.

| Test Level | Main Goal | Typical Scope | Example |
|---|---|---|---|
| Unit test | Verify one small unit of behavior | one function or class | parser helper, validation function, data transform rule |
| Integration test | Verify modules work together | two or more components | parser + engine, engine + output formatter |
| Acceptance test | Verify user-visible behavior | full CLI workflow | run executable on sample input and compare output |

Lecture 7 focuses on unit testing, but students must understand that unit tests are only one part of the full verification strategy.

## What Is a Unit Test?

A unit test checks one small, isolated piece of behavior.

Examples of good unit-test targets:

- a function that parses one line of input
- a function that validates one command argument
- a method that transforms one record into another format
- a helper that sorts output into deterministic order
- a function that returns an error for invalid data

Examples of poor unit-test targets:

- the entire application from command line to file output
- code that depends directly on many unrelated systems at once
- a test that checks many unrelated behaviors in one test case

If a unit test requires a large amount of setup, the code may be too tightly coupled.

## Unit Testing Principles

Strong unit tests usually have these properties:

- focused: each test checks one main behavior
- deterministic: the same input leads to the same result every time
- readable: the test name and structure explain intent clearly
- isolated: the test avoids unrelated external dependencies when possible
- repeatable: it can run many times without special manual setup
- fast: it should execute quickly enough to be run frequently

Students should prefer many small clear tests over a few large confusing tests.

## Test Design Strategy

For each requirement, ask these questions:

1. What is the normal expected behavior?
2. What is the boundary condition?
3. What invalid input should be rejected?
4. What output or state change should be observed?
5. What should remain unchanged?

This leads naturally to a test set that includes:

- happy-path tests
- boundary tests
- invalid-input tests
- error-handling tests
- determinism tests where order or formatting matters

## Connect Tests to Requirements

Tests should not be random examples added after coding. They should relate back to project requirements.

For example:

- `FR-1`: parse valid JSON input into internal records
- `ER-1`: reject malformed input with a clear error
- `NFR-1`: output order is deterministic

Possible matching unit tests:

- `T-1`: valid parser input returns expected record count
- `T-2`: malformed input throws or reports parse error
- `T-3`: sorting helper returns stable deterministic order

This is why the project template uses `docs/04_test_plan.md` and `docs/06_traceability.md`.

## Recommended Minimal Testing Approach

For this course, the default recommendation is to keep testing simple:

- write a normal C++ test executable
- compile it with CMake
- register it with `add_test(...)`
- run it through `ctest`

This approach works well because:

- it introduces no extra framework dependency
- it keeps the testing workflow easy to explain
- it integrates directly with CMake and GitHub Actions
- it is enough for small and medium student projects

## Basic C++ Test Executable Example

Consider a simple function:

```cpp
int add(int left, int right) {
	return left + right;
}
```

Simple test executable:

```cpp
#include <iostream>

int add(int left, int right);

int main() {
	if (add(2, 3) != 5) {
		std::cerr << "add(2, 3) should be 5\n";
		return 1;
	}

	if (add(-2, 3) != 1) {
		std::cerr << "add(-2, 3) should be 1\n";
		return 1;
	}

	return 0;
}
```

What this shows:

- the executable returns `0` on success
- the executable returns non-zero on failure
- failure messages explain what behavior was expected

## Assertion Style Without a Testing Framework

When students do not use a test framework, they should still write tests clearly.

Useful patterns include:

- compare actual values against expected values explicitly
- print a clear error message to `std::cerr`
- return a non-zero exit code on failure
- keep each test executable focused on one component or behavior set

If students want a lightweight helper, they can define a small local check function or macro, but it should remain simple and readable.

## Example: Testing a Parser Helper

Suppose the project has a helper that parses one CSV line.

```cpp
std::vector<std::string> split_csv_line(const std::string& line);
```

Possible unit tests:

```cpp
#include <iostream>

int main() {
	const auto fields = split_csv_line("a,b,c");
	if (fields.size() != 3) {
		std::cerr << "expected 3 fields\n";
		return 1;
	}

	if (fields[0] != "a" || fields[1] != "b" || fields[2] != "c") {
		std::cerr << "unexpected field contents for simple CSV line\n";
		return 1;
	}

	const auto fields_with_empty = split_csv_line("a,,c");
	if (fields_with_empty.size() != 3 || fields_with_empty[1] != "") {
		std::cerr << "empty field handling failed\n";
		return 1;
	}

	return 0;
}
```

These tests are better than testing the entire CLI just to learn whether one line parser works.

## Example: Testing Error Handling

If the function should reject malformed input, the test should check that behavior explicitly.

```cpp
#include <iostream>
#include <stdexcept>

int main() {
	try {
		split_csv_line("\"abc,def");
		std::cerr << "expected parse failure for unterminated quoted field\n";
		return 1;
	} catch (const std::runtime_error&) {
		return 0;
	}
}
```

This is important because error paths are often less tested than happy paths.

## Designing Code for Testability

Some code is hard to test because of poor structure, not because testing itself is difficult.

Students should try to:

- separate pure logic from file I/O
- separate parsing from CLI handling
- separate data transformation from printing
- keep functions small and focused
- inject dependencies instead of hard-coding them when practical

A common pattern is:

- one layer reads files or command arguments
- one layer performs core logic
- one layer formats output

The core logic layer should be easiest to unit test.

## Suggested Test Directory Structure

One simple structure for course projects is:

```text
tests/
├─ parser_tests.cpp
├─ engine_tests.cpp
├─ model_tests.cpp
└─ cli_smoke_tests.cpp
```

Students do not need to mirror production files exactly, but tests should remain organized by component or behavior.

## CMake Integration Example

CMake should register tests so they run consistently in local development and CI.

### Step-by-step preparation

Students can prepare local testing in this order:

1. create a root `CMakeLists.txt`
2. enable CMake testing support
3. define the production source target
4. define one or more test executables under `tests/`
5. register each test executable with `add_test(...)`
6. configure and build the project
7. run the tests with `ctest`

### Minimal `CMakeLists.txt` example

For a small course project, a minimal starting point can look like this:

```cmake
cmake_minimum_required(VERSION 3.20)
project(cs351_project LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

enable_testing()

add_library(project_core
	src/parser.cpp
	src/engine.cpp
)

target_include_directories(project_core PUBLIC include)

add_executable(parser_tests
	tests/parser_tests.cpp
)

target_link_libraries(parser_tests PRIVATE project_core)

add_executable(engine_tests
	tests/engine_tests.cpp
)

target_link_libraries(engine_tests PRIVATE project_core)

add_test(NAME parser_tests COMMAND parser_tests)
add_test(NAME engine_tests COMMAND engine_tests)
```

This is not the only valid structure, but it shows the essential pieces:

- `enable_testing()` turns on CMake test support
- `add_library(...)` groups reusable production code
- `add_executable(...)` creates test programs
- `target_link_libraries(...)` connects the tests to the production code
- `add_test(...)` makes each test visible to `ctest`

Example outline:

```cmake
enable_testing()

add_executable(parser_tests
    tests/parser_tests.cpp
    src/parser.cpp
)

add_executable(engine_tests
    tests/engine_tests.cpp
    src/engine.cpp
)

add_test(NAME parser_tests COMMAND parser_tests)
add_test(NAME engine_tests COMMAND engine_tests)
```

If the test executable returns `0`, the test passes. If it returns a non-zero status, `ctest` reports a failure.

The exact setup may vary by project, but the important point is that tests are buildable through CMake and runnable through `ctest`.

### Preparation checklist

Before running local tests, students should confirm:

- `CMakeLists.txt` exists in the repository root
- source files referenced in CMake actually exist
- test source files exist under `tests/`
- include paths are declared correctly
- each test executable has a `main()` function
- each test executable returns `0` on success and non-zero on failure
- each test executable is registered by `add_test(...)`

## Standard Local Test Workflow

Students should be able to run tests with a standard local workflow:

```bash
cmake -S . -B build
cmake --build build
ctest --test-dir build --output-on-failure
```

`--output-on-failure` is useful because it shows which test failed and why.

### Recommended local command sequence

Students can use the following detailed sequence during development:

```bash
cmake -S . -B build
cmake --build build
ctest --test-dir build --output-on-failure
```

Useful optional commands:

```bash
ctest --test-dir build -N
ctest --test-dir build --output-on-failure -R parser_tests
cmake --build build --target parser_tests
```

What these commands do:

- `ctest --test-dir build -N` lists discovered tests without running them
- `ctest --test-dir build --output-on-failure -R parser_tests` runs only tests matching `parser_tests`
- `cmake --build build --target parser_tests` builds only the named test target

### First-time local setup for students

If students are preparing testing for the first time, the simplest path is:

1. create one small production function in `src/`
2. create one matching test executable in `tests/`
3. add both targets to `CMakeLists.txt`
4. register the test with `add_test(...)`
5. run `cmake -S . -B build`
6. run `cmake --build build`
7. run `ctest --test-dir build --output-on-failure`

Only after this works should they add more test executables.

## Naming Conventions

Good test names communicate behavior.

Prefer:

- `parser_tests.cpp`
- `engine_tests.cpp`
- `validation_tests.cpp`

Avoid:

- `Test1`
- `MyTest`
- `WorksCorrectly`
- `FinalVersion`

The goal is to make test purpose understandable from the file name, executable name, and failure output.

## Common Mistakes in Student Tests

Students should avoid these mistakes:

- writing only happy-path tests
- testing multiple unrelated behaviors in one test
- depending on file system state when a pure function test would be enough
- making tests order-dependent
- copying large amounts of production logic into tests
- asserting too little
- asserting implementation detail instead of observable behavior
- never running tests after refactoring

## Unit Testing Workflow in the Project

The recommended workflow for each feature is:

1. identify the requirement to implement
2. decide what unit behavior should be verified
3. write the test first or at least define the expected cases early
4. implement the code
5. run the unit tests locally
6. add edge-case tests
7. include the tests in the PR
8. update the test plan if coverage changed

Students are not required to follow strict TDD in every case, but they are expected to think in a test-first or at least test-aware way.

## Relationship to CI

Local tests are not enough. The same tests should run automatically in CI.

Why this matters:

- it confirms the project works on a clean environment
- it prevents "works on my machine" problems
- it provides verification evidence before merge
- it protects the main branch from obvious regressions

At minimum, CI should:

1. configure the project
2. build the code
3. run the unit tests

In this course, the recommended CI platform is GitHub Actions.

## Why GitHub Actions Fits This Course

GitHub Actions is a good default choice because:

- it runs automatically on pushes and pull requests
- it works directly inside the repository
- it provides visible pass or fail status for reviewers
- it helps enforce clean-environment builds
- it integrates naturally with GitHub-based team workflows

For student teams, this means test automation is not a separate tool chain that lives only on one laptop. It becomes part of the shared project workflow.

## Recommended GitHub Actions Trigger Policy

At minimum, automatic testing should run on:

- pushes to active branches
- pull requests targeting `main`

This catches problems early and prevents many broken changes from reaching the review or merge stage.

## Example GitHub Actions Workflow

Students can create a workflow file at `.github/workflows/ci.yml`.

Example:

```yaml
name: C++ CI

on:
	push:
	pull_request:
		branches:
			- main

jobs:
	build-and-test:
		runs-on: ubuntu-latest

		steps:
			- name: Check out repository
				uses: actions/checkout@v4

			- name: Configure project
				run: cmake -S . -B build -DCMAKE_BUILD_TYPE=Release

			- name: Build project
				run: cmake --build build --config Release

			- name: Run unit tests
				run: ctest --test-dir build --output-on-failure
```

This workflow is intentionally simple. It assumes:

- CMake is the build system
- the test executable is already registered with `ctest`
- the project builds on `ubuntu-latest`

If the project uses extra dependencies, students may need additional setup steps.

## How the Workflow Connects to Unit Testing

The workflow above automates the same process students should already run locally:

1. configure with CMake
2. build the targets
3. run the tests with `ctest`

This is important because a test process that only works in the author's local environment is not reliable project evidence.

## Recommended Repository Structure for CI

To support automatic testing smoothly, the repository should include:

- `CMakeLists.txt`
- `src/`
- `include/`
- `tests/`
- `.github/workflows/ci.yml`

The workflow should be version-controlled like any other engineering artifact.

## Practical Notes for CMake-Based CI

Students should ensure that:

- the test target is part of the normal CMake build
- tests are registered with `add_test(...)`
- tests do not depend on machine-specific paths
- tests do not depend on hidden local files
- test output is stable enough for repeated CI runs

If the CI workflow passes locally but fails on GitHub Actions, that usually means the project depends on undeclared assumptions.

## Recommended CI Review Checklist

Before opening or merging a pull request, students should ask:

1. Does the branch build on a clean environment?
2. Do unit tests run through `ctest`?
3. Does the GitHub Actions workflow run automatically?
4. Are test failures easy to interpret from logs?
5. Is the PR blocked from merge if the workflow fails?

These checks turn testing from a personal habit into a team-level quality gate.

## Suggested Course Policy for Automatic Testing

For project work in this course, a reasonable baseline policy is:

- no direct push to `main`
- every feature branch goes through a pull request
- GitHub Actions must pass before merge
- unit tests should be updated whenever behavior changes

This policy aligns with the Jira, GitHub, and review workflow introduced in earlier lectures.

## How Much Unit Testing Is Enough?

There is no single magic number, but students should aim for meaningful coverage of important behaviors.

Minimum expectation:

- every important module has at least some unit tests
- every important error path has explicit tests
- edge cases are not ignored
- deterministic behavior is tested when required by the project

Low-value testing patterns include writing many superficial tests that do not protect real behavior.

## Review Checklist

When reviewing a project draft, ask:

1. Are the core functions testable without running the full program?
2. Are test names readable and behavior-based?
3. Are invalid inputs tested?
4. Are requirements linked to tests?
5. Can tests run through `ctest`?
6. Do the tests help future refactoring?

## Suggested In-Class Practice

Students can practice unit testing by doing the following:

1. choose one small parsing or validation function
2. list three happy-path cases
3. list three invalid or edge cases
4. write the test executable cases
5. run them locally
6. intentionally break the function and observe test failure
7. fix the code and rerun the tests

This exercise makes the value of regression testing visible very quickly.

## Final Advice

Good unit tests are part of system design, not only part of debugging. If the code is hard to test, that is often a sign that the design should be improved. In this course, students should treat unit tests as a normal deliverable alongside code, design, and documentation.
