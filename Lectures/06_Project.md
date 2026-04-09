# Lecture 6 - Project SOP: From Scratch to Running System

## Purpose

This lecture provides a standard operating procedure (SOP) for building a course project from zero to a runnable, testable, and reviewable system. The goal is not only to make the project work, but to make the work reproducible, traceable, and easy for another person to understand, build, and validate.

Students should treat this lecture as the global framework for Project 0, Project A, Project B, and Project C.

## Core Idea

Your project is not only `src/` code. A complete project in this course contains:

- problem definition
- plan and task breakdown
- requirements
- design
- implementation
- tests
- traceability
- deployment or packaging notes
- known limitations

That is why the template repository includes these documents:

- `docs/00_intended_use.md`
- `docs/01_plan.md`
- `docs/02_SRS.md`
- `docs/03_SDS.md`
- `docs/04_test_plan.md`
- `docs/05_acceptance_tests.md`
- `docs/06_traceability.md`
- `docs/07_deploy.md`
- `docs/08_known_issues.md`

## Global Framework

Use the following framework for every project.

| Stage | Main Question | Required Output |
|---|---|---|
| 0. Intended use | What problem are we solving, for whom, and under what constraints? | `docs/00_intended_use.md` |
| 1. Planning | How will the team divide and track the work? | `docs/01_plan.md`, Jira stories |
| 2. Requirements | What must the system do? | `docs/02_SRS.md` |
| 3. Design | How will the system be organized internally? | `docs/03_SDS.md` |
| 4. Implementation | What source code, headers, and CLI are needed? | `src/`, `include/`, `README.md` |
| 5. Verification | How do we prove each requirement works? | `tests/`, `docs/04_test_plan.md` |
| 6. Validation | Does the system satisfy the intended use in black-box scenarios? | `docs/05_acceptance_tests.md` |
| 7. Traceability | Can we trace each requirement to design and tests? | `docs/06_traceability.md` |
| 8. Deployment | How does a user build and run the system from scratch? | `docs/07_deploy.md` |
| 9. Maintenance | What is still limited, risky, or deferred? | `docs/08_known_issues.md` |

## SOP Overview

Students should follow this sequence.

1. Define the problem before writing code.
2. Break work into stories before creating branches.
3. Write requirements before finalizing implementation details.
4. Write design before large-scale coding.
5. Implement in small, traceable increments.
6. Add tests for each implemented behavior.
7. Prove the full CLI workflow works on a clean setup.
8. Document how another person can build and run the project from scratch.

## Step-by-Step SOP

### Step 1. Start from the intended use

Before implementation, complete `docs/00_intended_use.md`.

Students must define:

- target user
- input and output expectations
- execution environment
- success criteria
- explicit non-goals
- key constraints such as language, time, and dependency policy

If this file is weak, the rest of the project will drift.

### Step 2. Build the plan and task structure

Complete `docs/01_plan.md` and create Jira items.

At minimum, create stories for:

- requirements
- design
- parser or input handling
- core engine or transformation logic
- CLI
- tests
- CI
- documentation
- release or deployment notes

Every feature branch should correspond to a Jira item or one well-scoped task.

### Step 2A. Initialize Jira for project progress management

Before major coding starts, each team should initialize Jira as the operational control center for the project.

At minimum, set up the following structure:

- one Epic for the whole project
- Stories for major deliverables
- Subtasks when one Story is too large for one person or one PR
- one milestone or sprint grouping for each project checkpoint

Recommended initial Stories:

- Project setup
- Intended use and scope
- SRS draft
- SDS draft
- Core parser or input module
- Core engine or business logic
- CLI integration
- Test framework setup
- Acceptance test preparation
- CI pipeline
- Deployment notes
- Final release and changelog

Each Jira item should include:

- clear title
- short description
- owner
- due date or sprint
- acceptance criteria
- links to related requirement IDs when available

Recommended workflow states:

- Backlog
- To Do
- In Progress
- In Review
- Blocked
- Done

If your Jira board does not make blocked work visible, the team will hide schedule risk until it is too late.

### Step 2B. Connect Jira to Git and GitHub

Jira is most useful when it is connected to actual development evidence.

Students should follow these rules:

