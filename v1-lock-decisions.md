# V1 Lock Decisions

## Purpose

This file closes the remaining V1 questions so the next step can be a build plan instead of more product-scope debate.

## Lock Result

The project is now locked enough to move into phased build planning.

## Final V1 Scope

- one structured course: `Java Fundamentals`
- two product entry points:
  - `Course Practice`
  - `Open Problem Practice`
- one shared problem bank
- `10` Java problems in the initial release
- the same `10` problems power both the course path and the open-practice list
- a coding workspace with problem statement, examples, editor, `Run`, `Submit`, results, `Recap`, and `Syntax Guide`
- auth
- saved progress
- problem status tracking

## Final Java Course Structure

`Java Fundamentals` is locked to `5` modules:

1. `Java Syntax, Variables, and I/O`
2. `Conditionals and Boolean Logic`
3. `Loops and Iteration`
4. `Methods and Decomposition`
5. `Arrays, Strings, and Intro Classes`

Each module includes `2` core problems, giving the first course `10` problems total.

## Final Content Rules

Each V1 problem must include:

- a statement and constraints
- at least `1` worked example
- starter code for `Java`
- at least `2` visible test cases
- at least `3` hidden test cases
- one short problem-linked recap
- one linked Java syntax-guide topic

### Recap Rules

- recap content should stay short and reference-style
- target length is about `3` to `5` bullets or roughly `100` to `200` words
- recaps are reminders that support practice, not full lessons

### Syntax Guide Rules

- syntax guides are shared by language/topic instead of being rewritten per problem
- V1 only requires Java syntax guides
- the minimum baseline is `5` Java syntax guides aligned with the `5` course modules

## Final Language Support

- shipped V1 enables `Java` only for editing, starter code, run, and submit
- `Open Problem Practice` exists in V1, but its initial pool is still Java-only
- the architecture and database schema remain multi-language ready
- `C`, `Python`, and `C++` move to Post-V1

## Explicitly Not In V1

- multi-language execution
- more than one structured course
- long-form lessons
- a dedicated DSA track
- system design modules
- AI teaching or judging features
- trying to build a large content library in the first release
