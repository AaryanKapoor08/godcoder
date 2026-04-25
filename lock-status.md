# Lock Status

## Purpose

This file records the result of the lock-in process and points to the final V1 decisions that should now drive planning.

It is based on:

- `productvision.md`
- `architecture.md`
- `discussion.md`
- `v1-lock-decisions.md`

## Lock Result

The lock-in process is complete enough to move into detailed build planning.

## Locked Product Decisions

- GodCoder is a university-oriented coding practice platform, not a full beginner tutor.
- The product is practice-first.
- The student-facing experience should feel familiar to LeetCode, but more aligned with coursework and less intimidating.
- The shipped V1 has two entry points:
  - `Course Practice`
  - `Open Problem Practice`
- The shipped V1 contains one structured course: `Java Fundamentals`.
- The shipped V1 includes auth, saved progress, and problem status tracking.
- The workspace includes `Run`, `Submit`, `Recap`, and `Syntax Guide`.

## Locked Content Decisions

- `Java Fundamentals` is locked to `5` modules:
  - `Java Syntax, Variables, and I/O`
  - `Conditionals and Boolean Logic`
  - `Loops and Iteration`
  - `Methods and Decomposition`
  - `Arrays, Strings, and Intro Classes`
- the initial release contains `10` Java problems
- the same shared problem bank powers both the course path and the open-practice list
- each problem includes starter code, a short recap, visible tests, and hidden tests
- syntax guides are shared by Java topic instead of being rewritten per problem

## Locked Technical Decisions

- the system split remains:
  - frontend
  - backend
  - database
  - execution service
- the shipped V1 is Java-only for editing, starter code, run, and submit
- the architecture remains multi-language ready for later expansion
- judging uses `stdin/stdout`
- hidden tests stay on the backend
- frontend-first with mock data is still the intended build order

## Locked Process Rules

- this is a learning project
- the project owner should write the code personally and understand the system layer by layer
- AI should help with discussion, documentation, and build-plan generation, not replace the builder
- detailed phase planning comes after product and architecture lock-in, not before

## Next Step

The next artifact should be a phased build plan based on the locked V1 decisions, not another product-scope exploration pass.
