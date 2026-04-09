# Lecture 8 - Standards Before Vibe Coding

## Purpose

This lecture focuses on what students must define before they start fast AI-assisted coding or so-called vibe coding. The central message is simple: if a team wants code to remain maintainable, reviewable, and revisable, then the team must establish shared standards on Day 1.

Without shared standards, AI-assisted coding can produce a large amount of code quickly, but the team will struggle to understand, review, trace, and safely modify that code later.

## Core Message

Speed without standards creates maintenance debt.

Before a team starts generating or writing large amounts of code, it should already agree on:

- naming conventions
- repository structure
- coding style rules
- documentation expectations
- testing expectations
- commit and pull request conventions
- traceability rules
- review standards

These decisions reduce ambiguity and help every developer stay on the same page.

## Why This Matters in AI-Assisted Development

AI tools can generate code quickly, but they do not automatically enforce a team's conventions unless those conventions are clearly defined.

If standards are missing, the result is usually:

- inconsistent filenames
- mixed naming styles
- duplicated logic
- unclear module boundaries
- weak commit history
- difficult reviews
- poor traceability from requirement to implementation

This is why standards should be defined before the team begins large-scale implementation.

## Day 1 Engineering Decisions

At the beginning of the project, the team should define the following.

### 1. File and Directory Naming Convention

Students should decide how files and folders will be named.

Examples of questions to answer:

- Will source files use `snake_case`, `camelCase`, or another pattern?
- Will header files match source file names?
- How will lecture files, docs, and test files be named?
- Where will parser, engine, model, and CLI files live?

Good examples:

- `parser.cpp`
- `variant_filter.cpp`
- `json_converter_tests.cpp`
- `docs/04_test_plan.md`

Poor examples:

- `FinalCode.cpp`
- `myFile.cpp`
- `temp_new_version.cpp`
- `test2.cpp`

The rule should be written down and followed consistently.

### 2. Variable, Function, Type, and Constant Naming

The team should agree on naming style for code symbols.

Typical decisions include:

- variable names
- function names
- class or struct names
- constants and enum values
- macros, if any are used

Example policy:

- variables and functions use `snake_case`
- classes and structs use `PascalCase`
- constants use `kCamelCase` or `UPPER_SNAKE_CASE`

The exact choice is less important than consistency.

### 3. Code Organization Rules

Students should decide how code is divided across modules.

For example:

- parsing logic stays in `parser.cpp` or parser-related files
- business logic stays in engine or transform files
- CLI handling stays separate from core logic
- tests stay under `tests/`

This matters because code organization affects readability, testability, and future modification.

### 4. Formatting and Coding Style

Teams should define basic formatting rules before implementation.

At minimum, decide:

- indentation width
- brace style
- maximum reasonable function size
- how to wrap long lines
- how includes are organized
- whether helper functions should be static or in anonymous namespaces

The purpose is not style for style's sake. The purpose is to reduce review friction and make code easier to scan.

### 5. Comment and Documentation Policy

Students should define what deserves a comment and what should remain self-explanatory.

Useful comments explain:

- why a non-obvious decision was made
- assumptions about input or output
- constraints or invariants
- tricky edge-case behavior

Poor comments only restate obvious code.

Documentation expectations should also include:

- what goes in `README.md`
- what belongs in `docs/02_SRS.md`
- what belongs in `docs/03_SDS.md`
- when `docs/04_test_plan.md` must be updated

### 6. Testing Standard

Before coding starts, the team should agree on how testing will be done.

For this course, students should define:

- where test files live
- how test executables are named
- how tests are registered in CMake
- how local tests are run
- how GitHub Actions runs tests automatically

Testing should be part of the default workflow, not something added near the deadline.

### 7. Commit and Pull Request Conventions

The team should define how commits and PRs are written.

At minimum, the team should already know:

- branch naming format
- commit message format
- Jira issue reference rules
- PR title format
- what must be included in a PR description

This helps make the development history traceable and reviewable.

### 8. Review Standard

Code review should have shared expectations.

Before implementation starts, the team should agree on what reviewers will check.

Common review points:

- correctness
- readability
- naming consistency
- test coverage
- requirement alignment
- unexpected complexity
- documentation updates

Without review standards, review quality becomes inconsistent and subjective.

## Naming Convention Is Not a Small Detail

Students often underestimate naming. In practice, naming affects:

- readability
- searchability
- code review speed
- onboarding of teammates
- refactoring safety
- AI prompt clarity when asking tools to modify code

If filenames, variables, and functions follow random patterns, the codebase becomes harder to search and harder to discuss.

## Example: Naming Policy Defined on Day 1

An example of a small, workable policy:

- markdown documents use numbered prefixes where order matters
- source and test files use `snake_case`
- C++ functions use `snake_case`
- C++ types use `PascalCase`
- test files end with `_tests.cpp`
- branches use `feature/<JIRA-KEY>-short-title`
- commit messages include the Jira issue ID

This is not the only valid policy. It is an example of a policy that can be applied consistently.

## Relationship to Traceability

Standards are not only about aesthetics. They also support traceability.

Traceability becomes easier when:

- filenames are predictable
- modules have clear responsibilities
- tests are named consistently
- commits reference Jira items
- PRs reference requirements and tests

This directly supports the course workflow from intended use to requirements, design, implementation, testing, CI, and release.

## Relationship to Code Review and Revision

Teams revise code throughout the project. That is normal.

Standards help revision because they make it easier to answer questions such as:

