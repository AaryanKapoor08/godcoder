# Initial Product Vision

## What GodCoder Is

GodCoder is a coding practice tool for university students.

The simplest way to describe it is: LeetCode, but built for university-level learning and practice instead of interview preparation.

It is not meant to be a tutor that teaches programming from zero. It is meant to help students apply what they are already learning in class.

## The Problem

Many students attend lectures, read notes, and understand concepts at a surface level, but still struggle when they have to sit down and solve problems on their own.

On one side, textbook exercises are often too dry or too limited. On the other side, platforms like LeetCode can feel too advanced, too broad, or too focused on interview-style problem solving.

There is room for a practice platform that is closer to how university students actually learn.

## Core Idea

GodCoder should be a place where students practice programming in a structured way.

The purpose is not to replace class, lectures, or textbooks. The purpose is to give students a better way to apply what they already learned, build confidence, and improve through repetition.

If a student forgets a concept or needs a quick recap, the platform can provide that. But the main product is still practice.

## What Makes It Useful

The value is not just having a list of coding problems.

The value is:

- problems organized in a way that matches university learning
- practice that starts from basics and builds upward
- support for students who need a quick syntax recap or concept refresher
- a more approachable experience than interview-prep platforms

## Two Ways To Use GodCoder

### 1. Course Practice

A student picks a course and practices in sequence.

For example, in a Java course, the student starts with the basics such as syntax, variables, conditionals, loops, methods, arrays, and classes, then gradually works toward more advanced topics and data structures.

This mode is structured. It follows a learning path.

### 2. Open Problem Practice

A student can also practice from a general problem set, similar to how LeetCode works.

In this mode, the student browses problems more freely instead of following a fixed course order.

For the shipped V1, `Open Problem Practice` still uses `Java` only. The architecture should remain ready for broader language support later, but `C`, `Python`, and `C++` move to `Post-V1`.

## Role of Recaps and Guides

GodCoder is not trying to fully teach concepts inside the platform.

But if a student is solving a problem and needs a reminder, there should be an option to view:

- a short concept recap
- syntax guidance
- basic notes for the topic at hand

These should be written guides that support practice, not long lessons that turn the platform into a full teaching product.

## Experience Direction

The platform should feel familiar to anyone who has used LeetCode, but it should be more aligned with student coursework.

That means:

- clearer progression
- more beginner-appropriate problem ordering
- less interview-prep energy
- less intimidation
- more academic usefulness

## First Direction

The first structured course should be `Java`.

That gives the product a clear starting point and lets the platform prove the main idea: a university student can choose a course, practice from the basics upward, and use the platform as a serious companion to what they are learning in class.

At the same time, the product should also support open problem practice from the beginning. That means V1 is built around two visible entry points:

- structured `Course Practice`
- flexible `Open Problem Practice`

## Product Principles

- practice first
- class-aligned structure
- clarity over feature count
- useful recaps, not full lessons
- approachable for beginners
- broad enough to be useful, focused enough to stay coherent

## Locked V1 Decisions

The remaining V1 questions are now closed.

- shipped V1 enables `Java` only for editing, starter code, run, and submit
- `Java Fundamentals` is locked to `5` modules:
  - `Java Syntax, Variables, and I/O`
  - `Conditionals and Boolean Logic`
  - `Loops and Iteration`
  - `Methods and Decomposition`
  - `Arrays, Strings, and Intro Classes`
- the initial release uses `10` shared Java problems
- those `10` problems power both `Course Practice` and `Open Problem Practice`
- each problem gets a short recap and links into shared Java syntax guides

The detailed lock decisions are recorded in `v1-lock-decisions.md`.

## Full Product Vision

The long-term vision for GodCoder is broader than the current V1.

GodCoder is meant to become a university-oriented coding practice platform where students can:

- practice through structured courses that follow real academic progression
- practice from a general open problem bank like LeetCode
- work across multiple languages
- move from beginner syntax and fundamentals toward deeper problem solving

The product is still practice-first. It is not meant to replace lectures or become a full teaching platform from zero. Its role is to help students apply what they learned in class, get repetition, and build confidence through volume and structure.

In the full vision, GodCoder grows into a larger platform with:

- multiple structured language courses
- a larger shared problem bank
- broader language support
- stronger progress tracking
- more polished course progression
- recap and syntax material across more topics
- later expansion into DSA-focused structured practice
- possibly system design or other advanced practice areas later on, if they still fit the product

## Vision Breakdown

To keep the project realistic, the full vision is divided into:

- `V1`: the first real version we are actively shaping now
- `Post-V1`: everything that belongs to the broader product, but not to the first release

## V1

V1 is the current working scope.

### V1 Goal

Build a real, usable first version of GodCoder that proves the core idea:

- a university student can sign up
- browse a Java course or open problem practice
- solve problems in a familiar coding workspace
- use recap/syntax support when needed
- save progress and come back later

### V1 Includes

- `Java Fundamentals` as the first structured course
- `5` Java modules
- `Course Practice`
- `Open Problem Practice`
- one shared problem bank
- `10` shared Java problems across both practice modes
- recap content and syntax guidance
- prefilled starter boilerplate in the editor
- `Run` and `Submit` in a LeetCode-shaped workspace adapted to student practice
- auth
- saved progress
- problem status tracking

### V1 Technical Direction

- Java-only content and execution in the shipped V1
- architecture prepared for more languages later
- `stdin/stdout` judging model
- hidden tests on the backend
- real code execution is part of the final V1 release, but it can be added after the main product flow is stable during the build sequence

### V1 Does Not Include

- multi-language execution in the initial release
- full multi-language course rollout
- DSA as its own dedicated structured track
- system design modules
- a giant problem bank
- heavy AI-driven judging or teaching
- trying to build the full platform in one pass

## Post-V1

Post-V1 contains the broader product direction that we are not forcing into the first release.

### Additional Language Courses

After Java, the platform can expand into more structured language courses such as:

- `C`
- `Python`
- `C++`
- possibly other languages later if they make sense

The goal is to keep the same course-first structure while reusing the same platform foundation.

### Larger Open Problem Practice

The open problem pool can expand over time with:

- more problems
- more tags and filters
- support for more languages
- better difficulty spread

### DSA Track

A later version of GodCoder can include a proper structured DSA section.

That would be separate from language courses and focused on problem-solving patterns, data structures, and algorithmic thinking in a more organized sequence.

### System Design and Other Advanced Areas

System design was part of the earlier broader vision, but it is not part of V1.

If it is ever added, it belongs later, after the core coding practice platform is already strong.

The same is true for any more advanced tracks beyond language fundamentals and basic/open practice.

### Expanded Progress and Product Depth

Later versions can also include:

- richer dashboards
- better progress analytics
- more mature recommendation systems
- more polished content systems
- broader recap/reference material

These are future improvements, not requirements for the first release.

## Documentation Note

For now:

- this file contains both the broader product vision and the scoped V1
- `V1` is the active build target
- `Post-V1` is future direction, not immediate commitment
