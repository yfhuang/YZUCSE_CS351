# Test Plan (Verification)

## 1. Test Strategy
- Unit tests: per module
- Integration tests: engine + parser
- Golden tests: CLI end-to-end output compare

## 2. Test Environment
- Compiler:
- OS:
- How to run tests:
  - cmake -S . -B build
  - cmake --build build
  - ctest --test-dir build

## 3. Test Cases (table)
| Test ID | Level | Requirement ID | Description | Input Fixture | Expected |
|---|---|---|---|---|---|
| T-1 | Unit | FR-1 |  |  |  |
| T-2 | Unit | ER-1 |  |  |  |
| T-3 | Integration | FR-2 |  |  |  |
| T-4 | Golden | AC-1 |  |  |  |

## 4. Edge Cases Checklist
- Empty input
- Missing fields / nulls
- Invalid formats
- Large file sanity (optional)
