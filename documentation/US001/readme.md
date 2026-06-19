# (My Shell) US001 - Sequence Diagram

---

## 1. Introduction

In the context of the project, it's of massive importance the creation of a **_sequence diagram_** that will explain the interaction flow between the system user and the shell system. The _**sequence diagram**_ must be designed to show this interaction in an explanatory and clear way. This will be useful for anyone who wants to understand the program flow quickly and deeply.

---

## 2. Requirements

- It must be developed a _**sequence diagram**_ to demonstrate the interaction between the _**system user**_ and the _**shell system**_.

### 2.2 Acceptance Criteria

1. The **_shell system_** is a combination of **_Shell_** (interpreter) and **_Kernel_** (operating system). The SD must show the interaction between the system user and this system described.

### 2.3 Dependencies/References

No dependencies.

---

## 3. Relevant Information/Considerations

The SD can be found in:

[Sequence Diagram](documentation/global/images/SD.svg)

It's important to clarify what's really going on in the system illustrated in the SD designed. To do this, there are a few arrows that need to be explained more deeply:

- **3.** The raw input typed by the user and sent to the shell must be **tokenized**: it means splitting the input into a sequence of tokens that the Kernel can understand and will interpret. (To be completed)
