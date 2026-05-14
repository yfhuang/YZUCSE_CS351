# Assignment II - SDD, BDD, and TDD in AI-Assisted Software Development

## Student Information

- Name:
- Student ID:
- Course:
- Date:
- Due Date: 2026/5/31 23:59:59 (Submit via YZU Portal and you own course github repository)

# 1. Assignment Overview

In this assignment, you will practice three important development approaches in the AI era:

1. **SDD: Specification-Driven Development**
2. **BDD: Behavior-Driven Development**
3. **TDD: Test-Driven Development**

You will apply all three approaches to the same software scenario:

> **Scenario: Student Grade Calculator**

There is **no coding requirement** in this assignment.  
You only need to write the assignment in **Markdown format** and export it as a **PDF file**.


# 2. Assignment Scenario: Student Grade Calculator

Design a **Student Grade Calculator** that calculates a student’s final score and letter grade based on four components.

| Component | Weight |
|---|---:|
| Assignment | 30% |
| Midterm Exam | 20% |
| Final Exam | 30% |
| Project | 20% |

The final score is calculated as:

```text
Final Score = Assignment × 0.30 + Midterm × 0.20 + Final Exam × 0.30 + Project × 0.20
```

The letter grade is assigned according to the following rules:

| Final Score | Letter Grade |
|---:|---|
| 90–100 | A |
| 80–89 | B |
| 70–79 | C |
| 60–69 | D |
| Below 60 | F |

Grade interval rule:

- Use exact numeric intervals:
  - A: 90.0 <= Final Score <= 100.0
  - B: 80.0 <= Final Score < 90.0
  - C: 70.0 <= Final Score < 80.0
  - D: 60.0 <= Final Score < 70.0
  - F: Final Score < 60.0
- Final Score should be rounded to one decimal place before reporting.

# 3. Important Rule: Original Work Required

The examples provided in this assignment are only for reference.

Students **cannot directly copy or reuse the examples provided in this assignment markdown**.

You must create your **own version** of SDD, BDD, and TDD content based on the **Student Grade Calculator** scenario.

Each section should include at least **two original examples**.

| Section | Requirement |
|---|---|
| SDD | At least **two original specification items or acceptance criteria** |
| BDD | At least **two original Given–When–Then scenarios** |
| TDD | Include **three testing scenarios**, and each scenario must include **two original test cases** |

You may design your own examples by using:

- Different score combinations
- Different grade levels
- Boundary cases
- Invalid input cases
- Special cases related to grade calculation

# 4. Required Report Content

Your report should include the following sections.

## 4.1 Introduction

Briefly explain:

1. What AI-assisted software development is.
2. Why clear requirements are important when using AI tools.
3. Why SDD, BDD, and TDD are useful in the AI era.

Suggested writing direction:

```text
AI can generate software artifacts quickly, but AI does not automatically understand the real intention of the developer. Therefore, developers need to provide clear specifications, behavior descriptions, and test criteria to guide AI-generated results.
```

You should write this section in your own words.

## 4.2 Definition of SDD

Explain the meaning of **Specification-Driven Development**.

You may discuss the following items:

| Item | Description |
|---|---|
| Goal | What problem the software should solve |
| Functional requirements | What the software must do |
| Input | What data the system receives |
| Output | What result the system produces |
| Constraints | Rules or limitations the system must follow |
| Acceptance criteria | Conditions used to check whether the system is correct |

Your explanation should be written in your own words.

## 4.3 SDD: Student Grade Calculator

Write an SDD-style specification for the Student Grade Calculator.

Your SDD section should include the following parts.

### 4.3.1 Goal

Describe the purpose of the Student Grade Calculator.

### 4.3.2 Functional Requirements

Describe what the system should do.

For example, you may describe:

```markdown
- The system accepts four scores.
- The system calculates the weighted final score.
- The system assigns a letter grade.
- The system displays the final score and letter grade.
```

Do not copy the example directly.  
Please write your own version.

### 4.3.3 Input

Describe the required input data.

For example:

```markdown
- Assignment score: 0–100
- Midterm exam score: 0–100
- Final exam score: 0–100
- Project score: 0–100
```

### 4.3.4 Output

Describe the expected output.

For example:

```markdown
- Final weighted score
- Letter grade
```

### 4.3.5 Grade Rules

Explain the grading rules based on the final score.

### 4.3.6 Acceptance Criteria

Describe how to decide whether the system works correctly.

For example:

```markdown
- The final score must be calculated using the correct weights.
- The letter grade must follow the grading rules.
- Invalid scores should be identified if any score is below 0 or above 100.
```

