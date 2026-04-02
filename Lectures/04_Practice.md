# Lecture 4 - Feature Development Workflow Practice

## Jira + GitHub + VS Code Feature Development Checklist

### Course Purpose

This handout describes the standard workflow students must follow when developing a feature in this course. The objective is to help students practice a complete software development process, including task management, branch control, coding, versioning, pull request review, merge, and synchronization.

Students are expected to follow this workflow for every assigned feature unless otherwise specified by the instructor.

## 1. Learning Objectives

By completing this workflow, students should be able to:

* manage development tasks using Jira
* organize feature work under the correct Epic and Story
* create and track feature branches
* develop code in a controlled Git workflow
* write meaningful commit messages with Jira issue IDs
* create and manage pull requests
* participate in code review
* merge reviewed code into the main branch
* clean up development branches after completion
* synchronize local and remote repositories correctly

## 2. Standard Feature Development Procedure

### Step 1. Create or confirm the Jira Story

Each feature must begin with a Jira Story under the correct Epic.

Students should:

* confirm the feature belongs to the assigned Epic
* create a new Story if needed, or use the Story assigned by the instructor
* make sure the Story clearly represents one meaningful unit of work

### Step 2. Complete the required information in the Jira Story

Before starting development, students must complete the required Story information.

The Jira Story should include:

* Story title
* feature description
* acceptance criteria
* assignee
* priority
* sprint or milestone information, if applicable
* labels, components, or tags, if required by the course

This step is important because the Jira Story serves as the formal record of the task and its expected outcome.

---

### Step 3. Create the feature branch via the Jira Story panel

Students must create the feature branch from the Jira Story so that the branch can be linked to the issue properly.

Requirements:

* use the Jira-integrated branch creation function if available
* follow the naming convention required by the project
* ensure the Jira issue ID appears in the branch name

Example:

* `feature/PROJ-123-user-login`
* `feature/CS351-25-add-search-filter`

### Step 4. Check the feature branch in GitHub

After creating the branch from Jira, students should verify that the branch has been created successfully in GitHub.

Students should confirm:

* the branch exists in the remote repository
* the branch name is correct
* the branch is associated with the intended Jira Story

### Step 5. Update the local repository before development

Before working locally, students must make sure their local repository is up to date.

In VS Code, students should:

* switch to the `main` branch
* pull the latest updates from the remote repository
* confirm there are no unresolved local changes that may interfere with the new feature work

This step helps avoid unnecessary conflicts later.

### Step 6. Create or check out the local feature branch in VS Code

Once the remote feature branch exists, students should create or check out the corresponding local feature branch.

Students should:

* base the local branch on the latest `main`
* connect the local feature branch to the remote feature branch if needed
* verify they are working on the correct branch before coding

### Step 7. Develop and test the feature

Students may now begin implementation.

During development, students are expected to:

* keep their work focused on the specific Story
* write readable, organized, and maintainable code
* follow the project coding conventions
* test the feature before committing or opening a pull request

If the feature is large, students are encouraged to develop it in small logical steps rather than making one large unstructured change.

### Step 8. Commit code with Jira ID and meaningful message

Students must commit their code with clear and traceable commit messages.

Commit messages should:

* include the Jira issue ID
* briefly describe the purpose of the change
* be specific enough for reviewers to understand the update

Examples:

* `PROJ-123 add login form validation`
* `PROJ-123 fix branch creation error handling`
* `CS351-25 implement search filter for product list`

Poor examples:

* `update code`
* `fix bug`
* `final version`

Recommended references for writing commit messages:

