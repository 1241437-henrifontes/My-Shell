# (My Shell) User Stories

---

## Actors Definition

1. **Project Manager**

2. **System User**

## User Stories

#### US001 – Sequence Diagram
    As a Project Manager, I want a Sequence Diagram to show the interaction between the system user and the shell system (Shell + Kernel) to be developed.

#### US002 – Technical Constraints
    As a Project Manager, I want the project Non-Functional Requirements to be listed in order to the project development be guided by it.

#### US003 – Use Case Diagram
    As a Project Manager, I want a Use Case Diagram to identify the main interactions between the actors and the shell system to be developed.

#### US004 – Domain Model
    As a Project Manager, I want a Domain Model to be created in order to identify the main domain concepts (e.g., command, token, process, job, environment, redirection) and their relationships within the project.

#### US005 – Shell Initialization and REPL Loop
    As a System User, I want the shell to start, display a prompt, read my input continuously, execute the commands I type, and terminate gracefully when I request it (via the "exit" command or EOF), so that I can have an interactive session with the system.

#### US006 – Lexical Analysis (Tokenization)
    As a System User, I want the shell to break my raw input into tokens (command name, options, arguments, operators), so that the shell can identify each meaningful unit before interpreting and executing the command.

#### US007 – Syntactic Parsing
    As a System User, I want the shell to parse the token stream into a structured representation (simple commands, pipelines, lists, redirections), so that the shell can correctly understand the logical structure of what I typed before executing it.

#### US008 – Quoting and Escape Handling
    As a System User, I want the shell to interpret single quotes ('...'), double quotes ("..."), and the backslash escape character (\), so that I can include special characters, spaces, and metacharacters in my arguments without unintended expansion.

#### US009 – Shell Expansions
    As a System User, I want the shell to perform tilde expansion (~), parameter/variable expansion ($VAR), command substitution ($(...)), arithmetic expansion ($((...))), word splitting, and pathname expansion (globbing: *, ?, [...]) in the correct order, so that I can write commands more dynamically and concisely.

#### US010 – External Command Execution and PATH Resolution
    As a System User, I want the shell to locate executables in the directories listed in the $PATH environment variable and run them in a child process using the fork/exec/waitpid mechanism, so that I can execute any program installed on my system.

#### US011 – Built-in Commands
    As a System User, I want the shell to provide a set of built-in commands (cd, pwd, exit, echo, export, unset, env, alias, unalias, history, help, type, jobs, fg, bg) executed within the shell process itself, so that I can manage the shell state and perform common operations without spawning a new process.

#### US012 – Environment Variables Management
    As a System User, I want the shell to read inherited environment variables at startup, allow me to define, modify, and remove shell and environment variables (via export and unset), and pass the proper environment to every child process, so that I can configure my session and the programs I run.

#### US013 – I/O Redirection
    As a System User, I want the shell to support input (<), output (>), append (>>), error redirection (2>), and combined redirection (&> or 2>&1), so that I can redirect data streams from and to files instead of the terminal.

#### US014 – Pipelines
    As a System User, I want the shell to support pipelines using the "|" operator (e.g., "cmd1 | cmd2 | cmd3"), connecting the standard output of one command to the standard input of the next, so that I can compose commands to solve complex tasks.

#### US015 – Command Sequencing and Logical Operators
    As a System User, I want the shell to support sequential execution (;), conditional execution based on exit status (&& and ||), and command grouping with parentheses and braces, so that I can build composite command lines and express control flow at the shell level.

#### US016 – Background Execution and Job Control
    As a System User, I want the shell to run commands in the background when I append "&", track their state, and provide job-control built-ins (jobs, fg, bg, wait, kill), so that I can manage multiple concurrent jobs within the same shell session.

#### US017 – Signal Handling
    As a System User, I want the shell to handle signals correctly — ignoring SIGINT and SIGTSTP in the shell itself, forwarding them to the foreground job, and reaping terminated children via SIGCHLD — so that Ctrl+C and Ctrl+Z behave the way I expect and no zombie processes are left behind.

#### US018 – Command History
    As a System User, I want the shell to record the commands I execute, allow me to navigate through previous commands using the up and down arrow keys, search through them, and persist the history across sessions in a file (e.g., ~/.myshell_history), so that I can easily reuse past commands.

#### US019 – Line Editing and Tab Completion
    As a System User, I want the shell to support line editing (cursor movement, backspace, delete, word-level navigation) and tab completion for commands, file paths, and variable names, so that I can build and correct my commands efficiently.

#### US020 – Configuration File and Customizable Prompt
    As a System User, I want the shell to read a configuration file (e.g., ~/.myshellrc) at startup to apply user-defined aliases, environment variables, and settings, and to support a customizable prompt via the PS1 variable with placeholders for username, host, current directory, and last exit status, so that I can personalize my shell experience.