Do not copy the example directly.  
You must write at least **two original specification items or acceptance criteria**.

## 4.4 Definition of BDD

Explain the meaning of **Behavior-Driven Development**.

BDD describes software requirements through user behaviors and concrete scenarios.

The common BDD format is:

```gherkin
Given some initial condition
When an action happens
Then the expected result should occur
```

Your explanation should describe why BDD is useful for communicating expected software behavior.

## 4.5 BDD: Student Grade Calculator

Write BDD scenarios using the **Given–When–Then** format.

You should include at least **two original BDD scenarios**.

Suggested scenario types include:

1. Grade A scenario
2. Grade B scenario
3. Grade C scenario
4. Grade D scenario
5. Grade F scenario
6. Invalid input scenario
7. Boundary case scenario

Reference example:

```gherkin
Scenario: Student receives grade A
Given the assignment score is 95
And the midterm exam score is 90
And the final exam score is 92
And the project score is 94
When the system calculates the final grade
Then the final score should be 92.9
And the letter grade should be A
```

You **cannot copy this example directly**.  
You need to create your own BDD scenarios with your own score combinations and expected results.

Example structure for your own answer:

```gherkin
Scenario 1: [Write your scenario title]
Given ...
And ...
When ...
Then ...
And ...

Scenario 2: [Write your scenario title]
Given ...
And ...
When ...
Then ...
And ...
```

## 4.6 Definition of TDD

Explain the meaning of **Test-Driven Development**.

TDD is a development approach where developers define test cases before implementation.

You should briefly explain the TDD cycle:

| Step | Description |
|---|---|
| Red | Write a test that fails because the function has not been implemented yet |
| Green | Create the simplest implementation that passes the test |
| Refactor | Improve the implementation while keeping all tests passing |

In this assignment, you do **not** need to write code.  
You only need to design test cases.

## 4.7 TDD: Student Grade Calculator

Write test cases for the Student Grade Calculator.

You should include **three testing scenarios**.
Each scenario must include at least **two original test cases**.

The three required scenarios are:

1. Normal test cases
2. Boundary test cases
3. Invalid input test cases

Reference example:

```markdown
### Test Case: Calculate grade A

#### Input
- Assignment: 95
- Midterm: 90
- Final Exam: 92
- Project: 94

#### Expected Calculation
Final Score = 95 × 0.30 + 90 × 0.20 + 92 × 0.30 + 94 × 0.20
Final Score = 92.9

#### Expected Output
- Final Score: 92.9
- Letter Grade: A
```

You **cannot copy this example directly**.  
You must create your own test cases with your own score combinations and expected results.

Example structure for your own answer:

```markdown
### Scenario 1: Normal Test Cases

#### Test Case 1:

#### Input
- Assignment:
- Midterm:
- Final Exam:
- Project:

#### Expected Calculation
Write your calculation here.

#### Expected Output
- Final Score:
- Letter Grade:

#### Test Case 2:

#### Input
- Assignment:
- Midterm:
- Final Exam:
- Project:

#### Expected Calculation
Write your calculation here.

#### Expected Output
- Final Score:
- Letter Grade:

### Scenario 2: Boundary Test Cases

#### Test Case 1:

#### Input
- Assignment:
- Midterm:
- Final Exam:
- Project:

#### Expected Calculation
Write your calculation here.

#### Expected Output
- Final Score:
- Letter Grade:

#### Test Case 2:

#### Input
- Assignment:
- Midterm:
- Final Exam:
- Project:

#### Expected Calculation
Write your calculation here.

#### Expected Output
- Final Score:
- Letter Grade:

### Scenario 3: Invalid Input Test Cases

#### Test Case 1:

#### Input
- Assignment:
- Midterm:
- Final Exam:
- Project:

#### Expected Calculation
Write your calculation here.

#### Expected Output
- Final Score:
- Letter Grade:

#### Test Case 2:

#### Input
- Assignment:
- Midterm:
- Final Exam:
- Project:

#### Expected Calculation
Write your calculation here.

#### Expected Output
- Final Score:
- Letter Grade:
```

## 4.8 Comparison of SDD, BDD, and TDD

Create a comparison table.

You may use the following format:

| Item | SDD | BDD | TDD |
|---|---|---|---|
| Full name | Specification-Driven Development | Behavior-Driven Development | Test-Driven Development |
| Main focus | Requirements and system specification | User behavior and scenarios | Test cases and correctness |
| Main question | What should be built? | How should the system behave? | How do we verify correctness? |
| Typical format | Structured specification | Given–When–Then | Test case table |
| AI-era value | Guides AI to understand requirements | Guides AI to understand expected behavior | Checks whether AI-generated output is correct |

