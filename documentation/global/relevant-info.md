# (My Shell) Relevant Information

---

First, it's important to understand the differences between the concepts: 

> **Shell**

> **Terminal**

> **Command Line Interface (CLI)**

**Shell** is a program that receives commands from the user, processes them, asks the operating system to execute them, and then returns the output to be printed on the screen. It's the interpreter and intermediary between the user interface and the operating system. It calls the operating system – from now on, I will call it _OS_ – by using _system calls_ (or syscalls). 
The OS is the one that actually executes the commands and performs the tasks the user requests, while the shell is responsible for interpreting the commands and then, according to this interpretation, calling the OS. Making a comparison with the MVC architecture, the shell works as the Controller component, controlling the flow of data and calling the OS (or in this point of view, the Model/Domain component).
The View component - or the user interface - in this case would be the **Terminal**.

**Terminal** is the user interface that allows the user to interact with the shell. It's the program that provides the graphical interface for the user to input commands and then see the output. It's the black-and-white window that can be found on every PC, and still the majority of people have no idea on how to work with it.

**Command Line Interface (CLI)**, on the other hand, is a type of user interface that allows the user to interact with the system not by pressing buttons or interacting with graphical elements, but by typing commands in a text-based interface. A terminal is an implementation of a CLI.

Those definitions are really important to understand what the project focus is about.

---

### Shell Life Cycle

Now, going deeper to what a shell really does, from a simple point of view, during its lifetime, the shell does three main things:

> **Initialize**: the shell reads and executes its configuration files. They dictate the shell's behavior. 

> **Interpret**: the shell reads the commands from standard input and then executes them.

> **Terminate**: the shell executes shutdown commands, frees up memory resources, and terminates.

During the interpretation phase, what the shell does is that it parses the user input: it breaks it down into tokens (tokenization), dividing the command into command name, options or flags and arguments.

### Processes

It's important to understand that the shell has a specific standard functioning: a shell has the main function of starting new processes. On Unix-like systems, this is done by calling the _fork()_ syscall. What it does is that it duplicates the current running process, creating a new one that will run in parallel with the original one. This logic means that all the shell-created processes come from the same parent process, which is the _Init_ process, loaded once the kernel is loaded; in other words, it is the first running process in the system.
But it happens that the new process cannot be an exact copy of the original one, running its same program. To make it run a different one, the one that the user wants to, the syscall used is _exec()_, responsible for replacing the current running program for a new one. 

The _fork()_ syscall will return the process ID (PID) of the new process to the parent process, and zero for the child. The parent process will then continue to run, but it will have to wait for the child process to finish its execution. The function _wait()_ will wait for the child process to finish its execution and return its exit status. The _exec()_, on the other hand, does not return a value; it just replaces the current running program with the one that the user wants to run. If it returns at all, an error during the new program's execution
occurred.

This last described processes functioning will always happen in every shell program.

---

# Bibliography

1. [Tutorial – Write a Shell in C](https://brennan.io/2015/01/16/write-a-shell-in-c/)