1. Create branches from Jira when possible.
2. Include the Jira issue key in branch names.
3. Include the Jira issue key in commit messages and reference the same Jira item in the PR title or description.
4. Keep one main PR focus per Story whenever practical.
5. Move the Jira item status when the real engineering state changes.

Example branch names:

- `feature/CS351-12-srs-draft`
- `feature/CS351-18-cli-acceptance-tests`

Example commit titles:

- `CS351-12 draft SRS for JSON converter`
- `CS351-18 add CLI golden tests`

Example PR titles:

- `CS351-12 Add first SRS draft`
- `CS351-18 Implement CLI acceptance test flow`

The Jira ticket, branch, commits, PR, and merged result should form one traceable chain.

### Step 3. Write the SRS before coding deeply

Complete `docs/02_SRS.md`.

This file should define:

- functional requirements with IDs such as `FR-1`, `FR-2`
- non-functional requirements such as determinism, portability, and robustness
- CLI interface and example commands
- error handling expectations
- acceptance criteria

The SRS is the contract. If the code and tests disagree with the SRS, the SRS must be revised intentionally rather than ignored.

### Step 4. Write the SDS before large implementation

Complete `docs/03_SDS.md`.

This file should explain:

- major modules
- key data structures
- parsing strategy
- core algorithms
- error model
- important design decisions

Students do not need an enterprise-scale design document. They do need enough structure so another engineer can understand why the codebase is organized the way it is.

### Step 5. Create the minimum runnable system

Before implementing all features, create a minimum project skeleton that can build successfully.

Recommended structure:

```text
.
├─ CMakeLists.txt
├─ README.md
├─ CHANGELOG.md
├─ docs/
├─ include/
├─ src/
├─ tests/
└─ .github/workflows/
```

At this stage, the repository should already support:

- configuration with CMake
- compilation without errors
- at least one executable target
- at least one test target or test placeholder
- a top-level README with build and run instructions

### Step 6. Implement incrementally

Do not write the whole project in one branch and test it at the end.

Use this pattern for each feature:

1. choose one requirement or story
2. create a branch
3. implement one coherent change
4. add or update tests
5. update docs if behavior changed
6. open a PR
7. revise from review feedback

Each commit message should be meaningful, include the Jira issue ID, and preferably follow a consistent convention such as a Jira-linked format or Conventional Commits with the Jira key preserved.

### Step 6A. Update Jira during implementation, not after it

Jira is not a final report that gets repaired at the end of the week. It should reflect current project state.

When a student starts work:

- move the item to `In Progress`
- confirm the assignee is correct
- confirm the branch is linked or recorded

When a pull request is opened:

- move the item to `In Review`
- link the PR in the Jira ticket if integration is not automatic
- check whether acceptance criteria are already satisfied or still pending

When work cannot continue:

- move the item to `Blocked`
- write the blocker clearly
- identify the dependency, missing decision, or technical risk
- assign the next action to a specific team member if needed

When work is merged and verified:

- move the item to `Done`
- verify linked tests, docs, and CI results are complete

This discipline matters because hidden incomplete work is one of the most common project management failures.

### Step 7. Write verification tests

Complete `docs/04_test_plan.md` and implement the tests.

At minimum, students should include:

- unit tests for internal logic
- integration tests for module interaction
- golden or end-to-end tests for CLI output
- invalid input tests
- edge case tests

Tests should map back to requirements when possible.

### Step 8. Write acceptance tests

Complete `docs/05_acceptance_tests.md`.

Acceptance tests are black-box scenarios. They answer this question:

Can a user run the program and obtain the expected result without knowing internal code details?

These tests should use realistic commands and expected outputs.

### Step 9. Maintain traceability

Complete `docs/06_traceability.md`.

The minimum traceability chain in this course is:

`Intended Use -> SRS Requirement -> SDS Section -> Test -> CI or Validation Step`

This prevents the project from becoming a pile of disconnected files.

### Step 10. Document deployment and clean setup

Complete `docs/07_deploy.md`.

This is the most important file for "run from scratch" behavior.

It must answer:

- what tools must be installed first
- how to configure the build
- how to build the executable
- how to run the program
- how to run tests
- how to package or release the result

If another student clones the repository and cannot follow this file successfully, the SOP is incomplete.

### Step 11. Record known issues honestly

Complete `docs/08_known_issues.md`.

Students should explicitly list:

- current limitations
- deferred features
- known bugs or assumptions
- reporting instructions