* [Conventional Commits](https://www.conventionalcommits.org/)
* [The Art of Writing Meaningful Git Commit Messages](https://medium.com/@iambonitheuri/the-art-of-writing-meaningful-git-commit-messages-a56887a4cb49)
* [Git commit message notes](https://hackmd.io/@howhow/git_commit)
* [How to Write a Git Commit Message](https://chris.beams.io/git-commit)

### Step 9. Push the feature branch to GitHub

After committing local changes, students must push the feature branch to GitHub.

Students should verify:

* all intended commits are pushed successfully
* the correct remote branch is updated
* GitHub reflects the latest development state before the pull request is created

### Step 10. Create the pull request

After development and testing are complete, students must create a pull request (PR).

If the course workflow uses Jira-integrated PR creation, students should create the PR through the Jira Story panel.
If not, students may create the PR directly in GitHub and verify that it is linked to the Jira issue.

The pull request should include:

* a clear title
* correct base branch and compare branch
* a short description of what was implemented
* a reference to the Jira Story

### Step 11. Check the pull request in GitHub and assign reviewers

Once the PR is created, students must review the PR details carefully.

Students should check:

* base branch is `main`
* compare branch is the correct feature branch
* PR title is clear and professional
* reviewers are assigned correctly
* any required labels, milestones, or checks are set properly

Students should not assume the PR is complete until these details are verified.

### Step 12. Revise code according to review comments

If reviewers request changes, students must respond professionally and revise the feature branch accordingly.

Students are expected to:

* read review comments carefully
* update the code in the same feature branch
* push the revised commits
* confirm that reviewer concerns have been addressed

Code review is part of the learning process and should be treated as a formal development requirement, not an optional step.

### Step 13. Merge the feature branch into the main branch

The feature branch may only be merged after:

* the required review is completed
* requested revisions have been addressed
* required checks or tests have passed
* approval has been granted according to course policy

Students should use the approved merge method required by the course or repository settings.

### Step 14. Delete the remote feature branch

After the PR has been merged, students should delete the remote feature branch in GitHub unless the repository policy states otherwise.

This helps keep the repository clean and reduces confusion about active branches.

### Step 15. Delete the local feature branch

Students should also delete the local copy of the feature branch after merge.

Before deleting the local branch, students must:

* switch back to `main`
* confirm the feature branch has already been merged

### Step 16. Synchronize the latest main branch to local

Finally, students must pull the latest `main` branch from GitHub so that their local repository is fully updated.

This ensures that:

* the merged feature is available locally
* the local environment matches the remote repository
* the student is ready for the next Story or feature task

## 3. Required Workflow Summary

For each feature, students must complete the following sequence:

1. Create or confirm the Jira Story under the correct Epic
2. Complete the required information in the Jira Story
3. Create the feature branch from Jira
4. Verify the branch in GitHub
5. Pull the latest `main` branch locally
6. Create or check out the local feature branch
7. Develop and test the feature
8. Commit with Jira ID and meaningful message
9. Push the feature branch to GitHub
10. Create the pull request
11. Assign reviewers and verify PR details
12. Revise based on review comments if needed
13. Merge into `main` after approval
14. Delete the remote feature branch
15. Delete the local feature branch
16. Pull the latest `main` branch locally

---

## 4. Common Mistakes to Avoid

Students should avoid the following common errors:

* starting coding before the Jira Story is complete
* creating a local branch without first updating `main`
* using unclear commit messages
* forgetting to include the Jira issue ID in commits
* creating a PR from the wrong branch
* forgetting to assign reviewers
* merging before review is completed
* forgetting to delete obsolete branches
* forgetting to synchronize the local repository after merge

---

## 5. Instructor Expectation

In this course, feature development is evaluated not only by whether the code works, but also by whether the student follows a correct and professional workflow.

Students are therefore expected to demonstrate:

* clear task tracking in Jira
* proper use of Git branches
* disciplined commit practice
* responsible pull request management
* participation in code review
* clean branch maintenance after merge

A correct workflow is part of software engineering practice and is considered an important learning outcome of the course.

## 6. Submission/Completion Evidence

When requested by the instructor or TA, students may need to provide evidence that the workflow was completed correctly, such as:

* Jira Story link
* GitHub branch screenshot or URL
* commit history
* pull request URL
* reviewer assignment
* merge record
* updated local repository status

## 7. Recommended Short Student Checklist

Before marking a feature as completed, ask yourself:

* Did I complete the Jira Story properly?
* Did I create the correct feature branch?
* Did I pull the latest `main` before coding?
* Did I test my feature before opening the PR?
* Did I write commit messages with the Jira ID?
* Did I assign reviewers?
* Did I merge only after approval?
* Did I delete both remote and local feature branches?
* Did I update my local `main` after merge?
