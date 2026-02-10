# Projects

## Project 0: Two Sum (Bootcamp)

**Focus:** full pipeline *(SRS/SDS → tests → CI → Docker → release)*

- Implementation is tiny; great for enforcing **CMake + tests + CI** discipline.

## Project A: JSON Plate-to-Nested Converter

- Use **nlohmann/json**.
- Teach:
    - parsing
    - schema assumptions
    - error handling
    - deterministic output
    - golden tests

## Project B: CSV Mini Database & Query Engine

- Teach:
    - parsing CSV
    - indexing
    - simple query grammar
    - performance trade-offs

**CSV parsing options:**
- write a simple, robust parser (handles quoted fields), or
- use a lightweight library via **vcpkg/Conan** *(optional)*

## Project C: VCF Variant Filter Engine

- Teach:
    - structured text parsing
    - DSL-like filtering
    - correctness testing

**Recommendation (teaching track):**
- implement a “good-enough VCF parser” (tab-splitting + `INFO` parsing)

**Optional (advanced track):**
- integrate **htslib** (powerful, but setup is heavier)
