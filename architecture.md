# Initial Architecture

## Purpose

This document defines the initial system split for GodCoder:

- what belongs in the frontend
- what belongs in the backend
- what belongs in the database
- how these parts work together in V1

The goal is not to lock every technical detail yet. The goal is to create a clean starting structure so the frontend can be built first without confusion later.

## Locked Decisions

These decisions are currently locked for the initial build:

- one shared problem bank
- the same problem can appear in both `Course Practice` and `Open Problem Practice`
- V1 content is centered on `Java`
- the first shipped V1 enables `Java` only for starter code, `Run`, and `Submit`
- the architecture should support adding more languages later without redesigning the system
- judging in V1 uses `stdin/stdout`
- the editor can still be prefilled with starter boilerplate and helper function stubs
- `auth` and saved progress are included in the first real release
- source tracking is not part of the initial architecture

## Locked V1 Content Baseline

- `Java Fundamentals` is the only structured course in the shipped V1
- `Java Fundamentals` contains `5` modules:
  - `Java Syntax, Variables, and I/O`
  - `Conditionals and Boolean Logic`
  - `Loops and Iteration`
  - `Methods and Decomposition`
  - `Arrays, Strings, and Intro Classes`
- the initial shared problem bank contains `10` Java problems
- those `10` problems power both `Course Practice` and `Open Problem Practice`
- no extra open-only problem set is required in V1
- each problem should include at least `1` worked example, `2` visible test cases, `3` hidden test cases, starter code, and a short recap
- V1 uses shared Java syntax guides by topic instead of long per-problem lessons

## High-Level Split

### Frontend

The frontend is the student-facing product.

It is responsible for:

- rendering pages and UI
- showing courses, modules, and problem lists
- showing the problem workspace
- hosting the code editor
- showing recap/syntax content
- collecting user actions like `Run`, `Submit`, `Next Problem`
- displaying test results, submissions, and progress

In the first stage, the frontend can use mock data or local JSON so the product experience can be built before the real backend is connected.

### Backend

The backend is the application layer between the frontend and the data/execution systems.

It is responsible for:

- exposing API endpoints to the frontend
- validating requests
- returning course, module, problem, and progress data
- handling authentication and user identity
- saving submissions and user progress
- deciding which test cases are visible and which are hidden
- sending code to the execution service
- receiving execution results and returning them safely to the frontend

The backend protects the system. The frontend should not directly talk to the database or directly expose hidden grading logic.

### Database

The database is the persistent storage layer.

It is responsible for storing:

- course content
- module structure
- problem statements
- recap content
- starter code
- visible and hidden test cases
- supported languages
- users
- progress
- submissions

The database is the long-term memory of the application.

### Execution Service

Code execution should be treated as its own concern, even if it is hidden behind the backend.

It is responsible for:

- compiling/running user code
- executing visible tests on `Run`
- executing full grading tests on `Submit`
- returning output, errors, runtime status, and timing information

V1 judging should use a `stdin/stdout` model. That means student code is executed as a full program, but the editor can still be prefilled with starter boilerplate so the student is not starting from a blank page.

For now, this can remain abstract while the frontend is being built.

## V1 Product Flows

### Flow 1: Course Practice

1. Student opens the app.
2. Frontend shows available courses.
3. Student selects `Java Fundamentals`.
4. Frontend requests course and module data from the backend.
5. Backend loads course/module/problem metadata from the database.
6. Student opens a problem.
7. Frontend shows statement, recap tab, starter code, and editor.
8. Student clicks `Run` or `Submit`.
9. Frontend sends code and language choice to the backend.
10. Backend sends the request to the execution service.
11. Backend stores the result and updates progress in the database.
12. Frontend shows results to the student.

### Flow 2: Open Problem Practice

1. Student opens the open problem list.
2. Frontend requests filterable problem data from the backend.
3. Backend returns problems from the database.
4. Student selects a problem.
5. Student solves it in the workspace.
6. Submission and result handling follow the same backend/execution flow as course practice.

## Frontend Responsibilities

## Core Screens

- landing page
- dashboard / home
- course page
- module page
- open problem list
- problem workspace
- progress page

## What The Frontend Owns

- routing
- layout
- editor integration
- tabs such as `Problem`, `Recap`, `Syntax Guide`, `Results`
- state for selected language, current code, active tab, and visible results
- optimistic UI where appropriate
- loading, empty, and error states
- prefilling starter boilerplate supplied by the backend/content layer

## What The Frontend Should Not Own

- hidden test cases
- grading rules
- permanent progress logic
- direct database reads/writes
- execution secrets or judge credentials

## Suggested Frontend Data Shapes

### Course card

- `id`
- `slug`
- `title`
- `description`
- `language`
- `moduleCount`
- `problemCount`

### Module item

- `id`
- `courseId`
- `title`
- `orderIndex`
- `description`
- `problemCount`
- `status`

### Problem summary

- `id`
- `slug`
- `title`
- `difficulty`
- `availableInCourse`
- `availableInOpenPractice`
- `supportedLanguages`
- `tags`
- `courseContext`

### Problem detail

- `id`
- `slug`
- `title`
- `statement`
- `constraints`
- `examples`
- `starterCode`
- `visibleTests`
- `recap`
- `syntaxGuide`
- `supportedLanguages`
- `judgeMode`

## Backend Responsibilities

The backend exists to turn the product into a real application instead of a static frontend.

## Backend Jobs

- serve structured content to the frontend
- manage auth and sessions
- track progress
- save submission history
- handle run/submit actions
- keep hidden tests hidden
- enforce permissions and validation

## Initial API Endpoints

### Public content

