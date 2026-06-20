# (My Shell) US002 - Non-Functional Requirements

---

**1.** **NFR01: User Stories Technical Documentation**

Every user story of the project must be documented under the `/documentation` folder, inside its own directory named after the user story identifier (e.g., `/US001`, `/US002`). Each directory must contain, at minimum, a `readme.md`
file written in Markdown, structured according to the templates available in `/documentation/US-templates` (one for documentation user stories, one for coding user stories). Coding user stories must additionally include at least one
UML diagram (e.g., _Sequence Diagram_, _Class Diagram_, _Use Case Diagram_) that illustrates the user story at an appropriate level of detail, exported as an image (`.svg` or `.png`) and accompanied by its source file (e.g., PlantUML
`.puml`) so the diagram remains editable and version-controllable.

**2.** **NFR02: Source Code Organization**

The source code must be placed under the `base/src` folder and organized by **architectural component**, not by user story. The project must follow a modular structure where each shell subsystem lives in its own module (e.g., `lexer/`,
`parser/`, `executor/`, `builtins/`, `expansion/`, `environment/`, `jobs/`, `signals/`, `io/`, `history/`). Public interfaces of each module must be declared in header files (`.h`) under the same module folder, while implementation
details (`.c`) remain private to the module. Cross-module dependencies must flow in a single direction (no circular includes), and shared utilities must live in a dedicated `common/` or `utils/` module.

**3.** **NFR03: Testing Approach**

The project must follow a **test-driven development (TDD)** methodology: every new feature or bug fix must start with a failing test that captures the expected behavior, followed by the minimum code required to make it pass, followed
by refactoring. The codebase must include both **unit tests** (covering individual modules in isolation) and **integration tests** (covering end-to-end command execution through the shell). A minimum **line coverage of 75%** must be
maintained across the production code, measured automatically in the CI pipeline (e.g., via `gcov`/`lcov`).

**4.** **NFR04: Continuous Integration and Quality Control**

A continuous integration pipeline (e.g., GitHub Actions) must be configured to run automatically on every push and pull request to the repository, as well as support manual execution. The pipeline must, at minimum: (a) compile the
project with `-Wall -Wextra -Wpedantic -Werror`; (b) run the full unit and integration test suite; (c) execute the test suite under AddressSanitizer and UndefinedBehaviorSanitizer to detect memory safety and undefined-behavior issues;
(d) report test coverage. A pull request may only be merged if the pipeline passes on the head commit.

**5.** **NFR05: GitHub Workflow and Best Practices**

The project must follow a disciplined GitHub workflow throughout development:
- Every unit of work must be tracked as a **GitHub issue**.
- The **project board** (GitHub Projects) must be kept up to date, reflecting the real status of each issue (To Do / In Progress / Done).
- All commits must reference the related issue (e.g., `#12`) and use a descriptive message that explains _what_ and _why_ (e.g., `Add lexer support for double-quoted strings (#12)`).
- Commits must be **frequent**.
- All work must be developed in **feature branches** named after the user story and merged into `main` exclusively via pull request, after CI passes and the changes have been reviewed.

**6.** **NFR06: Shell Robustness**

The shell must never crash because of a user input, no matter how malformed it may be. Invalid syntax must be clearly reported to the user, and the control must be returned to the prompt.

**7.** **NFR07: Build Automation**

The compiling process of the code must be possible to be invoked from a single-line command (e.g., `make`). It won't be acceptable to have to build the project from scratch every time a change is made.