You have to modify or expand this table using your own understanding.

---

## 4.9 Reflection

Write a reflection of **300-500 words**.

Please answer the following questions:

1. Which approach is easiest for you to understand: SDD, BDD, or TDD? Why?
2. Which approach is most useful when working with AI coding tools? Why?
3. How can SDD help reduce unclear AI prompts?
4. How can BDD help describe user expectations?
5. How can TDD help check whether AI-generated code is correct?
6. If you use AI tools in future software projects, how would you combine SDD, BDD, and TDD?

Your reflection should show your own understanding.  
Do not only write that “AI is useful.”  
You should explain how SDD, BDD, and TDD can help developers guide and evaluate AI-generated results.


## 4.10 References / AI Tool Usage

List the references, websites, books, or AI tools you used.

If you used AI tools, briefly describe how you used them.

Example:

```markdown
## References / AI Tool Usage

- ChatGPT was used to help understand the definitions of SDD, BDD, and TDD.
- The final content was reviewed and revised by myself.
- Reference website:
  - [Add website title and URL here]
```


# 5. Submission Requirements

You must submit **two files**:

1. One Markdown file
2. One PDF file converted from the Markdown file

Suggested file names:

```text
StudentID_SDD_BDD_TDD_Report.md
StudentID_SDD_BDD_TDD_Report.pdf
```

Example:

```text
1121234_SDD_BDD_TDD_Report.md
1121234_SDD_BDD_TDD_Report.pdf
```

# 6. Suggested Markdown Report Template

You may copy the following template structure, but you must write the content in your own words.

Note:

- You may follow this template numbering directly, or keep the same numbering style as this assignment document, as long as all required sections are included.

```markdown
# Assignment: SDD, BDD, and TDD in AI-Assisted Software Development

## Student Information

- Name:
- Student ID:
- Course:
- Date:

---

## 1. Introduction

---

## 2. Definition of SDD

---

## 3. SDD: Student Grade Calculator

### 3.1 Goal

### 3.2 Functional Requirements

### 3.3 Input

### 3.4 Output

### 3.5 Grade Rules

### 3.6 Acceptance Criteria

---

## 4. Definition of BDD

---

## 5. BDD: Student Grade Calculator

### Scenario 1:

### Scenario 2:

---

## 6. Definition of TDD

---

## 7. TDD: Student Grade Calculator

### Scenario 1: Normal Test Cases

#### Test Case 1:

#### Test Case 2:

### Scenario 2: Boundary Test Cases

#### Test Case 1:

#### Test Case 2:

### Scenario 3: Invalid Input Test Cases

#### Test Case 1:

#### Test Case 2:

---

## 8. Comparison of SDD, BDD, and TDD

---

## 9. Reflection

---

## 10. References / AI Tool Usage
```

---

# 7. Grading Rubric

Total: **100 points**

| Criteria | Points | Description |
|---|---:|---|
| Introduction | 5 | Clearly explains the importance of SDD, BDD, and TDD in AI-assisted software development |
| Definition of SDD | 10 | Correctly defines SDD and explains its purpose |
| SDD application | 15 | Provides a clear specification for the Student Grade Calculator with at least two original specification items or acceptance criteria |
| Definition of BDD | 10 | Correctly defines BDD and explains the Given–When–Then structure |
| BDD application | 15 | Provides at least two original BDD scenarios for the Student Grade Calculator |
| Definition of TDD | 10 | Correctly defines TDD and explains test-first thinking |
| TDD application | 15 | Provides three testing scenarios (normal, boundary, invalid), with at least two original test cases in each scenario |
| Comparison of SDD, BDD, and TDD | 10 | Clearly compares the three approaches |
| Reflection | 5 | Shows personal understanding and critical thinking |
| File submission format | 5 | Submits both Markdown and PDF files with correct file names |
| **Total** | **100** |  |

Originality policy:

- Reusing example content from this assignment document may result in point deductions in SDD application, BDD application, and TDD application sections.

---

# 8. Important Notes

1. You do **not** need to write program code in this assignment.
2. You must submit both a Markdown file and a PDF file.
3. The examples in this assignment are only for reference.
4. You cannot directly copy the examples from this assignment.
5. You must create your own SDD, BDD, and TDD examples.
6. SDD and BDD sections must each include at least two original examples; TDD must include three testing scenarios, with at least two original test cases in each scenario.
7. The purpose of this assignment is to practice how to describe software clearly before implementation.
8. In AI-assisted software development, you should not only ask AI to “write a program.” Instead, you should provide clear specifications, behavior scenarios, and test cases to guide and evaluate AI-generated results.