- `GET /api/courses`
- `GET /api/courses/:courseSlug`
- `GET /api/courses/:courseSlug/modules`
- `GET /api/modules/:moduleId`
- `GET /api/problems`
- `GET /api/problems/:problemSlug`
- `GET /api/problems/:problemSlug/recap`
- `GET /api/problems/:problemSlug/syntax-guide`
- `GET /api/problems/:problemSlug/starter-code`

### User and progress

- `POST /api/auth/signup`
- `POST /api/auth/login`
- `POST /api/auth/logout`
- `GET /api/users/me`
- `GET /api/users/me/progress`
- `GET /api/users/me/courses/:courseSlug/progress`
- `GET /api/users/me/problems/:problemSlug/status`

### Execution and submissions

- `POST /api/submissions/run`
- `POST /api/submissions/submit`
- `GET /api/submissions/:submissionId`
- `GET /api/users/me/submissions`

### Optional V1 utility endpoints

- `GET /api/languages`
- `GET /api/tags`

## Example Request Ownership

### `Run`

Frontend sends:

- problem id
- selected language
- current code

Backend:

- validates the request
- loads visible test cases
- sends code + visible tests to the execution service
- returns result data to the frontend

### `Submit`

Frontend sends:

- problem id
- selected language
- current code

Backend:

- validates the request
- loads full grading test set
- sends code + hidden tests to the execution service
- stores submission result
- updates user progress
- returns pass/fail and summary data

## Database Responsibilities

The database stores both content and user activity.

## Initial Tables / Models

### `users`

- `id`
- `email`
- `username`
- `password_hash`
- `created_at`
- `updated_at`

### `courses`

- `id`
- `slug`
- `title`
- `description`
- `language`
- `is_published`
- `created_at`
- `updated_at`

### `modules`

- `id`
- `course_id`
- `title`
- `slug`
- `description`
- `order_index`
- `is_published`

### `problems`

- `id`
- `slug`
- `title`
- `statement`
- `difficulty`
- `judge_mode`
- `is_open_practice`
- `is_published`
- `created_at`
- `updated_at`

Notes:

- `judge_mode` should be `stdin_stdout` for V1.
- `is_open_practice` indicates whether the problem appears in the open problem pool.
- course placement is handled separately through the course mapping table.

### `course_problems`

- `id`
- `course_id`
- `module_id`
- `problem_id`
- `order_index`

This table maps problems into a course sequence.

Because the same problem can appear in both modes, `course_problems` should only describe where a problem appears inside a course path. It should not duplicate the problem itself.

### `problem_languages`

- `id`
- `problem_id`
- `language`
- `starter_code`
- `solution_template`
- `is_enabled`

This allows one problem to support multiple languages with different starter code.

Only `Java` needs to be enabled in V1, but this table should stay multi-language ready for later expansion to `C`, `C++`, and `Python`.

### `problem_examples`

- `id`
- `problem_id`
- `input_text`
- `output_text`
- `explanation`
- `order_index`

### `problem_test_cases`

- `id`
- `problem_id`
- `language`
- `input_payload`
- `expected_output`
- `is_hidden`
- `label`
- `order_index`

### `problem_recaps`

- `id`
- `problem_id`
- `title`
- `content`

### `syntax_guides`

- `id`
- `language`
- `topic_slug`
- `title`
- `content`

### `tags`

- `id`
- `slug`
- `name`

### `problem_tags`

- `id`
- `problem_id`
- `tag_id`

### `submissions`

- `id`
- `user_id`
- `problem_id`
- `language`
- `source_code`
- `submission_type`
- `status`
- `passed_test_count`
- `total_test_count`
- `runtime_ms`
- `memory_kb`
- `created_at`

### `submission_results`

- `id`
- `submission_id`
- `test_case_label`
- `status`
- `stdout`
- `stderr`
- `expected_output`
- `actual_output`
- `runtime_ms`

### `user_problem_status`

- `id`
- `user_id`
- `problem_id`
- `last_language`
- `is_started`
- `is_solved`
- `best_submission_id`
- `attempt_count`
- `last_submitted_at`

### `user_course_progress`

- `id`
- `user_id`
- `course_id`
- `current_module_id`
- `completed_problem_count`
- `completed_module_count`
- `last_activity_at`

## Locked V1 Content Rules

To keep the system manageable:

- use one canonical shared problem bank
- all shipped V1 problems are `Java` problems
- each problem may appear in a course path, the open practice pool, or both
- each problem should include at least `1` example, `2` visible test cases, `3` hidden test cases, starter code, and a short recap
- recap content should be short and problem-linked
- syntax guides should be shared by language instead of rewritten for every problem
- V1 only requires Java syntax-guide content
- visible test cases and hidden test cases should be stored separately by flag, not by separate systems
- the shipped V1 should be Java-only even though the architecture remains multi-language ready
- starter code should reduce blank-page anxiety, but judging should still run as `stdin/stdout`

## What Can Be Mocked First

The frontend can be built first with mock data for:

- 1 course: `Java Fundamentals`
- `5` modules
- an open problem list using the same shared bank
- `10` sample Java problems
- recap text
- `5` Java syntax-guide entries
- starter boilerplate for Java problems
- fake run/submit responses

This is enough to build the full UX before real backend/database integration.

## Recommended Build Order

1. Build the frontend with local mock data.
2. Lock the shape of pages and data contracts.
3. Build auth and saved-progress support in the backend and database.
4. Build the backend endpoints to match those contracts.
5. Add the database schema and seed sample content.
6. Connect real run/submit behavior through an execution service.

## Practical Rule

Frontend first is fine.

But the frontend should be built as if the backend already exists. That means even mock data should follow the API and model shape we expect to use later, so the transition from static frontend to real app stays clean.
