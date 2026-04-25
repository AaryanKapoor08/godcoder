# Project Handoff

## Purpose

This file is the resume point for the project.

If you stop working and come back later, this should tell you:

- what the project is
- what is already decided
- what stage the project is in
- what has not been built yet
- what should happen next

## Current Project State

- project name: `GodCoder`
- current stage: documentation and planning
- implementation status: no real app code yet
- last completed milestone: V1 lock-in
- next milestone: phased build plan

This means the product definition work is far enough along that the next serious task is no longer product debate.

The next serious task is turning the locked docs into a build sequence.

## What GodCoder Is

GodCoder is a coding practice platform for university students.

The short version is:

`LeetCode`, but oriented toward university learning and structured practice rather than interview prep.

It is not meant to be a full beginner tutor. It is meant to help students apply class material through practice, repetition, and structured progression.

## Project Philosophy

This is a learning project.

The project owner should write the code personally and understand the system layer by layer.

AI is supposed to help with:

- discussion
- documentation
- structure
- later build-plan generation

AI is not supposed to replace the project owner as the builder.

## What Was Just Finished

The lock-in process is complete enough to stop refining V1 scope for now.

The following are now treated as decided:

- product direction
- V1 boundaries
- initial architecture
- initial content baseline
- initial language support decision

These decisions are captured mainly in:

- `lock-status.md`
- `v1-lock-decisions.md`
- `productvision.md`
- `architecture.md`

## Locked V1 Summary

### Product Shape

- one structured course: `Java Fundamentals`
- two visible entry points:
  - `Course Practice`
  - `Open Problem Practice`
- one shared problem bank
- one coding workspace with:
  - problem statement
  - examples
  - editor
  - `Run`
  - `Submit`
  - results
  - `Recap`
  - `Syntax Guide`
- auth
- saved progress
- problem status tracking

### Language Scope

- shipped V1 is `Java`-only
- `Open Problem Practice` exists in V1, but its initial pool is still Java-only
- the architecture stays multi-language ready for later expansion
- `C`, `Python`, and `C++` are explicitly Post-V1

### Content Baseline

- `Java Fundamentals` has `5` modules:
  - `Java Syntax, Variables, and I/O`
  - `Conditionals and Boolean Logic`
  - `Loops and Iteration`
  - `Methods and Decomposition`
  - `Arrays, Strings, and Intro Classes`
- each module has `2` core problems
- total initial problem count: `10`
- the same `10` problems power both the course path and the open-practice list

### Per-Problem Minimum Content

Each V1 problem should include:

- statement
- constraints
- at least `1` worked example
- starter code for `Java`
- at least `2` visible test cases
- at least `3` hidden test cases
- one short problem-linked recap
- one linked Java syntax-guide topic

### Architecture Direction

The system is split into:

- frontend
- backend
- database
- execution service

Important architectural rules:

- frontend can be built first with mock data
- frontend should still mirror the future backend contracts
- hidden tests stay on the backend
- V1 judging uses `stdin/stdout`
- the editor can be prefilled with starter boilerplate

## What Is Not Built Yet

None of the application layers are implemented yet.

That includes:

- no frontend app
- no backend app
- no database schema in code
- no execution service
- no seed content files
- no auth implementation
- no real run/submit pipeline

Right now this repository is a documentation package, not a software codebase.

## What Files Exist And Why

### `README.md`

Entry point for reopening the project later.

### `project-handoff.md`

This file. It explains the current state and what to do next.

### `discussion.md`

Explains the learning-project philosophy and the rule that build planning comes after documentation and lock-in.

### `productvision.md`

Defines what the product is, what V1 includes, and what belongs in Post-V1.

### `architecture.md`

Defines the frontend/backend/database/execution split, proposed API surface, data shapes, and initial schema direction.

### `v1-lock-decisions.md`

Records the final decisions that closed the open V1 scope questions.

### `lock-status.md`

Short summary of what is locked and what the next artifact should be.

## Recommended Resume Order

When you come back later, do this in order:

1. Read `README.md`.
2. Read `project-handoff.md`.
3. Read `lock-status.md`.
4. Read `v1-lock-decisions.md`.
5. Skim `productvision.md` and `architecture.md`.
6. Generate a phased build plan.
7. Start implementation only after the build plan exists.

## Exact Next Step

The next document that should be created is a phased build plan.

That build plan should:

- assume the locked V1 scope is final
- respect that this is a learning-first project
- break work into understandable phases
- start with a mock-data frontend
- keep backend contracts in mind from the beginning
- introduce real backend, database, and execution layers in a deliberate order

## Suggested First Build-Plan Shape

When planning resumes, the build plan should probably be organized around phases like:

1. project setup and repository structure
2. mock-data frontend and core screens
3. workspace flow and mock run/submit behavior
4. backend contracts and auth
5. database schema and seed content
6. real run/submit integration through an execution service
7. progress persistence and cleanup

This is not yet the formal build plan.

It is only the recommended direction for the next planning pass.

## Practical Resume Notes

- do not reopen language-scope debate unless the product direction changes
- do not expand V1 beyond the locked `Java`-only scope without a deliberate decision
- do not try to build the full long-term vision first
- keep Post-V1 ideas out of the first implementation plan
- keep the learning-project constraint active when deciding how detailed or ambitious each phase should be

## Resume Prompt Template

If you want to resume this project with AI later, a good starting prompt would be:

`Read README.md, project-handoff.md, lock-status.md, v1-lock-decisions.md, productvision.md, and architecture.md. Then generate a phased build plan for the locked Java-only V1 of GodCoder, keeping in mind that this is a learning project and the builder should implement the code personally.`

## Final Reminder

You stopped at a good point.

The project is not half-built or messy right now.

It is in a clean pre-build state with the product and V1 scope documented well enough that the next session can begin directly with planning.