- where should this change go?
- what file should I inspect first?
- what is the expected naming pattern?
- which requirement does this implementation support?
- what tests should change together with this code?

If standards are defined late, teams waste time arguing over avoidable inconsistencies.

## How to Use Standards When Working with AI Tools

Defining standards is not enough. Teams must also use those standards actively when prompting, reviewing, and revising AI-generated output.

The practical rule is this: standards should be treated as input constraints for AI tools, not only as human review criteria after code is generated.

### 1. Put standards into the prompt context

When asking an AI tool to generate or revise code, students should state the relevant standards explicitly.

Examples:

- use `snake_case` for function and variable names
- keep CLI logic separate from parsing logic
- place tests under `tests/`
- update `docs/04_test_plan.md` if behavior changes
- follow the team's commit and PR conventions

If these rules are not given, the tool may produce code that is technically plausible but inconsistent with the repository.

### 2. Ask AI to follow repository structure, not invent one

Students should prompt AI tools with the actual project structure and expected file destinations.

For example:

- modify `src/parser.cpp`, do not create a new parser module
- add tests in `tests/parser_tests.cpp`
- keep reusable declarations in `include/`

This prevents the AI from introducing parallel structures or unnecessary files.

### 3. Use standards as a review checklist for AI output

After AI generates code, students should review it against the same standards used for human-written code.

Questions to ask:

- are filenames and symbols consistent with the naming convention?
- does the code go in the correct module?
- does the style match the rest of the repository?
- are tests added in the right place?
- does the change preserve traceability to requirements and Jira items?

AI output should never bypass review just because it was generated quickly.

### 4. Require AI-generated changes to remain traceable

Students should maintain the same traceability chain for AI-assisted work as for any other work.

That means:

- the Jira ticket still defines the work item
- the branch name still follows team convention
- the commit still includes the Jira issue ID
- the PR still explains the purpose of the change
- the tests still map back to requirements or behaviors

AI assistance does not reduce the need for traceability. In many cases, it increases the need for it.

### 5. Use standards to reject low-quality AI suggestions

One of the most important professional habits is rejecting code that violates team standards, even if it appears to work.

Students should reject or rewrite AI output when it:

- introduces inconsistent naming
- mixes multiple responsibilities in one file
- duplicates existing logic
- skips tests or documentation updates
- hides assumptions or edge cases
- creates code that is difficult to review

Fast output is not the goal. Maintainable output is the goal.

### 6. Record AI-specific rules early

If the team uses AI tools regularly, the team should write down a short AI collaboration policy.

Possible rules include:

- always provide repository conventions in the prompt
- never merge AI-generated code without human review
- require tests for behavior changes
- require doc updates for interface changes
- require developers to understand any generated code before committing it

These rules make AI usage more consistent and reduce hidden quality risk.

## Example: Good AI-Assisted Workflow

One practical workflow is:

1. define the requirement and Jira ticket
2. identify the relevant coding and naming standards
3. prompt the AI with those standards explicitly
4. review the generated code against repository conventions
5. add or revise tests
6. update docs if needed
7. commit and open a PR using the normal workflow

This keeps AI as a productivity tool inside the engineering process, rather than replacing the engineering process.

## Vibe Coding Without Standards Is Risky

The danger of unstructured AI-assisted coding is not only incorrect code. It is inconsistent code that looks productive in the short term but becomes expensive to maintain.

Students should avoid the following pattern:

1. generate a large amount of code quickly
2. discover inconsistent names and structures later
3. spend significant time renaming, moving, and rewriting
4. lose confidence in the code because traceability and tests are weak

The better pattern is:

1. define standards first
2. write or generate code under those rules
3. review against those rules
4. revise consistently

## Recommended Team Standard Checklist

Before implementation begins, each team should confirm all of the following:

- filename convention is defined
- function and variable naming convention is defined
- class or type naming convention is defined
- repository structure is defined
- code formatting rules are defined
- comment policy is defined
- test naming and execution flow are defined
- commit and PR rules are defined
- review checklist is defined
- traceability expectations are defined

If these items are not decided, the team is not ready for large-scale coding.

## Suggested Artifacts to Create Early

Students should record these standards explicitly.

Possible places:

- `Lectures/CODING_STANDARDS.md` as a reusable AI-readable development standards attachment
- `README.md` for quick-start conventions
- `docs/01_plan.md` for team workflow agreements
- `docs/03_SDS.md` for module and design structure
- `AI_USAGE.md` if the project defines AI-assisted coding rules
- pull request templates or review checklists if used

Standards that are only spoken in class but never written down are easy to forget and hard to enforce.

## Suggested In-Class Exercise

Before coding, ask each team to produce a one-page team convention sheet containing:

1. file naming rule
2. symbol naming rule
3. repository structure rule
4. test file naming rule
5. commit message rule
6. PR review checklist
7. documentation update rule

This is a small exercise, but it prevents many avoidable project problems later.

## Review Questions

Before a team starts heavy implementation, ask:

1. If a new teammate joins, can they infer the naming rules quickly?
2. If a reviewer sees a file, can they predict its purpose?
3. If a requirement changes, can the team trace the impacted files and tests?
4. If AI generates code, does the team have standards to accept or reject it?
5. If a bug is found later, is the codebase organized enough to revise safely?

If the answer to these questions is no, the team should strengthen standards before moving faster.

## Final Advice

Professional teams do not define standards after the repository becomes messy. They define them early so implementation, review, and revision remain efficient. In this course, naming conventions and coding standards should be treated as Day 1 engineering decisions, especially before students start fast AI-assisted coding.