This is not a weakness. It is part of professional engineering practice.

## Minimum Implementation Details

For this course, a good baseline implementation usually includes:

- language: C++23
- build system: CMake
- test execution: `ctest`
- repository workflow: GitHub branches and PRs
- task tracking: Jira
- CI target: build plus test on a clean environment

### Minimum local commands

Students should be able to run the following commands on a clean clone:

```bash
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build
ctest --test-dir build
```

If the project exposes a CLI executable, also provide a real usage example such as:

```bash
./build/<app_name> --input data/sample.txt --output result.txt
```

Replace `<app_name>` with the actual executable name.

## SOP for "Run the Project from Scratch"

Every team should include this procedure in the project README and deployment notes.

### Environment checklist

Before building, confirm:

- Git is installed
- a C++ compiler is installed
- CMake is installed
- the repository is cloned successfully
- required sample input files exist

### Clean-start procedure

1. Clone the repository.
2. Enter the repository root.
3. Read `README.md` and `docs/07_deploy.md`.
4. Configure the build directory.
5. Build the project.
6. Run all tests.
7. Execute one documented example command.
8. Compare the result with expected output or acceptance criteria.

### Required documentation quality

Your run instructions are acceptable only if they are:

- complete
- copy-pasteable
- ordered
- tested on a clean setup
- consistent with the actual executable names and paths

## Jira Progress Management SOP

The team should use Jira to manage progress from project initialization to release.

### Project kickoff procedure

At the start of the project, the team should do all of the following:

1. Create the project Epic.
2. Create the initial Story list based on `docs/01_plan.md`.
3. Assign owners for the first wave of Stories.
4. Define milestone dates or sprint boundaries.
5. Agree on the board status meanings.
6. Confirm branch naming and commit message conventions.
7. Decide how blockers will be escalated.

The project should not begin implementation before this setup is done.

### Weekly progress routine

Each week, teams should review Jira using this checklist:

1. Is every active branch linked to a Jira item?
2. Does each in-progress ticket have an assignee?
3. Does each ticket have acceptance criteria?
4. Are blocked items clearly marked?
5. Are overdue items being split, reassigned, or re-planned?
6. Do new requirements require new Stories or SRS updates?
7. Do completed tickets have matching merged PRs and updated docs?

### Suggested board view by work type

To make progress visible, label or group work by category:

- documentation
- implementation
- testing
- CI or tooling
- release or deployment

This makes it easier to detect imbalance, such as a project with many coding tasks but no testing or release preparation.

### Jira-based checkpoint evidence

At a checkpoint or demo, teams should be able to show:

- the Epic and current milestone
- Stories already completed
- Stories currently in progress
- blocked tasks and their causes
- linked branches or PRs
- delivered artifacts in `docs/`, `src/`, and `tests/`

If a team claims progress that is not visible in Jira, Git history, tests, or documents, that progress is not yet reliable.

### When to split a Jira Story

Students should split a Story when:

- one Story spans multiple unrelated deliverables
- one Story cannot reasonably produce one focused PR
- one Story mixes design, implementation, and testing with no clear boundary
- one Story remains in progress for too long without reviewable output

Smaller, reviewable Stories produce better project control than one large ambiguous task.

## Definition of Done for the Course Project

A project is not done when the code "mostly works" on the author's machine. A project is done when all of the following are true:

- intended use is documented
- SRS and SDS are present and consistent
- code builds from scratch
- tests run successfully
- acceptance scenarios are documented
- traceability exists
- deployment instructions are reproducible
- known limitations are documented
- work is merged through PR review

## Common Failure Patterns

Students should avoid these common mistakes:

- writing code before defining requirements
- building features that are not in the intended scope
- keeping only one huge branch until the deadline
- having tests with no link to requirements
- documenting commands that were never actually tested
- assuming the grader knows hidden setup steps
- treating README as a marketing page instead of an execution guide

## Suggested Team Routine

For each weekly checkpoint, teams should be able to demonstrate:

1. one updated document in `docs/`
2. one implemented feature or module improvement
3. one test addition or refinement
4. one successful local build and run
5. one PR with review evidence

## Final Advice

The best project teams do not separate documentation from implementation. They treat documentation, code, tests, and deployment as one system. If your teammate cannot clone the repository and run the project from scratch by following your documents, then the project is not yet complete.
